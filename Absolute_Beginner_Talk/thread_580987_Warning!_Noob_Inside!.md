---
title: "Warning! Noob Inside!"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by HMartinho on 2007-10-19
Hi everybody

Im new to ubuntu and to linux in general.
Ive managed to get ubuntu 7.10 installed but im having a couple of problems.
The main problem is my network connection, I have a D-Link 624t adsl router modem wich is connected by cable to my computer, i can ping the router and access the router config page and ping an outside ip, but i was unable to open any page in firefox until i enabled the ipv6 option in firefox, so now i can connect to the internet but pidgin cant connect neither does synaptics package manager and nor does the update manager.
The other main problem I have is I probably messed up my sources.list file, Since I couldnt update ubuntu i initially thought it was a sources list problem and did some crazy editing in the file (at least i think so), so if anyone could post a sources.list as it should look like i would appreciate it.
Also having trouble getting my nvidia 6600GT to work, along with desktop effects, I-ve tried envy but that probably messed it more than i allready did, I now have 800x600 resolution screen.
Thanks for your time and please help a noob out!

Cheers.

---

### Post by hyper_ch on 2007-10-19
sources.list

Use the generator here:  [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)  (Google keyword:   source-o-matic )

---

### Post by HMartinho on 2007-10-19
Thanks for the response.
Allready applied defaul (provided) souces.list content, still no luck in getting either synaptics nor update manager to work.
Still struggling in here :).

Cheers

EDIT:
I now have 1280x1024 resolution, but can't activate desktop effects still, neither can activate the reestricted driver, the box is unticked the status is active but when I try to tick the box it say it can't do it.
Grasping now...

---

### Post by Tom Mann on 2007-10-19
Did you enable or disable ipv6 - most people find improvements when ipv6 is disabled.

I had to disable ipv6 in order to use the internet a long time ago :)

---

### Post by hyper_ch on 2007-10-19
well, I assume the servers are still being hammered with downloads (people really should use torrent for fetching the .ISOs)

---

### Post by HMartinho on 2007-10-19
@Tom Mann
When i disable ipv6, firefox doesn't work :(
Still no luck with pidgin either, getting automatix now.

Cheers

---

### Post by 001100 on 2007-10-19
The servers are quite full right now. Just give it acouple hours or maybe a dat to clear up. Then you will be abile to update and use the synaptics package manage. Use torrents for the .iso(s)

---

### Post by hyper_ch on 2007-10-19
automatix?  Iiiieeks... why would you want to do that?

---

### Post by orange2k on 2007-10-19
EasyUbuntu is much more reliable than Automatix - you should try it...

---

### Post by HMartinho on 2007-10-19
I'm gonna give it a day or so, you're probably right about servers being flooded with ppl downloading and updating their server and sync them.
Too bad I couldn't find a single mirror that could be reached.

Thanks I'll keep this updated with any progress.

I don't even have flash plugin nor can I get it :(

Cheers

---

### Post by corowakid on 2007-10-19
> **HMartinho said:**
> Hi everybody


Also having trouble getting my nvidia 6600GT to work, along with desktop effects, I-ve tried envy but that probably messed it more than i allready did, I now have 800x600 resolution screen.
Thanks for your time and please help a noob out!

Cheers.

For great help on nVidia driver installation, and before you play aroubnd with the xconf file, go here:

[http://albertomilone.com](http://albertomilone.com)

A great reference for nVidia stuff.

---

### Post by bobpur on 2007-10-19
I, also, Have a Nvidia 6600 GT and it worked fine with the nvidia-glx-new driver. 
I did a clean install and went to the restricted driver window and activated the driver.

                                                          Good Luck

---

### Post by HMartinho on 2007-10-19
Getting really pissed off...
It might be a DNS problem but I don-t know how to solve it.
I suspect it cause whenever i try to download a package it looks for the host name and displays an IP corresponding that host but....
Example, when I was trying to get googleearth:
Downloading from dl.google.com | 1.0.0.0:80...
and when it was trying to get wine it said:
downloading from  (whatever)|1.0.0.0:80...

so for both it isnt resolving the adress.

DNS problem would also explain why I can`t get pidgin working and why i had to enable ipv6 on firefox.
Could someone help me check if everything is ok with my connection?

Thanks in advance.

---

### Post by HMartinho on 2007-10-19
The problem with internet connection is solved.
I can't put my routers ip in the dns field, I use the ISP's dns and now it works.

Can't get my nvidia 6600gt to work now, settings must be all messed up, i've tried enabling restricted drivers with no result also tried envy to install the driver with no result also, when it restarts it goes in safe mode.

Could someone guide me through the nvidia installation process?

Tell me what to unninstall and what I'm doing wrong please.

Cheers.

---

### Post by HMartinho on 2007-10-20
IT'S ALIVE!!!

It works now, after reading a couple of guides I've managed to get compiz working just fine now.
Thanks to all who helped out.

Gonna try install GIS software now.

Thank you very much once again.

---

