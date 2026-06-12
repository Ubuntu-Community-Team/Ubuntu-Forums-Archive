---
title: "losing my rag!!!"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by erniewinner on 2006-06-24
](*,) arrrg! i have been wanting an mp3 internet service... i liked the look of napster (which is free now in the us...) i liked sonicselector but i can't use them on ubuntu. so i like most people tried allofmp3.com... i like that service. but it has blurry lines on legality? then i found "www.wippit.com" last night it was working well. (i think napster will take a long time to become free in the uk.) i can't get the site to work today i keep getting this error:

"An unspecified error occurred. Click here to go back.System.Data.SqlClient.SqlException: Timeout expired. The timeout period elapsed prior to completion of the operation or the server is not responding. at System.Data.SqlClient.SqlCommand.ExecuteReader(CommandBehavior cmdBehavior, RunBehavior runBehavior, Boolean returnStream) at System.Data.SqlClient.SqlCommand.ExecuteReader(CommandBehavior behavior) at System.Data.SqlClient.SqlCommand.System.Data.IDbCommand.ExecuteReader(CommandBehavior behavior) at System.Data.Common.DbDataAdapter.FillFromCommand(Object data, Int32 startRecord, Int32 maxRecords, String srcTable, IDbCommand command, CommandBehavior behavior) at System.Data.Common.DbDataAdapter.Fill(DataSet dataSet, Int32 startRecord, Int32 maxRecords, String srcTable, IDbCommand command, CommandBehavior behavior) at System.Data.Common.DbDataAdapter.Fill(DataSet dataSet, String srcTable) at Wippits.GenreTop5CTRL.Page_Load(Object sender, EventArgs e)"

i'm assuming the server is having maintance? can anyone get that working? i wouldn't mind but i liked it's content enough to subscribe... :-k

---

### Post by erniewinner on 2006-06-24
i'm also getting this:

"Server Error in '/' Application.
Timeout expired. The timeout period elapsed prior to completion of the operation or the server is not responding.
Description: An unhandled exception occurred during the execution of the current web request. Please review the stack trace for more information about the error and where it originated in the code.

Exception Details: System.Data.SqlClient.SqlException: Timeout expired. The timeout period elapsed prior to completion of the operation or the server is not responding.

Source Error:

An unhandled exception was generated during the execution of the current web request. Information regarding the origin and location of the exception can be identified using the exception stack trace below.

Stack Trace:

[SqlException: Timeout expired.  The timeout period elapsed prior to completion of the operation or the server is not responding.]
   Wippits.Wippit.SubscriberOrder.SubscriberOrder.PlaceOrder(String CartID, String strCurrency, String strIPAddress, Double c_TaxRate, String pr) +841
   Wippits.ProcessSubscriberOrder.Page_Load(Object sender, EventArgs e) +1066
   System.Web.UI.Control.OnLoad(EventArgs e) +67
   System.Web.UI.Control.LoadRecursive() +35
   System.Web.UI.Page.ProcessRequestMain() +731


Version Information: Microsoft .NET Framework Version:1.1.4322.573; ASP.NET Version:1.1.4322.573 " :-|

---

### Post by bscbrit on 2006-06-24
From my reading of the error messages, it seems that the problem is at their end, not yours.  Other than let them know that their server appears to have fallen over there is perhaps not much else you can do.  
But I will confess that this is not my area of expertise - perhaps someone else can give a more definitive answer?

---

### Post by erniewinner on 2006-06-24
it does the same under xandros, win98 and xp mmm... i've sent them an email. hope it's fixed soon!

---

### Post by erniewinner on 2006-06-25
](*,) better luck today i got a couple of albums worth of songs and then this:

"Server Application Unavailable

The web application you are attempting to access on this web server is currently unavailable.  Please hit the "Refresh" button in your web browser to retry your request.

Administrator Note: An error message detailing the cause of this specific request failure can be found in the application event log of the web server. Please review this log entry to discover what caused this error to occur."

i'm wondering if it cuts you off if you use the service too much??? i wouldn't mind but i downloaded 2 oasis albums and can't listen to them as they are "wmv" protected and i can't get the site to load to get a licence... pain in the bum drm... am i out of luck? once i get a licence does it turn off protection? :-? 

I LOVE MP3'S! ;)

---

### Post by bscbrit on 2006-06-25
You might be right, but I suspect that the answer is actually more simple than that.  Perhaps their free server is simply being overloaded by demand.  If everyone downloads **two Oasis albums**, how much data do you think that they are trying to serve?

---

### Post by erniewinner on 2006-06-26
8) i saw a maintanance post when i logged in and got an email confirming this... it seems to be alright now! but i wish there were more mp3's i hate wma's and drm... 

is there anyway to play wma's on linux i tried a few players and checked a few posts. i thought amarok was a good bet but it didn't work on protected content... i think i'll have to use windows to convert wma's to mp3's. but i'd have to use 98se any freewhere out there fit the bill? i tried tunebite and soundtaxi but they're xp only...

---

