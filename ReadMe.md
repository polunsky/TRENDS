Web Method for TRENDS Model
=========
This web method is used to calculate the forecasting numbers based on the user's input. It can be accessed through a HTTP post request by Ajax function.

## Example
~~~~
jQuery.ajax({
       type: 'POST',
       data: Inputs,
       dataType: '',
       url: URL,
       success: function (data) {
           txt2Parse = $(data).text();
           results = eval('(' + txt2Parse + ')');
       },
       async: false
   });
~~~~
### URL
The url of the web method is http://trends-tti.tamu.edu/AJAXCalculate.asmx/GetJSONResults. Note that the protocal of the website is http but not https. The request must be made from a http site too so it won't be blocked by the browser.

### inputs
This includes all input variables required for the calculation. It is stored in JSON format. All variables and their descriptions are explained in [this worksheet](Variables.xlsx). The following code shows an example of the input object.
~~~
{
"PersonalGrowthAssumptions":"GrowthAssumption4",
"FuelEfficiencyPersonal":"average",
"FuelEfficiencyCommercial":"average",
"NewCapacity":"Yes",
"AdditionalCapacity":"0",
"AdditionalCapacityBegins":"2016",
"AdditionalCapacityEnds":"2016",
"TxDOTMaintenance":"Yes",
"MaintenanceEstimate":"90",
"OtherExpenseIncreases":"No",
"ExpensePlan":"1",
"ExpenseBuild":"1",
"ExpenseMaintenance":"1",
"ExpenseUse":"1",
"ExpenseManage":"1",
"ExpenseOtherAgencies":"1",
"ExpenseContributions":"1",
"ExpenseIncreases":"No",
"ExpenseCat1":"1",
"ExpenseCat5":"1",
"ExpenseCat6":"1",
"ExpenseCat7":"1",
"ExpenseCat8":"1",
"ExpenseCat9":"1",
"ExpenseCat10":"1",
"ExpenseCat11":"1",
"StateGasTax":"Yes",
"StateGasTaxRate":"10",
"StateGasTaxYear":"2017",
"StateGasTax2":"Yes",
"StateGasTaxRate2":"10",
"StateGasTaxYear2":"2019",
"StateDieselTax":"Yes",
"StateDieselTaxRate":"10",
"StateDieselTaxYear":"2016",
"StateDieselTax2":"Yes",
"StateDieselTaxRate2":"10",
"StateDieselTaxYear2":"2019",
"FederalGasTax":"Yes",
"FederalGasTaxRate":"10",
"FederalGasTaxYear":"2016",
"FederalGasTax2":"Yes",
"FederalGasTaxRate2":"10",
"FederalGasTaxYear2":"2019",
"FederalDieselTax":"Yes",
"FederalDieselTaxRate":"10",
"FederalDieselTaxYear":"2016",
"FederalDieselTax2":"Yes",
"FederalDieselTaxRate2":"10",
"FederalDieselTaxYear2":"2019",
"FederalReimbursements":"85",
"IndexHighwayCost":"No",
"IndexConsumerPrice":"Yes",
"IndexFuelEfficiency":"No",
"IndexYear":"2019",
"NetPercentIncreaseStateFuelTax":"75",
"VehicleRegistrationFee":"Yes",
"ChangedAllFee":"10",
"ChangedMotorcycleFee":"10",
"ChangedPassengerVehicleLess6000":"10",
"ChangedTrailerLess6000":"10",
"ChangedAllLess10k":"10",
"ChangedAllLess18k":"10",
"ChangedAllLess26k":"10",
"ChangedAllLess40k":"10",
"ChangedAllLess55k":"10",
"ChangedAllLess70k":"10",
"ChangedAllLess80k":"10",
"ChangedYear":"2016",
"VehicleRegistrationFee2":"Yes",
"ChangedAllFee2":"10",
"ChangedMotorcycleFee2":"10",
"ChangedPassengerVehicleLess6000b":"10",
"ChangedTrailerLess6000b":"10",
"ChangedAllLess10k2":"10",
"ChangedAllLess18k2":"10",
"ChangedAllLess26k2":"10",
"ChangedAllLess40k2":"10",
"ChangedAllLess55k2":"10",
"ChangedAllLess70k2":"10",
"ChangedAllLess80k2":"10",
"ChangedYear2":"2019",
"VMTTax":"No",
"VMTTaxFeePersonal":"0",
"VMTTaxFeePersonalYear":"2016",
"VMTTaxFeeCommercial":"0",
"VMTTaxFeeCommercialYear":"2019",
"StateGasTaxYearEnd":"2050",
"StateDieselTaxYearEnd":"2050",
"PercentOfMaintenance":"25",
"PercentOfCategory2":"10.43",
"PercentOfCategory3":"1.56",
"PercentOfCategory5":"12.45",
"PercentOfCategory7":"22.61",
"PercentOfCategory9":"5.04",
"PercentOfCategory11":"5.05",
"MPO1":"No",
"MPOList":"Abilene,Amarillo,Beaumont,Brownsville,Bryan-College Station,Austin,Corpus Christi,El Paso,Harlingen-San Benito,Hidalgo,Houston,Killeen-Temple,Laredo,Longview,Lubbock,Midland-Odessa,Dallas-Ft. Worth,San Angelo,San Antonio,Sherman-Denison,Texarkana,Tyler,Victoria,Waco,Wichita Falls",
"MPO2":"Yes",
"LocalGasTaxRate":"10",
"LocalGasTaxYear":"2020",
"LocalDieselTaxRate":"10",
"LocalDieselTaxYear":"2021",
"MPO3":"Yes",
"LocalPersonalVMT":"1",
"LocalCommercialVMT":"1",
"LocalVMTYear":"2018",
"MPO4":"Yes",
"LocalAllFee":"10",
"LocalMotorFee":"10",
"LocalPassengerVehicleLT6k":"10",
"LocalTrailerLT6k":"10",
"LocalAllLess10k":"10",
"LocalAllLess18k":"10",
"LocalAllLess26k":"10",
"LocalAllLess40k":"10",
"LocalAllLess55k":"10",
"LocalAllLess70k":"10",
"LocalAllLess80k":"10",
"LocalRegistrationYear":"2020",
"MPO5":"Yes",
"LocalFuelEfficiencyCommercial":"average",
"LocalFuelEfficiencyPersonal":"average",
"Proposition12":"Yes",
"Proposition12Amount":"2.6",
"Proposition12Years":"3",
"Proposition12FirstYear":"2026",
"Proposition14":"Yes",
"Proposition14Amount":"2.9",
"Proposition14Years":"3",
"Proposition14FirstYear":"2019",
"Proposition14YearPayback":"2030",
"EIRateOfReturn":"8",
"EIBusinessProfit":"4.6",
"EISavingsRate":"10",
"advanced-mode-switch":true
}
~~~
### results
This is the calculated forecasting numbers parsed from the response of the http request. The response text are in JSON format. On TRENDS website, the results can be accessed through __TTI.calculatedData__. Most of reports are generated directly based on this data.. The structure of the results are shown below.

_Note:  The category reports need further calculation, so I suggest to use 'fake' numbers in the design of the UI._

~~~~
{
  Cummulative: Array[],
  EnhancementRevenue: Array[],
  EnhancementRevenueForCharts: Array[],
  Expense: Array[],
  FederalFuelTax: Object,
  FirstYear: Number,
  Inputs: Object,
  LocalInputs: Object,
  LocalOutputs: Object,
  Message: String,
  MPOList: String,
  NewCap: Array[],
  NumOfYears: Number,
  PopulationScenario: String,
  RememberBlance: Number,
  Result: Boolean,
  Revenue: Array[],
  StochNames: Array[],
  StochResults: Array[],
  SummaryStatement: Array[],
  UncollectedFederalTax: Object,
  UncollectedStateTax: Object,

}
~~~~

#### Cummulative
Stores the cummulative balance. It is not used anywhere in the report. The length of the array is the prediction period, which is determined by the __FirstYear__ and __NumOfYears__.

#### EnhancementRevenue
Enhancement revenue due to the change of inputs. The length of the array is the prediction period, which is determined by the __FirstYear__ and __NumOfYears__. These numbers are used in the revenues chart.
#### EnhancementRevenueForCharts
Not used anymore.
#### Expense
Projected expenses over the prediction analysis period. The length of the array is the prediction period, which is determined by the __FirstYear__ and __NumOfYears__. These numbers are used in the reports of __Revenue/Expense Summary__, __Revenue/Expense Chart__.
#### FederalFuelTax
Projected federal fuel tax over the prediction analysis period. The length of the array is the prediction period, which is determined by the __FirstYear__ and __NumOfYears__. These numbers are used in the reports of __Federal Fuel Tax Summary__.
#### FirstYear
The start year of the prediction period. It's set to __2016__ on the server. All results from __2016__ to the current year are historical data, so results  
#### Inputs
Summary of input variables for the state model. These numbers are used in the report of __Input Variables__.

#### LocalInputs
Summary of input variables for the local option model.

---------------
#### LocalOutputs
Projected revenues for each MPO. The object contains two items. __EconImpct__ stores the prediction numbers of the economic impacts, which is used in the report of __Economic Impact__. __LocalStmt__ stores the prediction revenues from the local option model.
##### Example of EconImpct Element
__AggregateEconomicActivity__: Estimated aggregate economic activity.
__AggregateEconomicImpact__: Estimated aggregate economic impact.
__AggregateIncrease__: Estimated aggregate income.
__BusinessProfit__: Estimated business profit/income.
__County__: MPO name.
__Jobs__: Estimated job increase.
__SystemImprovement__: not used anymore.
__TotalIncreasedBusinessEfficiency__: Estimated total increased business efficiency.
~~~~
{
  AggregateEconomicActivity:231,
  AggregateEconomicImpact:1234,
  AggregateIncrease:100,
  BusinessProfit:1000,
  County:"Tyler",
  Jobs:12,
  SystemImprovement:[[1,2,1],[2,3,4],[3,4,5]],
  TotalIncreasedBusinessEfficiency:456
}
~~~~
##### Example of LocalStmt Element
__DieselRevenue__: Local diesel tax revenue. __GasRevenue__: Local gas tax revenue. __MPO__: MPO name. __RegFee__: Local registration fee revenue. __VMTFee__: Local VMT fee revenue.
~~~~
{
  DieselRevenue:[1,2,3,4,...],
  GasRevenue:[2,3,4,5,...],
  MPO:"Dallas-Ft. Worth",
  RegFee:[2,3,4,5,...],
  Revenue:[2,3,4,5,...],
  VMTFee:[3,4,5,6,...],

}
~~~~
-----------------
#### Message
Error message sent from the server for tracing purpose.
#### MPOList
Selected MPOs for local model analysis.
~~~
"Abilene,Amarillo,Beaumont,Brownsville,Bryan-College Station,Austin,Corpus Christi,El Paso,Harlingen-San Benito,Hidalgo,Houston,Killeen-Temple,Laredo,Longview,Lubbock,Midland-Odessa,Dallas-Ft. Worth,San Angelo,San Antonio,Sherman-Denison,Texarkana,Tyler,Victoria,Waco,Wichita Falls"
~~~
#### NewCapacity
New capacity expenditures. It's varied by the input of the new capacity section.
~~~~
[0,0,0,0,0,0,0,...]
~~~~
#### NumOfYears
Total number of years of the prediction period. The end year of the prediction is __2050__. The start year is __FirstYear__. They are both set on the server side.
#### PopulationScenario
The scenario of population forecasting model is used.
#### RememberBlance
Not used anywhere.
#### Result
The flag shows if there is a valid result from TRENDS model.
#### Revenue
The projected state revenue calculated by TRENDS model. The length of the array is the prediction period, which is determined by the __FirstYear__ and __NumOfYears__.
#### StochNames
The names of variables that are applied stochastic analysis. These output variables are shown in the stoplight chart and the fan chart.
#### StochResults
The results of stochastic analysis.  The stochastic analysis is performed on __State Fuel Tax__, __Vehicle Registration Fee__, and __Vehicle Mileage__. It includes 3 items, which are corresponding to these 3 variables. Each item is an array with 500 elements, which represents the results of 500 Monte-Carlo simulations. The result of one simulation shows one set possible values projected on the prediction period.  According to these numbers, the stoplight chart shows the probabilities that revenue will locate in a given range, and the fan chart shows the percentile curves. __This is only available when advanced-mode-switch is on__.
~~~
[Array[500],Array[500],Array[500]]
~~~
#### SummaryStatement
Projected values of revenues and expenses in finer categories. These numbers are used in the reports of Detail Summary, Summary To 2050 and Category Distribution.
~~~~
{
   "StateFuelTax": 2.57172685E9,
   "VehicleRegistrationFees": 1.37552051E9,
   "VehicleMileTraveledTax": 0,
   "BondProceeds": 748244573,
   "EconomicStimulus": 45532983,
   "Prop1": 1134670797,
   "Prop7": 0,
   "ShortTermBorrowingRevenue": 400000000,
   "MobilityFunds": 728787,
   "MobilityTaxes": 341617159,
   "MobilityDebts": 345000470,
   "Miscellaneous": 989726345,
   "FederalFuelTax": 3709987606,
   "RightofWay": 0,
   "PE": 0,
   "CEandOther": 208414277,
   "PublicTransportationTraffic": 0,
   "Aviation": 0,
   "Category1Preservation": 208680762,
   "Category1PreservationCatchup": 0,
   "Category1Routine": 907088086,
   "Category2TMACorridorProjects": 129250465,
   "Category3NonTMACorridorProjects": 1060975554,
   "Category4StateConnectivityCorridorProjects": 0,
   "Category5CMAQ": 126487667,
   "Category6BridgeMaintenance": 235908140,
   "Category7STPMetroMobility": 363971845,
   "Category8FederalSafety": 201540956,
   "Category9FederalEnhancement": 128358950,
   "Category10CongressionalEarmarksandTPWD": 85438474,
   "Category11DistrictDiscretionary": 84491998,
   "Category12StrategicPriority": 233801463,
   "Category12Unallocated": 0,
   "Category2MTMACorridorProjects": 1.12447904E8,
   "Category2UNonTMACorridorProjects": 1.680256E7,
   "PLANIT": 1208695654,
   "BUILDIT": 1779225795,
   "MAINTAINIT": 3846111239,
   "USEIT": 155749349,
   "MANAGEIT": 224882806,
   "DebtService": 1398461283,
   "PaymentstoOtherAgencies": 197457943,
   "PaymentsonExistingProjects": 0,
   "RetirementComptroller": 303717549,
   "NEWCAPACITY": 0
}
~~~~
#### UncollectedFederalTax
Federal tax revenue loss due to the adoption of alternative vehicles. The length of the array is the prediction period, which is determined by the __FirstYear__ and __NumOfYears__. These numbers are used in __Alternative Vehicle Report__. Example of the JSON data is shown below. The keys of the object is the prediction year. There are two numbers for each year. One for personal vehicles and the other is for commercial vehicles. The total loss is the summation of the two numbers.
~~~~
{
  2016:
    [24988,8781]
  2017:
    [38635,14901]
  ...
}
~~~~

#### UncollectedFederalTax
State tax revenue loss due to the adoption of alternative vehicles. The length of the array is the prediction period, which is determined by the __FirstYear__ and __NumOfYears__. These numbers are used in __Alternative Vehicle Report__. The structure of the data is the same as __UncollectedFederalTax__.
