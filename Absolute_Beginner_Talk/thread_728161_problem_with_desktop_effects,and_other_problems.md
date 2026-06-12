---
title: "problem with desktop effects,and other problems"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by stonecoldjha on 2008-03-18
i cant enable desktop effects on my ubuntu7.10.i have downloaded all updates,including compiz,but it doesn't.well,lemme tell you that this is for the third time that i installed ubuntu on my PC.everytime it was problematic .last time i made a few modifications in some files from the terminal as told here,but then after reboot ubuntu occupied only a fraction of my screen,with the remaining portion undisplayed.i tried enabling the deskop effects and then they worked,but it literally made my system too slow,scrolling,selecting things and many others became much slower,even though i have a RAM of 1 GB,and an intel core2duo 2 GHz processor.please help as i am fed up with windows,and want to switch entirely to linux.


then i typed again and got this output:

[B][SIZE="2"]sonu@sonu-desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
sonu@sonu-desktop:~$ [/SIZE][/B]

then i tried:"SKIP_CHECKS=yes compiz --replace" in the terminal

yea it seems that chipset is blacklisted as the output of my terminal read:
[B][SIZE="2"]sonu@sonu-desktop:~$ SKIP_CHECKS=yes compiz --replace
Checking for Xgl: not present.
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1024x76 to maximum 3D texture size (204: Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
[/SIZE][/B]

OK,its worth waiting to get support for chipset,but in the meantime will i have to carry on with crummy brown looks,devoid of any modern desktop effects.i switched to ubuntu7.10 with high expectations that went way nullified,i mean i have been a windows user ,and had been running xp of late which didn't have trouble installing some really exquisite effects as i installed vista transformation pack,on the same hardware configuration.but now that i lacerate windows a lot for it being prone to infections and all such things,frequent program crashes and all that,i decided to switch to something i still believe is better.i know ubuntu is highly customisable ,but how can i be helped...............am i left with the only option to wait.i have been facing a hell lot of problems,no splash screen,failure to install dock,no desktop effects,bizzare brown looks that i don't find captivating,though i am sure they will be one day.i can't even play videos on the web despite having installed flash several times in the terminal.............please do reply............and help me become a part of this linux community......help me solve all this,i am absolutely new to linux,with not even a tad of knowhow in this regard.

---

### Post by Xiong Chiamiov on 2008-03-18
I don't have much I can say to help you with your problem, but if you puncuate correctly, your post will be much easier to read.  And since this is all run by volunteers, we're much more likely to help you if we can figure out what you're saying easily.

---

### Post by stonecoldjha on 2008-03-18
the nittygritty is that i have **Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)** as my driver which seems to be blacklisted,i can't enable desktop effects,how do i get around this problem............my plight is in much greater detail above only if spend some time for that.thanks for reading.i don't like the brown default look of ubuntu.

---

