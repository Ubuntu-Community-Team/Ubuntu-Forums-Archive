---
title: "Printer Woes &quot;Stopped: job-stopped&quot;"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Paradox_Wanderer on 2007-05-25
New to Ubuntu/Linux.  Successfully installed my Dell A920 with the Lexmark z600 drivers according to the LexmarkMultifunctionPrinters guide on the Ubuntu website.  Only problem is when I try to print a test page (from the CUPS web interface, the Ubuntu Printer Manager or from another application) I get the same error "Stopped: job-stopped".  When I look at the status again in the Printer Properties, it says "Processing Page 2..."  

I'm stuck and lost, any help would be great.

Here's my /var/log/cups/error_log report:
> E [25/May/2007:10:16:44 -0700] Creating missing directory "/var/run/cups/certs"
E [25/May/2007:10:22:45 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [25/May/2007:10:22:52 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [25/May/2007:10:23:46 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [25/May/2007:10:23:53 -0700] PID 6122 (/usr/lib/cups/cgi-bin/admin.cgi) crashed on signal 9!
E [25/May/2007:10:23:56 -0700] PID 6127 (/usr/lib/cups/cgi-bin/classes.cgi) crashed on signal 9!
E [25/May/2007:10:24:12 -0700] PID 6147 (/usr/lib/cups/filter/rastertoz600) stopped with status 127!
E [25/May/2007:10:24:30 -0700] PID 6181 (/usr/lib/cups/filter/rastertoz600) stopped with status 127!
E [25/May/2007:10:25:35 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [25/May/2007:10:25:59 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [25/May/2007:10:28:45 -0700] CUPS-Set-Default: Unauthorized
E [25/May/2007:10:32:03 -0700] Creating missing directory "/var/run/cups/certs"
E [25/May/2007:10:33:36 -0700] PID 5800 (/usr/lib/cups/filter/rastertoz600) stopped with status 127!
E [25/May/2007:10:33:55 -0700] PID 5830 (/usr/lib/cups/filter/rastertoz600) stopped with status 127!
E [25/May/2007:10:34:33 -0700] [Job 15] Communication was lost. Try printing again.
E [25/May/2007:10:34:55 -0700] PID 5961 (/usr/lib/cups/filter/rastertoz600) stopped with status 127!

Thanks in advance.

---

### Post by Pragmatist on 2007-05-25
It is probably a configuration issue with CUPS, but lets rule out other problems first.  If the problem is just due to CUPS, you still should be able to print with **lpr**  Try this:

```
echo This is a test >> test.txt
``````
lpr test.txt
```

edit: The above file, test.txt is probably too small.  Use a text file with about a page of text in it.  You can write one with an editor and just put a bunch of carriage returns to make the text span the page.  The problem with test.txt is that it has only one line and might possibly not show up (i.e. get cut off).  Using a larger file rules this out.

---

