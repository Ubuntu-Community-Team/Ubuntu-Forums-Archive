---
title: "[SOLVED] My new ACER ASPIRE 5315"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by snypercore on 2007-12-24
Ok well first off this is my first post on the forums so, hi i guess and hope i can learn lots here.

Now my problem is,
im very new to linux and ubuntu is the only distro ive really gone into in any detail, i have it on my PC on a dual boot and im using it now. Now with xmas being 1 day away my gf has bought me a new laptop, the ACER ASPIRE 5315 to be exact, ive read ALOT of threads on the issues with installing ubuntu on this laptop but being a newbie and console commands going right over mu head right now i still find myself a little confused, and lets be honest come xmas day i want to be able to pop in the ubuntu disk and start using it asap :D

so, i know how much of a big favour this is to ask but could someone give me some easy instructions on what to do to get it all working (from what ive read theres issues with WLAN and sound) so some easy instructions with the terminal commands would be nice. Also will i be ablt to have desktop effects as i cant on my PC because i have an ATI X1950 and from what ive read its just a no no :( so will i be able to have all the effects on the laptop?


thanks snypercore

---

### Post by SOULRiDER on 2007-12-24
My friend has an Acer lapop too. WLAN didnt work out of the bix but there's plenty of people here to help you so theres no problem there. ATI cards aren't the best but yes, you can turn desktop effects on. Just post if you need any help installing or setting something up and we'll help you, just make sure you have a wired connection or it will be a b*tch to install wireless if youre 100% disconnected.

---

### Post by snypercore on 2007-12-24
> **SOULRiDER said:**
> My friend has an Acer lapop too. WLAN didnt work out of the bix but there's plenty of people here to help you so theres no problem there. ATI cards aren't the best but yes, you can turn desktop effects on. Just post if you need any help installing or setting something up and we'll help you, just make sure you have a wired connection or it will be a b*tch to install wireless if youre 100% disconnected.

oh shite being wired up slipped my mind, it still shouldn't be a problem though, but thanks for the reply and i have seen this post

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=610603](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=610603)

althought he has a slightly diff model the hardware is the same he just has some extra ram and a webcam, but the code he has there if i just paste that in the terminal in the order he has i should be ok?

---

### Post by SOULRiDER on 2007-12-24
It probably will, BUT im not sure aobut the compiz part. My suggestion is, set up wireless like that guide says and then we'll help you out with installingt he official ATI drivers.

Good luck. Post any issues you come across!

---

### Post by bigspottycat on 2007-12-24
I have an ACE ASPIRE 5602 and found it pretty easy to set up Ubuntu Gutsy. 

Wireless and sound both worked immediately.

To activate desktop effects you first need to ensure that the repositories are enabled (look in System-Admin-Software Sources), then go to System-Admin-Restricted Drivers Manager and enable the graphics card.

In a terminal type:```
 sudo apt-get install xserver-xg
``` (you may need to logout or restart at this point)
then in the terminal type:```
 sudo apt-get install compizconfig-settings-manager
```
There should now be a new menu item:
System-Preferences-Advanced Desktop Effects Settings

To install multimedia codecs (for mp3 etc)
Go to Add/Remove Application, search for 'Ubuntu Restricted Extras' and install them.
Install mplayer and firefox mplayer plugin. Firefox should prompt you for this when you try to play a video. 

Hope this helps.

---

### Post by snypercore on 2007-12-24
thanks ill try it out tomorrow when i get to open it :lolflag:

---

### Post by SOULRiDER on 2007-12-24
I bet you can't wait!

---

### Post by snypercore on 2007-12-24
lol yeah im all giddy like a kid, nah but my gf and her family are really "in the spirit" when it comes to xmas, unlike me so yeah i have to wait lol :P
but my fear of a frustrating xmas morning setting this lappy up is worrying me

---

### Post by MrKlean on 2007-12-24
I have an Aspire 5100 and when I got it..Vista was on it !  I deleted Vista...install 64bit Ubuntu...and haven't looked back LOL!!

---

### Post by snypercore on 2007-12-25
ok soi got my ACER ASPIRE 5315 and nuked vista so now i have ubuntu only and here are my problems (bear in mind im new to linux so terminal codes help :D)

no wireless
no sound
no compiz at all

please please please help i really need wireless as when i ge home wired will be near impossible and i desperately want compiz :D 

thanks


OK EDIT****

i manually went to add/remove and installed ndiswrapper and insgtalled the windows wireless driver that way and disabled the restricted one but when i type sudo modprobe ndiswrapper in termnial i get

dave@dave-laptop:~$ sudo modprobe ndiswrapper
FATAL: Could not open '/lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko': No such file or directory

and it still shows me no wireless, and i also get the same issues when trying to add ndiswrapper to startup

---

### Post by SOULRiDER on 2007-12-25
Someone here has the same laptop as you do. 
[http://ubuntuforums.org/showthread.php?t=600714](http://ubuntuforums.org/showthread.php?t=600714) Check that thread out, you'll find all answers there :) Good luck and ask anything you need :)

---

### Post by snypercore on 2007-12-25
i really apreciate the help but i dont understand some of that, like ndiswarapper i dont knwo what it is let alone how to use it... untill you reply though ill keep searching, also my card isnt stuck on roaming it just isnt "there"

EDIT***
 i followed this guide
[http://ubuntuforums.org/showthread.php?t=512828&highlight=atheros+ar5007eg](http://ubuntuforums.org/showthread.php?t=512828&highlight=atheros+ar5007eg)

and it didnt work at all still no option to connect to a wireless network or anything to do with wireless
and i got compiz working but i cant get to or install the compiz manager to change settings the package manager wont let me.
and now i cant do the sound tutorial i have downloaded these to my desktop:

alsa-driver-0,40.tar.gz
alsa-lib-.0.4.0.tar.gz
alsa-utils-0.4.0.tar.gz

and ermm i cant understand what to do next i get errors when i run the script given


thanks for any help given, i really want this laptop to be an ubuntu one and not go back to XP

---

### Post by SOULRiDER on 2007-12-25
Ok, for your wireless check thos out: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

For desktop effects settings type
```
 sudo aptitude install gnome-compiz-manager
```

What kind of audio card is it? i need some more info to keep on searching.

---

### Post by snypercore on 2007-12-25
ok well i got compiz working turned out in preferences for add/remove all the locations and what type of software to download was all disabled so i had to reenable and ill get back and edit this post about my wireless

i think im messing up when theres a * for which ever directory or version im using when sometimes i dont know as im that new to ubuntu so maybe somone can post the terminal code with the stars filled and tell me where to put what and which to download?

i realise im asking for a bit of someones free time but it will be much appreciated.

heres the wireless guide im using
[http://ubuntuforums.org/showthread.php?t=512828&highlight=atheros+ar5007eg](http://ubuntuforums.org/showthread.php?t=512828&highlight=atheros+ar5007eg)

and heres the sound
(a quote form another thread)

"The sound was pretty hard. I followed a combination of the instructions found here [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and [http://ubuntuforums.org/showthread.p...light=ar5007eg](http://ubuntuforums.org/showthread.p...light=ar5007eg). For the ALSA upgrade I followed the instructions given by the first link, but only after stopping alsa as outlined by the second link. Then, after compiling and installing alsa-utils, I went on to follow the instructions given in the second link starting with running alsaconf and followed that to the end. After rebooting, I went back to the first link, tried cat /proc/asound/card0/codec#* | grep Codec
and found that I had a Codec: Realtek ALC268"



many many thanks

---

### Post by bboypoprocks on 2007-12-26
i have an aspire 5315-2153 and had the same problems. i've got the wireless to work but still working on the sound. since i'm new to linux as well i can't give you terminal commands. but i'll tell you your goning to need to download and install ndiswrapper and then use ndiswrapper to install the atheros AR5007EG drivers. not AR5006EG. hope that helps a little.

---

### Post by snypercore on 2007-12-26
ok well im going to look into that now and as for what sound card i have this is kinda weird the volume control tells me i have a HDA Intel (ALSA mixer) which i think is what i have.


also how did you get your wireless to work then?


EDIT*******
i manually installed ndiswrapper in add/remove and installed the driver, but it still wont work and when i try to set ndiswrapper to run on startup i get errors and when i try to run it in terminal i get errors but ndiswraqpper deff says i have the right driver installed,

EDIT*** 
to anyone else having issues with the sound on this laptop try this guide:
[http://ubuntuforums.org/showthread.php?t=600714&page=11](http://ubuntuforums.org/showthread.php?t=600714&page=11)    worked perfectyl im very happy now i just need to sort my wireless 
and im done

this is the error i get with the wireless

dave@dave-laptop:~/ar5007eg-32-0.2/ar5007eg$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found

and yes i DEFF have ndiswrapper installed along with the driver

---

### Post by snypercore on 2007-12-26
bump

---

### Post by snypercore on 2007-12-26
ok i managed to fix all issues after a ubuntu reinstall for anyone with this laptop follow the link i posted for the sound tut and it will fix wireless,sound and compiz


thanks

---

### Post by SOULRiDER on 2007-12-27
Good to know you got it working. Would you mind markign the thread as solved under the Thread Tools menu?

Thank you :)

---

