---
title: "Sound isn't working."
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by deville75 on 2006-05-24
I just installed Ubuntu and the sound doesn't work.  It says volume is at max and the music plays in "CD Player", but i dont hear anything.

What do I do?


Actually i just realized that the Speakers were not connected properly :S my bad.. BUT there is still a problem.

When i open music or video files it doesnt work.  For example, a video file opened in Totem gives me this error:

         Totem Could Not Startup: The video output is in use by another application. Please close other video applications, or select another video           output in the Multimedia Systems Selector.

When i try opening an audio file in XMMS i get an error saying it could not play, and tells me to check my sound driver config and other things like that.. but after a little while i hit play a few times and the music plays... Whats this mean?

---

### Post by Ben Sprinkle on 2006-05-25
its cuz u need the codecs to play it go in adept or the package manager and goto sound there , there should be some there:D

---

### Post by deville75 on 2006-05-25
I c.. so this should allow me to play DVDs?  Don't i need video codecs for that... anyway i'll check it out and see what happens

---

### Post by youthforlinux on 2006-05-25
yea u need to get the video codecs but if ur having a hard time use EasyUbuntu or Automatix

EasyUbuntu: [http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html)
Automatix: [http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)
or
[http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)

---

### Post by mlind on 2006-05-25
see [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by youthforlinux on 2006-05-25
yea that helps out a lot too

---

### Post by deville75 on 2006-05-25
[QUOTE=youthforlinux]yea u need to get the video codecs but if ur having a hard time use EasyUbuntu or Automatix

EasyUbuntu: [http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html)
Automatix: [http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)
or
[http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)[/QUOTE]


Hey, i tried Easyubuntu (BETA) and it gave me an error saying i need to repair broken packages.. What does this mean? 

THe other two jus keep saying ther is no such directory...

---

### Post by deville75 on 2006-05-25
Okay, i got DVD video to work!! Yes!!! my audio works fine, and now i just need streaming video to work and so how do i get *totem-xine-firefox-plugin*

Also, i still would like Easyubuntu to work... cuz it seems it has the ability to activate my Nvidia card's 3D rendering capabilities.  (I installed the vesa driver because the nv driver wouldn't work)

---

### Post by youthforlinux on 2006-05-26
[QUOTE=deville75]Okay, i got DVD video to work!! Yes!!! my audio works fine, and now i just need streaming video to work and so how do i get *totem-xine-firefox-plugin*

Also, i still would like Easyubuntu to work... cuz it seems it has the ability to activate my Nvidia card's 3D rendering capabilities.  (I installed the vesa driver because the nv driver wouldn't work)[/QUOTE]
are u using breezy or dapper?

---

### Post by youthforlinux on 2006-05-26
Dapper:[https://launchpad.net/distros/ubuntu/dapper/+package/totem-xine-firefox-plugin](https://launchpad.net/distros/ubuntu/dapper/+package/totem-xine-firefox-plugin)
Breezy:[https://launchpad.net/distros/ubuntu/breezy/+package/totem-xine-firefox-plugin](https://launchpad.net/distros/ubuntu/breezy/+package/totem-xine-firefox-plugin)

---

### Post by deville75 on 2006-05-26
... Breezy or Dapper? i dunno how do i find out, and whats the difference?

---

### Post by Sef on 2006-05-26
> Breezy or Dapper? i dunno how do i find out, and whats the difference?

System > About Ubuntu

Breezy is the current stable.  Dapper is the next current stable.  

For what's in Dapper, [click here.]("http://www.ubuntu.com/testing/dapperrc")

---

### Post by deville75 on 2006-06-01
[QUOTE=Sef]System > About Ubuntu

Breezy is the current stable.  Dapper is the next current stable.  

For what's in Dapper, [click here.]("http://www.ubuntu.com/testing/dapperrc")[/QUOTE]


Ok i got the plugin, but this is what comes up on Console when i try installing:

[COLOR="DarkGreen"]deville75@YingYang:~/Desktop/Stuff/Programs$ sudo dpkg -i totem-xine-firefox-plugin_1.2.1-0ubuntu1~breezy1_i386.deb
Password:
Selecting previously deselected package totem-xine-firefox-plugin.
(Reading database ... 74824 files and directories currently installed.)
Unpacking totem-xine-firefox-plugin (from totem-xine-firefox-plugin_1.2.1-0ubuntu1~breezy1_i386.deb) ...
Replacing files in old package totem-xine ...
dpkg: dependency problems prevent configuration of totem-xine-firefox-plugin:
 totem-xine-firefox-plugin depends on totem-xine (= 1.2.1-0ubuntu1~breezy1); however:
  Version of totem-xine on system is 1.2.0-0ubuntu3.
dpkg: error processing totem-xine-firefox-plugin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 totem-xine-firefox-plugin[/COLOR]


I have an AMD64, but i installed the Ubuntu for PC since it's better, so i'm guess i use the i386 version.

---

