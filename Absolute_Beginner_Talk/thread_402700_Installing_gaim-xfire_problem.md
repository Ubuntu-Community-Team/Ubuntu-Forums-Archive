---
title: "Installing gaim-xfire problem"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by jedishiz on 2007-04-06
Hi I am new to linux, however, I have been trying all day to get x-fire installed on my linux ubuntu edgy setup.  I downloaded the gaim-xfire-0.6.0.tar.gz file... and unpacked it. When I do ./configure I seemed to have mulitple files missing, therefore I Installed build essential and other ones it said I was missing. The only thing I believe I am missing now is something called makeinfo. If anyone can tell me where to get this file I would greatly appreciated it. I've looked in the Synaptic and across all the forums, with little luck. I may not be looking in the right place though:( Thanks in advance for the help.


I hope I am on the right track lol:P:lolflag:

---

### Post by Origin415 on 2007-04-06
Can you post the last part of the print out from ./configure? We can help you better that way.

---

### Post by brennydoogles on 2007-04-06
> **jedishiz said:**
> Hi I am new to linux, however, I have been trying all day to get x-fire installed on my linux ubuntu edgy setup.  I downloaded the gaim-xfire-0.6.0.tar.gz file... and unpacked it. When I do ./configure I seemed to have mulitple files missing, therefore I Installed build essential and other ones it said I was missing. The only thing I believe I am missing now is something called makeinfo. If anyone can tell me where to get this file I would greatly appreciated it. I've looked in the Synaptic and across all the forums, with little luck. I may not be looking in the right place though:( Thanks in advance for the help.


I hope I am on the right track lol:P:lolflag:

Depending on which version of Ubuntu/Gaim you use, there should be no reason to install by source for this plugin, as there are .deb files available for most of them. If you are using edgy eft and GAIM 1.5 you can get the plugin [here.]("http://downloads.sourceforge.net/gfire/gaim-xfire_0.6.0-gaim1.5-etch1_i386.deb?modtime=1158283715&big_mirror=0") For Dapper Drake and version 1.5 you can get it [here.]("http://downloads.sourceforge.net/gfire/gaim-xfire_0.6.0-gaim1.5-dapper1_i386.deb?modtime=1158283702&big_mirror=0") If you happen to have GAIM version 2.0 Beta, you can download the plugin [here.]("http://downloads.sourceforge.net/gfire/gaim-xfire_0.6.0-gaim2.0b3.1-dapper1_i386.deb?modtime=1158283730&big_mirror=0") Once you have downloaded the appropriate .deb file from the link above, simply double click it and click install, and you should be ready to add your Xfire account to GAIM. If you have any questions, feel free to post back!!

---

### Post by jedishiz on 2007-04-07
> **brennydoogles said:**
> Depending on which version of Ubuntu/Gaim you use, there should be no reason to install by source for this plugin, as there are .deb files available for most of them. If you are using edgy eft and GAIM 1.5 you can get the plugin [here.]("http://downloads.sourceforge.net/gfire/gaim-xfire_0.6.0-gaim1.5-etch1_i386.deb?modtime=1158283715&big_mirror=0") For Dapper Drake and version 1.5 you can get it [here.]("http://downloads.sourceforge.net/gfire/gaim-xfire_0.6.0-gaim1.5-dapper1_i386.deb?modtime=1158283702&big_mirror=0") If you happen to have GAIM version 2.0 Beta, you can download the plugin [here.]("http://downloads.sourceforge.net/gfire/gaim-xfire_0.6.0-gaim2.0b3.1-dapper1_i386.deb?modtime=1158283730&big_mirror=0") Once you have downloaded the appropriate .deb file from the link above, simply double click it and click install, and you should be ready to add your Xfire account to GAIM. If you have any questions, feel free to post back!!


I'm going to try this thanks. Not sure which version of gaim I have so i'll just guess and check.

---

### Post by jedishiz on 2007-04-07
WOOHOO  Thanks much...the .deb files worked great!  Now xfire works like a charm.. Now what was it that I was doing lol? Compiling?

---

### Post by igknighted on 2007-04-07
> **jedishiz said:**
> WOOHOO  Thanks much...the .deb files worked great!  Now xfire works like a charm.. Now what was it that I was doing lol? Compiling?

Yep.  The errors you got were because you don't have a compiler installed by default.  If you run into anything you do need to compile, get the package "build-essential" from apt-get or synaptic.  And get checkinstall as well.  Substituting "checkinstall" wherever your compile directions say "make install" will save you a lot of trouble later on, as it will make the source into .deb files which as you discovered are very nice and easy for the system to deal with, and should you ever want to upgrade or remove the program, it makes things much easier, as source installed things do not like doing this normally.

---

### Post by nanonomic on 2007-05-05
I installed through the .deb and in /usr/lib/gaim theres a libxfire.so, but for some reason when i go to add an account, theres no option for xfire.  what should i do?

---

