---
title: "Install Issues"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by Jaems on 2008-03-22
Ok.

A few months ago I put ubuntu on my desktop pc (Sempron 3600+) Was a real pain- tried 7.10 and it hung at the very start on the hardware detection screen. In the end had a problematic but eventually successful install of 7.04.

I am really happy with linux, so when i bought a laptop with vista OEM on it i naturally set about getting a dual boot happening.

7.04 hung at 85% after installing 'br1tty'. Extensive searching suggested this was an obscure problem with no solution- the best i found was [http://ubuntuforums.org/showthread.php?t=454121]("http://ubuntuforums.org/showthread.php?t=454121")
and i have an Nvidia card...

So i downloaded the .iso for 7.10. All seemed to be going well until it started 'scanning the mirror'. Now it has hung again.

The only fix i found was in disabling network interfaces via busybox. I might have been successful, but i'll never know seeing as there is nowhere on the internet that tells me how to get back to the GUI or continue the install via command line....

So.

1) Does anyone know of a fix for either of these problems??

2) And regardless, i'd like to know how to leave busybox for next time i have installation issues.

Sorry if i am drudging up old problems :S        Laptop specs are-
-core duo 1.66
-3 gb ram
-512 Nvidia 8600 GS
installing to 130 GB of partitioned space with 2 gb swap space

---

### Post by timbounceback on 2008-03-22
Have you tried the Alternate CD? Sorry, I know it's a generic answer, but it usually helps.

---

### Post by Jaems on 2008-03-22
yup.


BUT

i just finished the install by totally ignoring the DHCP/network setup part. It went through fine and i am now in Ubuntuland. If anyone else has the 'scanning the mirror' issue, its that simple.

But then there is the next problem. In network connections there is no recognition of my wireless. I'm sure it either assumed there was no card and just disregarded it or the OS isn't listing it assuming i'm not looking for it.

Imma go look for an answer, but if you got any ideas, feel free to post 'em.....?

---

### Post by timbounceback on 2008-03-22
what wireless card are you using? ndiswrapper may be necessary :-). BTW, don't forget to uncomment all the lines in /etc/apt/sources.list before installing any software.

---

### Post by smurphy_it on 2008-03-22
Ndiswrapper (as previously suggested) or the restricted driver manager (system, administration, restricted drivers manager).

Otherwise, you'll have to start posting some info on your wifi hardware.
like in a terminal typing lspci -v
and posting the output here.

---

### Post by Jaems on 2008-03-22
amazing what google turns up.
[http://scraping.icebo.org/index.php/2008/02/29/kubuntu-on-medion-akoya-md-96630/]("http://scraping.icebo.org/index.php/2008/02/29/kubuntu-on-medion-akoya-md-96630/")
This  is the model below my laptop, so i am assuming the wlan is going to be the same. I got the driver and am now attempting a 'makefile' but i have NO idea what is going on. Currently stuck on the location of my header file.... Is there no simple way to do this?

---

### Post by forrestcupp on 2008-03-22
Did you try what was suggested?  First open up the Restricted Drivers Manager and see if it just lists your wireless.  If so, it's as easy as checking the 'enable' box.  If not, you can look into installing the ndiswrapper.  One of those should get you going.

BTW, the reason it stuck at the scanning of mirrors is because you didn't have an internet connection - no wireless working.

---

### Post by Jaems on 2008-03-22
I have tried them both. It is definitely not in the restricted drivers. I've got the driver for windows but i cant get Ndiswrapper to do it's thang. Wouldn't be suprised if it is just my lack of terminal ability though....

Edit- Got the GUI.... Sorry for the stupidity :S

---

### Post by Jaems on 2008-03-22
The drivers are in .exe. ndiswrapper also doesnt seem to support my chipset. I ripped the drivers out of my windows install and although they are 'installed'in the ndiswrapper GUI i can't modprobe them.



This is a networking issue i suppose, so i'll shuffle over to another board.

---

