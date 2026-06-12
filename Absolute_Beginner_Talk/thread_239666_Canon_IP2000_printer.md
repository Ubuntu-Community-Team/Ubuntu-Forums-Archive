---
title: "Canon IP2000 printer"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by ve6ani on 2006-08-19
I'm using BJC-7000 for the driver. My printouts have a washed out look(faded, especially colors). Is there a better driver I should be using?

I would like to use the printer on my home network but running into some difficulty. I've entered [http://localhost:631](http://localhost:631) and looked at my cupsd.conf file. I've added the line:
Allow 192.168.123.175
to my cupsd.conf file. Otherwise my cupsd.conf file is the default file. On my other computer when I try to set up network printer I get "printer not found".
My browser.conf files shows "browser on"
My ports.conf file shows:
Listen localhost:631
Listen /var/run/cups/cups.sock
My error log doesn't seem to show anything
My other computer is running Windows 98 and Mandrake.
I've lost USB functionality on my other computer so I would like to get the printer working.
I'm obviously missing some step in the configuation but don't see it yet. Any suggestions?

---

