---
title: "Set up Gecko SDK and Mplayer in Opera... How to???"
date: 2010-03-13
forum: Apple Hardware Users
---

### Post by migel_wimtore on 2010-03-13
Hi. I really want to make the switch from Firefox to Opera as it is so much faster and more stable. But am having real trouble getting mplayer to work.

I was wondering if anyone who has successfully managed to get mplayer plugin working in the Opera web browser, or knows how to, could help me do the same. Iv been trying for a couple of days now and its getting repetitive.

Iv tried following the instructions here: 

[http://www.opera.com/docs/linux/plugins/install/](http://www.opera.com/docs/linux/plugins/install/)

I think im having trouble with Gecko SDK, havnt been able to find a package thats ppc compatible (am running Karmic on an iBook G4). 
Though i found an RPM package that was and converted it with Alien, not sure if it actually worked though. 

I have XULrunner 1.9.1 and mplayer installed.

Im falling down on this step of the above linked tutorial:

"Type ./configure --enable-x [--with-gecko-sdk={path}] where {path} is the path to the Gecko SDK" 

But have tried just running "./configure" and "make" from within the directory, without, of course, the desired effect.

Also im not sure when it says "Locate the files mplayerplug-in*.{so,xpt}" what or where "mplayerplug-in*.{so,xpt}" is supposed to be.

Sorry for the long post, trying to give as much detail as might be helpful to anyone who is trying to help me.

Please help me. :D

---

### Post by linuxopjemac on 2010-03-13
you could start here
[https://help.ubuntu.com/community/MPlayer/CVS](https://help.ubuntu.com/community/MPlayer/CVS)
Gecko SDK
[https://developer.mozilla.org/en/Gecko_SDK](https://developer.mozilla.org/en/Gecko_SDK)

I think the SDK is in the repository and it's called xulrunner
there is also a package called gecko-mediaplayer, which sounds like the mplayer-plugin

---

### Post by migel_wimtore on 2010-03-13
I already visited the second page you linked to. Unfortunately, it doesnt have a PPC download available for SDK. The second one seems like a lot of fuss considering i already have mplayer. I already have gecko media player and XULrunner installed as well. 

Its actually getting mplayer functioning within Opera thats proving a pain.

:confused:

---

### Post by migel_wimtore on 2010-03-14
Well, iv managed to get opera to recognise mplyaer when you go to the "opera:plugins" page. 

However, it still wont stream content.

Where im getting stuck in the tutorial is "Type ./configure --enable-x [--with-gecko-sdk={path}] where {path} is the path to the Gecko SDK". Because, i am using XULrunner i changed "with-gecko-sdk" to "with xulrunner-sdk" and put the path to the xulrunner file (which contains a folder called sdk. It manages to get though allot before out putting "ARE YOU SURE YOU WANT TO BUILD WITHOUT GTK? BECAUSE mplayerplug-in WITHOUT GTK TAKES AWAY FUNCITIONALITY".

Getting opera to recognise the mplayer plug-in has been a little encouraging, just wish i could get it working as well.

---

### Post by migel_wimtore on 2010-03-14
Update: I guess all the successful steps from all the failed tutorials i followed must have made their own near whole as Divx is now working. Some quicktime files are also working. 

However youtube does not play (just an empty box (and that thanks to the flashplugin-alternative.so. I remember that youtube wouldnt work in firefox running mplayer untill a certain script was loaded through greasemonkey, so may give up on that one.

However, if anyone has successfully got all round video streaming in opera using mplayer, including youtube if posible, and could take a minute to give me some pointers that would be appreciated.

Cheers.

---

