---
title: "weird colors when trying to play DVDs"
date: 2007-11-07
forum: Apple PPC Users
---

### Post by gfxdom on 2007-11-07
I was just wondering if anyone knew what the cause of this could be, and how I can fix it.
I have done all of the stuff to play restricted formats, but whenever I put in a DVD and open it with any of the programs this is what happens,
[http://s234.photobucket.com/albums/ee26/GFxDomination/?action=view&current=Screenshot-1.png](http://s234.photobucket.com/albums/ee26/GFxDomination/?action=view&current=Screenshot-1.png)
Im using 7.04 on a G4 tower, and the graphics card is an ATI Rage 128 pro

---

### Post by seatea on 2007-11-07
I have had the same problem occur on my PM G4 with the same graphics card. My understanding is that Xv, part of xine, is buggy for this graphics card. I got around this occurrence by selecting the XShm option in video in the multimedia preferences of gnome. XShm is allegedly not as good as Xv, but I couldn't figure out any other solution. Maybe someone else has a better solution?

---

### Post by gfxdom on 2007-11-07
thanks man but since I'm a noob do you think you could explain how to do that please?

---

### Post by gfxdom on 2007-11-09
Sorry for the double post, but I just got flash working and now all thats left is to get DVDs working, so if someone can please explain what seatea said to do that would be awesome.
Thanks in advance

---

### Post by seatea on 2007-11-09
Under System or Desktop at the  top of your gnome screen, navigate to Preferences then to Multimedia Systems Selector. Under video, select the X Window System(no Xv) Default Output Plugin from the dropdown menu located there. Also, you may have to add a line to your xorg.conf like the one mentioned in the xine faqs. 

[http://xinehq.de/index.php/faq#NOVIDEO](http://xinehq.de/index.php/faq#NOVIDEO)

[I]I only see a blue (or green or black) video image most of the time.

You are either watching a very boring video (just kidding) or you are suffering from a bug in the Xorg 6.7 implementation of X11.

The workaround is to add the line

   Option "XaaNoOffscreenPixmaps"

in the Device section of your X server configuration (usually /etc/X11/xorg.conf or /etc/X11/XF86Config).[/I]

You may have to restart X windows to make everything work after making the changes.

---

### Post by gfxdom on 2007-11-09
Ok so the reason I couldn't figure out what you were saying before is because the Multimedia Systems Selector wasn't on my menu so I had to go in and add it. Now that I did the first part of what you said I went in to the filesystem and opened up the file you said but after I added the line it won't let me save???
EDIT: Ok i edited the file and rebooted but still nothing :( :(

---

### Post by seatea on 2007-11-10
You added  Option "XaaNoOffscreenPixmaps" to your  xorg.conf flie under devices and  selected XShm to the Multimedia System selector? Ok, are you using xine as your video player? I haven't been using Totem for a while as I kept getting  into problems with it that  I could not straighten out. I did get xine  to work. I think I did switch to the XShm driver in  the  xine setup as well. The xine gui can be added through synaptic. When you start it, go to setup>video and select XShm driver from the drop down menu. Then close xine and  restart it and try to play your DVD. I always thought there must be an easier way to get DVDs to play, but  couldn't find one. Make sure you have all the libraries for DVD play as outlined int the ubuntu guides too.

---

### Post by gfxdom on 2007-11-10
Thanks for all your help man I did everything you said to do, but I noticed that when I switched to XShm it makes the video's I stream from my sever skip and just play like crap. The DVDs still dont work so  I'm just gonna leave it for now and maybe try to get a new graphics card or something.
Once again thank you for all your help, you have helped me to understand alot more about ubuntu.

---

