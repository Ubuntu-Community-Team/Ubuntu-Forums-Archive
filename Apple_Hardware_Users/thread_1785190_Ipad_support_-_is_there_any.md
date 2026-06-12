---
title: "Ipad support - is there any?"
date: 2011-06-17
forum: Apple Hardware Users
---

### Post by keevill on 2011-06-17
Am I correct in believing that there is currently no way to put songs/vdo/music onto an Ipad1 using Ubuntu 10.0xx ?
I have tried the following :
Amarok - doesn't even see the Ipad
Banshee ( v 2.2 ) can see the Ipad and looks to be copying the songs across but nothing shows up in the Ipad.
Rythmbox opens up when the Ipad is connected but it performs just the same as Banshee i.e it reports copying over to Ipad and even after leaving it connected for 10 mins or so, nothing has been copied to the Ipad.
GTKpod can't even see the Ipad.
Itunes installed into Wine doesn't see the Ipad either.
I guess I am forced to  use a dual boot into Win and Itunes which works flawlessly but it's not really what I want to do. 
It's a bit inconvenient
( And I haven't even talked about pictures yet ! Fspot opens also when its connected but nothing can be copied to the Ipad )
This is not a rant but a cry for help in desperation
:-(
It's surprising really as the machine shows up in the places 
-keevill-

---

### Post by para-banana on 2011-06-19
Hi,

I haven't tried it with music, but everything else works!

libimobiledevice: [http://ubuntu-install.blogspot.com/2011/04/connect-ipad-and-ipod-with-ubuntu.html](http://ubuntu-install.blogspot.com/2011/04/connect-ipad-and-ipod-with-ubuntu.html)

Hook up your iPad to your PC and a window opens automatically showing the folders of the installed apps.
Now you can copy your files into the folders of your apps. Unfortunately you will not get access to system and apple apps folders (e.g. iPod). Anyhow you can transfer movies (azul app...), ebooks (goodreader, iAnnotate...) ...

However you will need a windows system to update your device! (Wine works only until iTunes version 7.x)
I managed that by installing a virtual machine (Oracle VM Virtual Box) with win7 and iTunes. This is the only way to make backups and to upgrade the iPad.
Please consider that the virtual hard drive of your VM should have at least 10GB, because iTunes will start making a backup automatically and if the drive is not big enough it will crash! Furthermore consider that you always have to activate the USB support for your VM during an upgrade! When the iPad restarts during an upgrade the connection drops and you have to enable the iPad USB connection again immediately, otherwise your iPad crashes! Thus stand by during upgrading your iPad!

If you have bought your iPad recently, you should definitively upgrade it, otherwise it continues gathering location data.

Hope I could help you :-)
I have had the same problem :-)

---

### Post by keevill on 2011-06-20
> **para-banana said:**
> Hi,

I haven't tried it with music, but everything else works!

libimobiledevice: [http://ubuntu-install.blogspot.com/2011/04/connect-ipad-and-ipod-with-ubuntu.html](http://ubuntu-install.blogspot.com/2011/04/connect-ipad-and-ipod-with-ubuntu.html)

Hook up your iPad to your PC and a window opens automatically showing the folders of the installed apps.
Now you can copy your files into the folders of your apps. Unfortunately you will not get access to system and apple apps folders (e.g. iPod). Anyhow you can transfer movies (azul app...), ebooks (goodreader, iAnnotate...) ...

However you will need a windows system to update your device! (Wine works only until iTunes version 7.x)
I managed that by installing a virtual machine (Oracle VM Virtual Box) with win7 and iTunes. This is the only way to make backups and to upgrade the iPad.
Please consider that the virtual hard drive of your VM should have at least 10GB, because iTunes will start making a backup automatically and if the drive is not big enough it will crash! Furthermore consider that you always have to activate the USB support for your VM during an upgrade! When the iPad restarts during an upgrade the connection drops and you have to enable the iPad USB connection again immediately, otherwise your iPad crashes! Thus stand by during upgrading your iPad!

If you have bought your iPad recently, you should definitively upgrade it, otherwise it continues gathering location data.

Hope I could help you :-)
I have had the same problem :-)

Thx for trying to help.
I have done as suggested and installed that software upgrade to Ubuntu 10.04 however, whilst the Ipad 2 appears in the devices when viewing in Rhythmbox, I cannot successfully move songs or podcasts into the Idevice.
It shows the job going ahead when I drag and drop within RB into the Idevice but actually the file is not transferred.I can see the file actually transferred into the Idevice when I view in RB.
However, when I physically open the Idevice and check, the file is not there.
Moreover, when I close down RB and re-open, the song/podcast is no longer showing in the Idevice within RB
The only way I can get stuff ( movies, songs, podcasts , photos into the damn thing , is to use an app called Ifiles which works but does not put the files into the appropriate folders. i.e audiobooks into ipod AB and songs into ipod Songs and movies into Video.
( Idevice = Ipad 2 or Iphone 4G )

-keevill-

---

