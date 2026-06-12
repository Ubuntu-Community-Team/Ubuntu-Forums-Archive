---
title: "Printing from iOS Devices - CUPS, Avahi and Airprint Question"
date: 2012-06-01
forum: Apple Hardware Users
---

### Post by catnippants on 2012-06-01
Folks - I'm wondering if someone can help me understand something.  I have a small 12.04LTS server set up for media sharing, and I got the 'brilliant' idea of setting up my wireless printers so I could access them from the server.   CUPS is all set up, drivers are installed, and it's working great.   Then I started wondering if I could use the server as a host for printing from my iPad.  I found this post:

[http://www.micromux.com/2010/11/22/airprint-for-mac-on-linux/]("http://www.micromux.com/2010/11/22/airprint-for-mac-on-linux/")

And sure enough, that works great too....except in the printer selection dropdown box on my ios devices, I see two entries for each printer - one that says Airprint <name of printer>, and another that says just <name of printer>.  I have found that if I delete the .service files from /etc/avahi/services, the Airprint version of the printer drops out of the list, but the <name of printer> items remain, and I can print to them just fine.

Bottom line, it seems like I don't need to set my server up as an Airprint server at all - my iOS devices just see the printers attached to the server.  What's the point of the .service files?  Does setting them up to look like Airprint devices buy me anything?   Or is the post I used now outdated and this service is just simply built into CUPS?

Would love to understand this one - any help would be appreciated!
Mike

---

### Post by catnippants on 2012-06-01
I have a hunch, and if there's anything to it, then you need more info.   I have several media server packages running on this server - including Twonky, Subsonic and AirVideo.  AirVideo is running under Wine - and requires Bonjour to be installed within Wine in order to run correctly.   (For those familiar with AirVideo, I tried the Linux port, but without mp4creator, I couldn't get offline conversion working properly...so I <cringe> reverted to Wine).  At any rate, I am now wondering if having Bonjour running under Wine AND Avahi running is essentially 'broadcasting' the printers twice....or something along those lines.   

Again, any clues would be greatly appreciated.   I'm now setting up a duplicate server without Wine to check my reasoning...

Mike

---

