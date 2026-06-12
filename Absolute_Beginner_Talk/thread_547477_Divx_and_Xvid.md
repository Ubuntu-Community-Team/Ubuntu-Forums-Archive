---
title: "Divx and Xvid"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by comradexiactura on 2007-09-10
I have been trying to figure out how to install a codec for divx, but have not been able to find one. I read that you can install VLC  and that should be able to play it but i was wonder if there was a codec so that i could just use totem or realplayer. All help is appreciated, thank you in advance.

---

### Post by funpop on 2007-09-10
you need the w32codecs,
get em from medibuntu
[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

or simply download the deb:

[http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20061022-0medibuntu1+build1_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20061022-0medibuntu1+build1_i386.deb)
and install:

sudo dpkg -i w32codecs_20061022-0medibuntu1+build1_i386.deb

"It is your legal responsibility to make sure that the software you are installing can be legally used in your country and for your intended purpose" #-o

---

### Post by nickpaton on 2007-09-10
I use VLC with no problems and installed via Synaptic.

There are a number of plug in options too which I have installed but don't know how relevant they are to playing Divx:

vlc-nox
Also grap all the vlc-plugin-xyz (there's a few of them)

Why I like vlc is that it has stuff like deinterlacing for improving the picture and the like, however you may find that it takes a few seconds for the picture to settle down when you initially select a deinterlace category.

---

### Post by comradexiactura on 2007-09-10
ok so this is what im getting:
   tony@tony-laptop:~$ sudo dpkg -i w32codecs_20061022-0medibuntu1+build1_i386.deb
Selecting previously deselected package w32codecs.
(Reading database ... 119068 files and directories currently installed.)
Unpacking w32codecs (from w32codecs_20061022-0medibuntu1+build1_i386.deb) ...
dpkg: dependency problems prevent configuration of w32codecs:
 w32codecs depends on libc6 (>= 2.5-0ubuntu1); however:
  Version of libc6 on system is 2.4-1ubuntu12.3.
dpkg: error processing w32codecs (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 w32codecs

Im guessing i need to upgrade that libc6?

---

### Post by BrendanM on 2007-09-10
Sounds like it. You can try "sudo apt-get upgrade" to get newer versions of all the packages installed on your system.

---

### Post by holydog on 2007-09-10
Why not use songbird? I've installed VLC but it seems a bit sad and plain. More like windows media player classic. It might be hard to install but i say its worth it. If you really need help in installing songbird then go here- [http://ubuntuforums.org/showthread.php?t=273162](http://ubuntuforums.org/showthread.php?t=273162) . Thx anyway aysiu!!! If it wasn't for the script then i would still ponder on how to install songbird!

---

### Post by nickpaton on 2007-09-10
> **holydog said:**
> Why not use songbird? I've installed VLC but it seems a bit sad and plain.

LOL Holydog - Surely you should be more interested in what you are watching on VLC than how it looks!!  I know what you mean and am going to have a look at Songbird myself

---

### Post by djchandler on 2007-09-10
But VLC plays just about anything you give it. 

Maybe it is time for a change.

Checked out Songbird. Looks like the next killer app from Mozilla. Going to wait for beta at least. I'm not much as a packager. That's too much like work.

I'll stay with VLC for now.

---

### Post by Perfect Storm on 2007-09-10
Even Chuck Norris uses VLC :guitar:


On a serious note, to turn down down VLC because of its looks is a bad idea. VLC look slick and light with the right theme.
[img]http://www.imageviper.com/displayimage/96862/0/VLC-short.png[/img]

Also it have 1000s of options that you can enable/disable.

---

### Post by holydog on 2007-09-10
Hey i pretty use it only cause it looks good. Anywayz. That looks like it came from a MAC. If its not then could you tell me where you downloaded the theme? Might install it.

---

### Post by nickpaton on 2007-09-10
Mmmm - Just installed Songbird and it seems to do different things to VLC.

I use VLC to watch DVD's and Songbird does not appear to pick up Video VOB files for instance (unless there are specific plugins for Songbird - & I do have all the necessary multimedia plugins available!)

Am I right in thinking that Sb is more a music management program? Certainly looks the biz.

Thanks for your comments HD but I think because of the flexibility and sheer amount of controls on VLC, I'll stick to it, but appreciate the heads up on what seems an excellent music management program.

---

### Post by koshari on 2007-09-10
given most people play movies in full screen mode its pretty much irellevent what the theme looks like anyway.

---

### Post by Hallvor on 2007-09-10
> **koshari said:**
> given most people play movies in full screen mode its pretty much irellevent what the theme looks like anyway.

+1. 

Yes, who cares? VLC`s ability to change the aspect ratio to perfect 16:9 saved my evening yesterday. :)

---

### Post by holydog on 2007-09-10
Hey its choice. Anywayz. I don't watch any videos from my computer. :P If i do then i just smack it into my USB then just play it on my HI-FI.

---

### Post by Rhubarb on 2007-09-10
To get codecs installed (so they work in totem), in the terminal type this in:
```
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```
This will allow you to play Xvid + DivX videos (and many many other video formats), for some other codecs (like WM10 I think), you'll need the medibuntu win32codecs package (or win64codecs if you're using 64bit ubuntu).

---

### Post by holydog on 2007-09-10
Thx. I really needed that codec. Now i just double click and just use totem in stead of right clicking.

---

