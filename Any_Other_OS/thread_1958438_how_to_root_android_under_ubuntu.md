---
title: "how to root android under ubuntu"
date: 2012-04-14
forum: Any Other OS
---

### Post by Claus7 on 2012-04-14
Hello,

here is a small how to about rooting an android phone using linux environment. So, let's get started!

1) open synaptic and install the package eclipse
2) install sdk tools, which will enable you to install adb (emulator shell), which will help you to issue the commands from ubuntu in order to root your phone 
e.g. your android version might be froyo
go here: [http://developer.android.com/sdk/installing.html](http://developer.android.com/sdk/installing.html) and download the [COLOR="Blue"]SDK Tools, r18[/COLOR] on the left hand side of the page (mind that the number 18 might not be the same)
3) unzpip the file, go into the folder [COLOR="Red"]tools[/COLOR] and execute ./android
a graphical environment will open and from there install all those packages (click them) which are specific to your phone
4) go then into [COLOR="DarkRed"]platform tools[/COLOR] and initiate the adb like ./adb
5) follow **this** guide here: [http://blog.mx17.net/2011/08/howto-root-your-xperia-x10-mini-pro.html](http://blog.mx17.net/2011/08/howto-root-your-xperia-x10-mini-pro.html)
which explains what you do after you have installed the sdk package with the adb emulator shell
**ATTENTION**
i) connect your phone, do not mount it (I did not)
ii) the first two parts of the provided guide (step 5) should be accomplished from your terminal and **NOT** from the adb shell
iii) in the end, while rebooting, your phone might not actually reboot, yet just shut down, just open it yourself

6) get rid of the unnecessary apps that eat your memory
follow this: [http://ot-990.blogspot.com/2012/03/how-to-uninstall-system-apps-alcatel-ot.html](http://ot-990.blogspot.com/2012/03/how-to-uninstall-system-apps-alcatel-ot.html)
and install the packages from here:
[http://www.apktops.com/es-file-explorer-1-6-1-3.html](http://www.apktops.com/es-file-explorer-1-6-1-3.html)
[http://www.apktops.com/link2sd-2-0-3.html](http://www.apktops.com/link2sd-2-0-3.html)

it is better to move the apps you do not need under /sdcard/backups/apps

the apps that I safely removed were:
vending (android market)
youtube
twidroid
touchpal and all its components (have an alternative keyboard installed though)
shazam
marketupdater
maps
layar
google all
gmail
geniewidget
fbandroid
accuweather
parlingo

more or less 20MB of internal storage and 50MB of internal memory will be freed like that
I noticed that after I had rooted my phone, it became more responsive...

Hope it helped,
Regards!

---

### Post by arasbm on 2012-06-16
Thanks for sharing your method. But I think a lot of the steps you provide here are for setting up the android development environment and are not really necessary for rooting your phone. Do you know of an straight forward guide for moding android phones and installing new images such as the CyanogenMod on them?

---

### Post by Claus7 on 2012-06-16
Hello,

glad if it can provide some help. Concerning your answer I have not dealt so much with installing other roms on my phone. I do not know whether this link helps:
[http://x-ewra.blogspot.gr/p/manual.html](http://x-ewra.blogspot.gr/p/manual.html)

This is what I came across, while searching some days ago out of curiosity. If they implement CyanogenMod on my phone, maybe I will search it a little bit more as they say that is really nice rom.

Regards!

---

### Post by psyclechick on 2012-07-05
> **arasbm said:**
> Thanks for sharing your method. But I think a lot of the steps you provide here are for setting up the android development environment and are not really necessary for rooting your phone. Do you know of an straight forward guide for moding android phones and installing new images such as the CyanogenMod on them?
 
To root nearly all Android devices on Ubuntu you can use SuperOneClick from here:
[http://shortfuse.org/?page_id=2](http://shortfuse.org/?page_id=2)
 
Support can be found here: [http://forum.xda-developers.com/showthread.php?t=803682](http://forum.xda-developers.com/showthread.php?t=803682)
 
To install a custom recovery such as CWM et al you will still need the OP's method for setting up ADB and/or Fastboot to flash the recovery image which will then allow you to flash custom roms to your hearts content :D
 
Here is another good guide:
 
[http://rootzwiki.com/topic/20770-guideinstall-java-android-sdk-adb-and-fastboot-in-linux-ubuntu-and-mint12/](http://rootzwiki.com/topic/20770-guideinstall-java-android-sdk-adb-and-fastboot-in-linux-ubuntu-and-mint12/)
 
With Ubuntu popularity on the rise there are more and more good how-to's out in the Android community as well to peruse.
 
Of course...these are just more suggestions to follow on from the original post ):P

---

### Post by sunfromhere on 2012-07-07
I just got my first Android phone yesterday and it looks like I will root it by tonight.
So thanks for the guide.

The idea that I cannot remove some apps on my phone annoys me. F.e. Facebook app (not from market, the one that comes with phone). For the love of god, just let me uninstall the thing.

---

### Post by Claus7 on 2012-07-15
Hello,

> **psyclechick said:**
> To root nearly all Android devices on Ubuntu you can use SuperOneClick from here:
[http://shortfuse.org/?page_id=2](http://shortfuse.org/?page_id=2)
 
Support can be found here: [http://forum.xda-developers.com/showthread.php?t=803682](http://forum.xda-developers.com/showthread.php?t=803682)
 
To install a custom recovery such as CWM et al you will still need the OP's method for setting up ADB and/or Fastboot to flash the recovery image which will then allow you to flash custom roms to your hearts content :D
 
Here is another good guide:
 
[http://rootzwiki.com/topic/20770-guideinstall-java-android-sdk-adb-and-fastboot-in-linux-ubuntu-and-mint12/](http://rootzwiki.com/topic/20770-guideinstall-java-android-sdk-adb-and-fastboot-in-linux-ubuntu-and-mint12/)
 
With Ubuntu popularity on the rise there are more and more good how-to's out in the Android community as well to peruse.
 
Of course...these are just more suggestions to follow on from the original post ):P

nice to add superoneclick here in this thread. Unfortunately, as you mention, is works nearly for all phones, and mine was an exception to this rule. From what I have seen it might be the fastest way for rooting phones if it works.

Thanks also for the nice comments. I just wrote down what it worked for me also for other users to check out.

> **sunfromhere said:**
> I just got my first Android phone yesterday and it looks like I will root it by tonight.
So thanks for the guide.

The idea that I cannot remove some apps on my phone annoys me. F.e. Facebook app (not from market, the one that comes with phone). For the love of god, just let me uninstall the thing.

I hope that this is helpful and yes! you will be able to get rid off those apps that you think are redundant. Watch out though, which applications you are uninstalling as this might cause some problems to your phone. E.g. I do not use the default messages application, yet I have seen that it is not a nice idea to remove it. I just froze it. And do not remove jrdsensor, if you have such kind of an application.

Regards!

---

### Post by Regisz on 2012-10-31
Thx your method, Claus7. But unfortunately the step 5 can not be followed because of /sqlite_stmt_journals dir can not be founded on my phone (Samsung Galaxy 3 with 2.2 (Froyo)). Any solution? (I use Ubuntu 12.04). Thx!

---

### Post by northrup on 2012-11-05
> **arasbm said:**
> Thanks for sharing your method. But I think a lot of the steps you provide here are for setting up the android development environment and are not really necessary for rooting your phone. Do you know of an straight forward guide for moding android phones and installing new images such as the CyanogenMod on them?

That depends on the manufacturer of the phone.  For Samsung phones, for example, you can use Heimdall for that.  Instructions for Ubuntu installation can be found [here](http://www.ivegotavirus.com/heimdall-open-source-alternative-to-odin/).

---

### Post by tuxonapogostick on 2012-12-19
> **sunfromhere said:**
> The idea that I cannot remove some apps on my phone annoys me. F.e. Facebook app (not from market, the one that comes with phone). For the love of god, just let me uninstall the thing.
Well said!

---

### Post by sheldon-corey on 2013-11-10
at the minumum you will need adb AND Fastboot to root any device iOS / Android / Samba its just the facts.......everything else in the OP is for running a development build enviroment, You ABSOLUTLEY DON'T need eclipse for rooting any android....

---

### Post by 3dmatrix on 2013-12-05
I had been trying to figure out since a long time how I could root an Android phone completely in Ubuntu.
I searched a lot of different android developers forums but most of them mostly talked about doing it on windows comp.
I finally tried unlocking the bootloader of my mobile with fastboot and ADB (installed from the repo) and it was so easy to do that.
But I still need help in rooting my phone. Does any one has any experience doing it esp. on a Huawei phone ?
I would also like to know if there is any way to keep a backup of my rom so that if anything goes wrong I could revert back to it.
Kindly advise.

---

### Post by Claus7 on 2013-12-25
Hello,

I think that in order to get some more help in order to root your phone, you will have to provide more info about the phone itself and which were the steps that you tried to follow and at which point you faced a problem. Some users with similar experience (using the same phone) will be able to respond and help you, since in many cases there are some differences from one phone to the other and the rooting procedure.

Now, I have not used a backup procedure up to now to my phone or different roms, yet I think that you should take a look on ROM Manager - ClockworkMod. I think that this should be the place to start for backing up your phone.

Regards!

---

### Post by Osmodivs on 2014-02-03
Hello.
So, I installed _Eclipse_ and the _Android SDK_ from my Lubuntu 13.10 64bits.
I can now login to my phone:

127|shell@android:/

But the link of the original post sends me to a specific brand phone tutorial (**Xperia**),I have an **LG LX3 **with  Android 4.1.2 and  Kernel version 3.4.0. so I can't access the first directory because It does not exist.

127|shell@android:/ $ cd /sqlite_stmt_journals                                 
/system/bin/sh: cd: /sqlite_stmt_journals: No such file or directory

I thought every android was the same, so what are the directories I need to access in order to root my phone?

---

