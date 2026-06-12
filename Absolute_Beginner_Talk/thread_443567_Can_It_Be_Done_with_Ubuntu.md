---
title: "Can It Be Done with Ubuntu?"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by watchmeunravel on 2007-05-14
Greetings all. This post comes from a poor college student who has decided that Linux might be able to help him out in this situation. I have used Linux sparingly over the past two years and recently installed Ubuntu desktop for a friend and he enjoys it already, so I figured I'd give it a shot for a server I'm working on. Here's the situation. I am moving into a house off-campus with five of my classmates next year. We all have computers with our own music and movie collections. Everyone else is running Windows XP and I have an iMac running OS X. We are also going six-way and pooling together to get a large TV for our living room. What I want to do is get some sort of front-end for the TV that can stream our music and movies. I do not want to centralize the process and have one server hosting all of the tunes and flicks, but rather, have all six computers retain the data separately. A nice front-end for the TV would be great, something reminiscent of AppleTV or Front Row perhaps. Is this possible with the abundance of Linux and Ubuntu software out there? Thanks!

---

### Post by cmost on 2007-05-14
Linux MCE.  Words cannot describe it.  Watch the demo video.  Here's the link:

[http://linuxmce.com/](http://linuxmce.com/)

---

### Post by Zuuswa on 2007-05-14
I havn't messed with it myself, but I think you are looking for a program called MythTV

..::edit::.. looks like i wasnt fast enough :p and sure enough linuxmce uses mythTV

---

### Post by 3rr0r on 2007-05-14
> **cmost said:**
> Linux MCE.  Words cannot describe it.  Watch the demo video.  Here's the link:

[http://linuxmce.com/](http://linuxmce.com/)

What kind of PC does he install it on.  It looks like some wierd rectangle box thats hooked up to his tv somehow???

---

### Post by Scunizi on 2007-05-14
since you don't want to centralize anything, look at VLC. It can be run on mac, windows and linux and will serve up video and audio.

---

### Post by cmost on 2007-05-14
"LinuxMCE is a free, open source add-on to Ubuntu including a 10' UI, complete whole-house media solution with pvr + distributed media, and the most advanced smarthome solution available. It is stable, easy to use, and requires no knowledge of Linux and only basic computer skills."

The video has been taken down for reworking, but, you can find others on YouTube.

Linux MCE is like MythTV but so much more!

---

### Post by newlinux on 2007-05-14
LinuxMCE and mythtv might be a little overkill for what you want to do. Maybe look into Elisa or Freevo. I don't think Mythtv does a good job of managing music and playlists. But really, you could just set up shares on all the computers and use just about anything you like. But for a slick interface I'd go with Elisa or Freevo in this case.

---

### Post by amoore on 2007-06-06
LinuxMCE is just super junk!!!!! Give elisa a try!! Elisa still has some bugs (its still in beta dev). Elisa should be out by July

Just setup your ~/.elisa/elisa.conf after you have run Elisa for the first time make sure that you close Elisa using the "Q" key the first time you run Elisa so that the ~/.elisa/elisa.conf is generated.

```
gedit ~/.elisa/elisa.conf
``` to put in the sources for each computer or location of files and folders.

Elisa does work with lirc to so its not that hard to set up a remote too!

---

