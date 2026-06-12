---
title: "beagle crashes"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by mwshook on 2007-04-23
I installed beagle off of automatix. I set it to search my root folder and my FAT32 hard drive.

The gui starts up, but then disappears when I hit the search button. This is the output I get:

Any suggestions?

> Debug: Loading Beagle.Util.Conf+IndexingConfig from indexing.xml
Debug: Loading Beagle.Util.Conf+DaemonConfig from daemon.xml
Debug: Loading Beagle.Util.Conf+SearchingConfig from searching.xml
Debug: Creating a ResponseMessageException from an ErrorResponse

Unhandled Exception: Beagle.ResponseMessageException: Object reference not set to an instance of an object
  Details: System.NullReferenceException: Object reference not set to an instance of an object
  at System.Text.RegularExpressions.Regex.Match (System.String input, Int32 startat) [0x00000] 
  at System.Text.RegularExpressions.Regex.Match (System.String input) [0x00000] 
  at Beagle.Daemon.QueryStringParser.Parse (System.String query_string) [0x00000] 
  at Beagle.Daemon.QueryDriver.DehumanizeQuery (Beagle.Query query) [0x00000] 
  at Beagle.Daemon.QueryDriver.DoQuery (Beagle.Query query, Beagle.Daemon.QueryResult result, Beagle.AsyncResponse send_response) [0x00000] 
  at Beagle.Daemon.QueryExecutor.Execute (Beagle.RequestMessage req) [0x00000] 
  at Beagle.Daemon.ConnectionHandler.HandleConnection () [0x00000] 


---

### Post by mwshook on 2007-04-23
Now it works fine. Maybe I hadn't given it enough time to index (only about 30 mintues).

---

