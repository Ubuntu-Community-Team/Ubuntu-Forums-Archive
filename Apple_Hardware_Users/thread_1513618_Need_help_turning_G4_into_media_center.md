---
title: "Need help turning G4 into media center"
date: 2010-06-19
forum: Apple Hardware Users
---

### Post by tsunamikitsune on 2010-06-19
A few weeks ago, my friends and I went to a local university surplus and bought a ton of Apple computers. Unfortunately, all of them are Power PC Macs, which I've learned after spending a few frustrating weeks with them, seem pretty useless in comparison to Intel-based Macs. Luckily, most of them are iMac G4s, so they have the cool flowerpot design that almost makes them worth having. Almost.

I tried OS X and I hated it. Soon after installing it, I hit the internet and tried to find an alternative. It made me happy to find that Ubuntu was still community supported on PPC Macs and I quickly installed it. It's nice to use Ubuntu on the iMac, but I haven't the slightest clue how to set it up properly. Things were straightforward enough for me to easily get a Ubuntu install running smoothly on my PC, but that was a while ago. Now I'm working with this PPC nonsense and it seems more difficult for whatever reason.

So anyway, I'd appreciate some help on a few things. I hope to primarily use this Mac as something of a media center at my bedside, with the ability to play music and movies over my network. It has a wireless card that's was able to connect to my network and access my files from my Windows PC, but at this exact moment it doesn't seem to be working correctly. If possible, I'd like the Mac to mount my Windows drive automatically on startup, since most (if not all) my media will be streamed this way and it would be nice to have it ready to go right away.

After the filesharing issue, there's yet another problem. Codecs: Where do I get them? I haven't gotten anything to play on my Mac yet. I remember having to use the repositories to find them, but I don't think my repositories are setup correctly or something because I'm having no luck.

The next issue I need to tackle is one I'm not sure can be helped, but I figure it's worth a shot. It's inconvenient for me to have a full keyboard and mouse with the Mac next to my bed, so I thought of an alternative. I own an Android phone (Motorola Droid) that has an app called Gmote, which lets me control my computer with my phone. I can browse files and start them remotely via wi-fi and use media controls with them. The big draw, however, is the ability to use my phone as a mouse/keyboard. I managed to get the program for it running on the Mac end, but I get an error when I start it:

```
There was an error running the gmote server. Please visit http:/www.gmote.org/faq for mote information
jnidispatch (/com/sun/jna/linux-ppc/libjnidispatch.so) not found in resource path

```

The only thing I've really been able to determine with this is that I think it's some kind of error that's caused by the Mac running OpenJava and not official Java. Any thoughts on this issue and how it might be fixed?

Finally, I read about something called [Mac-On-Linux]("http://mac-on-linux.sourceforge.net/") that will allow me to run OS X virtually under Linux at almost native speeds. Is this something worth looking into or should I just dual boot? It would be nice to run OS X in a window for the very few situations I need it rather than have to restart the computer to get to it.

I'm having a lot of frustrations with this computer, but hopefully I can find some help on here. I'd love to get some use out of the thing so it isn't just sitting there, collecting dust. Thanks in advance.

---

### Post by tsunamikitsune on 2010-06-20
Desperate bump?

I'm not expecting every one of my problems to be fixed, but if someone could please give me any advice that would make this thing moderately useful, I would sincerely appreciate it.

---

### Post by linuxopjemac on 2010-06-21
I can give you some reading material, to help you along:
[http://mac.linux.be/content/apple-powerpc-wiki](http://mac.linux.be/content/apple-powerpc-wiki)

---

### Post by vincentieo on 2010-07-13
Hello, I am currently on a very similar project with a ppc G4 (not imac) and was really excited when i easily got gomte to work on my intel macbook but ran into the same error message installing the linux server.

Did you make any head way on any of your problems?

I will keep you posted if i do.

---

### Post by vincentieo on 2010-07-13
I cant even get my android (htc desire) to mount with usb!? really frustrated now, I dont want to get rid of the old gal because there is still alot of useful functionality but i am slowly going mad.

---

### Post by svtguy88 on 2010-07-13
I can't really comment on the Android issues, as I don't had a droid phone (though my HTC Diamond can sort of run it...).  However, as far as codecs, when you open a movie file, the Movie Player should yell at you for not having them, and then direct you to install them from the box that pops up.  If it doesn't auto-prompt you, go to Synaptic Packager Manager and search for gst-plugins (I believe that's the name.  I'm on my OS X install right now, so I can't really look).  

Something else you may want to look into, is Xbox Media Center (XBMC).  I'm not sure how to get ubuntu to auto-mount your networked Windows drive, but I know that once you configure XBMC (i.e. tell it where your drive that you want to mount is), it will mount it automatically when you click on "Movies" or whatever the folder/drive name is.  

I haven't used XBMC on a computer much, but I know that it can make an old school Xbox a media beast once it's configured.  There's two in my living room.

Oh, you could also check out Mythbuntu.  I don't think they make a full PPC live-CD of it, buy you should be able to fine it in Synaptic and install...pretty sure there is a PPC build in the repositories.  Again, I don't have a whole lot of experience with it, but I've heard good things.

---

### Post by barbaGNU on 2010-07-13
> **tsunamikitsune said:**
> 
I'm having a lot of frustrations with this computer, but hopefully I can find some help on here. I'd love to get some use out of the thing so it isn't just sitting there, collecting dust. Thanks in advance.

they are nice machines but you must have a good linux skill and quite good powerpc knowledge.

After you tuned your machine you can build by yourself an application like typhon:
[http://www.frostworx.de/?p=1](http://www.frostworx.de/?p=1)
to build a personalized media center.

---

