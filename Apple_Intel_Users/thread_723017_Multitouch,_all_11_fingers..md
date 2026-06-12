---
title: "Multitouch, all 11 fingers."
date: 2008-03-13
forum: Apple Intel Users
---

### Post by tannewt on 2008-03-13
As I've posted before I own a new MacBook Pro.  Over the last few weeks I've begun to delve into the workings of the multitouch pad.  At this point I've gotten it to give me data via a python usb program and can understand the coordinates, velocity and area of each finger.  So far I've managed to view 11 fingers concurrently.  In the next few days I'll be releasing all of my code and data for further analysis.  I only understand 10 of 28 bytes per finger and none of the 26 extra bytes so there is more to find.

Also, I've never written a kernel driver before and am still pondering what the best way to do X integration would be.

Anyhow, I just thought I'd share the good news.

---

### Post by cassowary on 2008-03-13
Oh that's excellent news! A new MacBook Pro looks like it's the computer that best fulfills my needs, but I can't buy one if the trackpad won't work on Linux. Well done indeed.

---

### Post by tannewt on 2008-03-13
Well, it works out of the box but doesn't do anything fancy.  No clicking, no multifingers.  Just movement.

---

### Post by cyberdork33 on 2008-03-13
I would post findings on the mactel-linux mailing list. They create the appletouch (mactel) patches there. Once the kernel driver can send the needed information, then synaptic (xorg driver) can be modified to do something with that info.
[http://www.mactel-linux.org/wiki/Main_Page](http://www.mactel-linux.org/wiki/Main_Page)

---

### Post by cassowary on 2008-03-14
> **tannewt said:**
> Well, it works out of the box but doesn't do anything fancy.  No clicking, no multifingers.  Just movement.

With only a single mouse button, not supporting multifingered taps for second and third button clicks is pretty much the same as not working at all. (Supporting scrolling is a luxury; I'd cope without &mdash;* in fact, my desktop mouse has no scrollwheel at all, being ancient)

* Online forums with their own unnecessarily incompatible markup languages annoy me. Does anyone know how I can do what I obviously want to do?

---

### Post by tannewt on 2008-03-15
I've posted my findings at [tannewt.org/touch]("http://tannewt.org/touch").

---

### Post by cyberdork33 on 2008-03-16
please join the mactel-linux mailing list. I am sure they will find this data very interesting.

---

### Post by tannewt on 2008-03-31
Just thought I'd let you all know I've got it working.  I can now control the mouse, keyboard and button through my touchd.  So far I've added one finger moving and two finger scrolling.  I'll post the code soon along with a video.

Anyone have any ideas for gestures?

---

### Post by cyberdork33 on 2008-04-01
> **tannewt said:**
> Anyone have any ideas for gestures?

I would work on similar gestures to OSX as many users expect things to operate equivalently in Ubuntu.

Also, once you get to a stable release, can you upload the package to the mactel-support PPA on launchpad? I will gladly approve your membership request.

---

### Post by tannewt on 2008-04-01
cyberdork33, yeah, thats what I've been working off.  However, some of the gestures like pinch and pull don't work very well with the smaller touchpad.  I wish there were others who had it going and could come up with ideas.

Thanks.

---

### Post by mrsteveman1 on 2008-04-02
You have 11 fingers?

---

### Post by tannewt on 2008-04-02
I have friends.  :)

---

### Post by cyberdork33 on 2008-04-02
> **tannewt said:**
> I have friends.  :)
Excellent videos and research by the way. I took the time to check it out last night. Way to go!

You ought to start a team in launchpad and put your code into Bazaar or something so that people can see it easier / help hack on it.

---

### Post by Chrisj303 on 2008-04-03
Nice work mate!

---

### Post by mr.loco on 2008-04-05
I have a sick mind... i lolled hard at "11 fingers"

---

### Post by mrsteveman1 on 2008-04-05
I pictured either a guy with 11 fingers, or one of those college type "lets see how many people fit in a phone booth" games. how many fingers on one touch pad? the world may never know...

---

