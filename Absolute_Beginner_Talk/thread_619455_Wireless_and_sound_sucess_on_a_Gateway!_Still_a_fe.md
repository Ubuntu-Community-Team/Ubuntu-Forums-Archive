---
title: "Wireless and sound sucess on a Gateway! Still a few kinks though..."
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Paradoxfox93 on 2007-11-21
Okay...sure, I've only been unsing Linux/Ubuntu for about a week now; however, I am throughly in love with it. It's not nearly as rough to learn as I had anticipated.  I was a little scared at first when Gutsy crashed on me every time I loaded, when I had wireless and sound problems and the threads I read made them seem eternally insoluble.  I am one stubborn SoB though and I made it work!  So I thought since I had such a rough time with it, others using gateways, similar hardware, even and especially MT3422's like me! There are a few things still wrong with the process but I have sound and wireless so I'm happy for the moment.  I'm posting so that maybe I can get a bit of help with the bugs and so that others with similar hardware/laptops will find help. I noticed a lot of people looking for help on gateways like I am.  The wireless chipset is a Realtek 8185 and I think it's a Zebra 100 as thats what it says on the sticker on the bottom of my laptop but I haven't seen any references to that or anything else anywhere.  THe audio card is a Sigmatel 9200

Here is what I have Observed:

64bit Gutsy crashes every time a network is attempted, wired or wireless. As such, very little was really attempted beyond about a dozen reinstalls till someone suggested I try feisty.  I supose gutsy might work in 32 bit but since I have feisty working, I'm not messing with that at the moment.  Let me know if you have success with it on this model.

So basically I had no sound and no wireless even though I could see my hardware and they had drivers.

Wireless was pretty much easily solved by Following Kevdog's instructions for manually installing Ndiswrapper with the 98 driver.  The driver can be found on the realtek website [Http://www.realtek.com.tk](Http://www.realtek.com.tk) and it is listed as the "ME" version but the .rar file contains both 98 & ME drivers.

Thread with Kevdog's Ndiswrapper Instructions:

[http://ubuntuforums.org/showthread.php?t=571129](http://ubuntuforums.org/showthread.php?t=571129)

Sound was a bit more rough and in the end I never was able to finish installing the utils package and I don't understand why.  However the lib and Drivers updated fine.  I guess since the Patch goes into the drivers the sound works.  I'm wondering if I'll have problems since utils were not updated.  If anyone who knows if this is a largely irrelevant problem or how to fix it would share, I'd appreciate the information and will post my results with them.  Thanks to MyR for translating the patch instructions into something I could follow in Ubuntu.  Essentially Alsa released a patch for the problem with Sigmatel 9200 audio hardware and you just patch up an update for Alsa and manually install it.  However, removing the old alsa seems unecessary and I didn't do that (Though I did the first time, same errors were reported when trying to make utils). You need the curses dev lib which can be gotten from synaptic to update the utils.

Thread with MyR's instructions:
[http://ubuntuforums.org/showthread.php?t=614903](http://ubuntuforums.org/showthread.php?t=614903)

You will need to modify them to the current alsa & patch version.  Also many of the commands need a sudo prefix.  

Here is the error I recieved when sudo make:

Making all in include
make[1]: Entering directory `/usr/local/src/alsa/alsa-utils-1.0.15/include'
make  all-am
make[2]: Entering directory `/usr/local/src/alsa/alsa-utils-1.0.15/include'
make[2]: Leaving directory `/usr/local/src/alsa/alsa-utils-1.0.15/include'
make[1]: Leaving directory `/usr/local/src/alsa/alsa-utils-1.0.15/include'
Making all in alsactl
make[1]: Entering directory `/usr/local/src/alsa/alsa-utils-1.0.15/alsactl'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/local/src/alsa/alsa-utils-1.0.15/alsactl'
Making all in alsaconf
make[1]: Entering directory `/usr/local/src/alsa/alsa-utils-1.0.15/alsaconf'
Making all in po
make[2]: Entering directory `/usr/local/src/alsa/alsa-utils-1.0.15/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/usr/local/src/alsa/alsa-utils-1.0.15/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/alsa/alsa-utils-1.0.15/alsaconf'
make: *** [all-recursive] Error 1


Also when I sudo ./configure, this pops up in the middle:

config.status: WARNING:  alsaconf/po/Makefile.in seems to ignore the --datarootdir setting


Still, Sound and wireless work!  I'm happy!  No vista, no microcrack! Hope this helps anyone who needs it!

---

### Post by pheonix7117 on 2008-02-09
thanks a lot! this worked perfectly. 
a couple updates: 
the newest stable ndiswrapper 1.52 works fine with the realtek 8185 windows 98 driver, too.
to get the sound working with alsa, all i had to to was go to [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) and download the latest sources for the driver, lib, and utils, then compile, make, make install all three sources. works fine for me, though i did get those same error messages as you

---

### Post by Paradoxfox93 on 2008-07-11
A small update.  Sound work right off the bat on Hardy 8.04.  Wireless works with ndiswrapper as well.  I download 1.51 with wget as per kevdog's instructions but it shows up as 1.52 idk wtf is up with that but it works.

And btw...hardy is sweet...even if 64bit is still a ***** to my wireless hardware.

---

