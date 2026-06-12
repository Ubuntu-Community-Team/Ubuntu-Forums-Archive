---
title: "Very Very New to Linux and Ubuntu, and I need help with a few items."
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by renay on 2007-06-05
Hi.

Newbie here with linux and Unbuntu.  I installed 7.04 server on an old Toshiba Tecra8000 and I have a problem with the GUI.  I would like to learn from a gui stand point and is not a production server just a learing tool for now until I get used to CLI.

Four things I would love you have assistance with are:
1. Wireless network:
     I am using a linksys wpc11b v4 and i think comes with rlt8081 but not sure how to install the drivers.
2. GUI:
     I don't have access to network so how can i update and or use the (sudo aptitude install ubuntu-desktop)?
3. Resolution:
    I have neomagic but will need to install drivers?
4. Sound.
    How do i find out what i have and how to install?

Any help from this community is greatly appreciated.
Renay

---

### Post by jvc26 on 2007-06-05
Might seem quite an obvious suggestion, but rather than trying to make it all work via installation of the server version with no GUI and then trying to install the GUI could you possibly install just the normal desktop version. At the end of the day that will put the GUI on (solving one issue) and will probably make it easier to solve your connectivity issues too with GUI interfaces. Then you can learn your way around Ubuntu, get used to the CLI for a server and then get it all set up as a server with a CLI only interface at a later date. You could also get hold of the alternate install cd, apt-cd add (or something like that, the command is on the forums somewhere am afraid since a re-install I dont have all my bookmarks yet) and you could install the ubuntu-desktop package via that ```
sudo apt-get install ubuntu-desktop
``` to cut a long story short, that adds the cd as a repo and then you can install the small number of apps which are on the cd from that even without internet connectivity.
Il

---

### Post by renay on 2007-06-06
Thanks for you advise Illuvator.  I did a full install of 7.04 desktop and now have an active GUI and do have sound but my resolution does not have an option?  it only has 640x480 with 60Hz and i cant seem to get it any higher.  

Also I see that it notices i have rlt8180l but how do i get it to load?

Any suggestions?

AGain any help will help me gain linux

Thanks
:o

---

### Post by Bohlio on 2007-06-06
Posting information about your graphics hardware will probably help in getting it set up. and sorry, but i cant help you much with the internet part... :-(

---

### Post by renay on 2007-06-06
Thank you Bohilo.  I am using a Toshiba Tecra8000 laptop with a device from Neomagic Corporation.
the product in question is NM2200 [MagicGraph 256 AV] does that help?

AGain thanks to all that helps
:o

---

### Post by renay on 2007-06-06
I did a bit more research and did find a solution to my resolution issue.
Thanks to physx i was able to use his suggestion by modifying both HorzSync and VertRefresh in X11/xorg.conf.  

TO:
HorizSync 36-52
VertRefresh 36-60 

Thanks for all your help on this.
Now on to the linksys wpc11b v4 issue.

Does not seem to be active or being detected by the system.  I know its a rtl8180l but how do i get the system to recognize it?


AGain thanks for any assist on this
:D

---

### Post by renay on 2007-06-06
Hi all,

Just wanted to let you know that I was able to net my rtl8180l to work now.

I was looking at other threads and found soundguy666:

He suggested to use the command "modprobe r818x" rather than insmod and when I looked at my network, i now see my wireless connection roaming mode enabled.  YEAH.

I am now set i hope.  I will test out my wireless when I get home and hopefully sees my AP.

I reply once i get this going.

AGain, thanks to all that helped

Pease

:KS

---

### Post by Bohlio on 2007-06-06
Glad to hear you got your problems solved :-) 
Usually, If you encounter a problem, the chances are really high that someone else has already asked about it here :-)

Have fun Ubuntuing!

---

