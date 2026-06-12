---
title: "Missing CUPSYS mystery"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by BAS54 on 2007-05-11
Hi. Third day newbie.
  

Compared to some postings, I have had a dream run with install,dual boot and modem setups. 
One hiccup, which was my fault entirely. Bad command typing in Terminal. Thumb kept sneaking in spaces where it shouldn't have. That's my story anyway. 

Next project, get the printer up and running. Epson Stylus Colour 460. Should be accepted. 


Problem;

 System/Admin/Printing throws up a small black screen, then is gone in the blink of an eye.
I was expecting a menu or to get a manager but nothing apart from that flash.

Help pointed to me needing CUPS. Scoured the postings, links and on board help.
Checked Places/Computer/Files System/Etc/Cups. and in the folder, cups.conf , it had a sample of how Cups could/should be configured but no actual values.  So figured I did need to get it.

The only reference in Add/Remove programs is one entry to an Open Office App.

Help aimed me at Aptitude and so below.

 
bas@bas-desktop:~$ sudo apt-get install cupsys cupsys-client
Password:
Reading package lists... Done
Building dependency tree... Done
cupsys is already the newest version.
cupsys-client is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bas@bas-desktop:~$


Back in Synaptic Package Manager, it puts up seven cupsys entries, 
all boxes green and unticked including my cupsys-client entry.

 Properties tell me:

Common Tab; Among the description, a green box unticked.
            Installed version   1.2.0.0-ubuntu5
                       Size     287 kb.
                      Download    N/A

Dependancies Tab         Many.

Installed Tab         Many. Starting with '/' and so forth down, each with and address.

Version Tab           1.2.0.0 ubuntu 5 (Now) 


Sorry I can't seem to copy and paste in a lot places but can supply these entries 
if needed.
Does that Size sound right?

Question is. Is it installed?  Waiting to be installed?  Where can I check where 
it is? A couple addresses in the Installed Tab pointed to System file in which a 
lot had .exe extensions and I lost my nerve and backed out. 

Or more important, if indeed I do have it, how can I get it to meet me at 
System/Admin/Printing to discuss my printer?  
That little screen which trips but fails to load suggests something may be there but needs configuring. 

Any pointers appreciated.

BAS54.

---

### Post by Seisen on 2007-05-11
To see if cups is installed put this in the terminal and then you can set your printer up if it works.

[127.0.0.1:631]("127.0.0.1:631")

---

### Post by BAS54 on 2007-05-11
Thanks Seisen.

I sincerely appreciate your help but it is completely over my head. 

I'm going back to reading everything in help. This Terminal access is spooking me. Some times I breeze through. Other times Bad commands. I checked that address. Checking any drivers maybe. 

     Sorry.
BAS54

---

### Post by BAS54 on 2007-05-11
Problem solved.
 No Add Printer manager appeared until I tried to print as test. Set it up got a nice Ubuntu headed colour test strips page.
 Go figure.


BAS54

---

