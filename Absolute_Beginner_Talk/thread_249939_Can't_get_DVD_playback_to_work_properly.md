---
title: "Can't get DVD playback to work properly"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by n00b@linux on 2006-09-03
I've just installed Kubuntu 6.06.1 and put in a BBC DVD of Tinker, Tailor, Soldier, Spy ("TTSS").  I've had this DVD for a few years but this is the first time I've tried to play in on the DVD-ROM in my IBM Thinkpad T40p.

I have only tried playing it in Kaffeine.  The bizarre thing is that it plays the BBC marketing-type intro well, but then it stops once this is finished.  I don't get any menus and it doesn't start playing TTSS proper.

Can someone please help me?  I think it might be an encryption thing but I really have no idea when it comes to multimedia.:confused:

---

### Post by steve.horsley on 2006-09-03
You probably need to install libdvdcss2, which gives you the ability to view scrambled DVDs. This isn't included in the Ubuntu distro because the pea-brains that make DVDs seem to think that watching DVDs on Linux is somehow bad.

Edit the file /etc/apt/sources.lst by using this command:
**gksudo gedit /etc/apt/sources.lst**
and add these two lines at the end of the file:
> ## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free

Then update to learn the new packages available:
**sudo apt-get update**
and install the package:
**sudo apt-get install libdvdcss2**
Now you can watch DVDs as nature intended.

---

### Post by sandyjo on 2008-01-13
I have got the same symptoms, I get the bbc intro, but then no menu and no film. I have been trying to sort this for a few days now and have installed about 20 different codecs and have got both libdvdcss2 and libdvdread3 installed using Synaptic but I STILL CANT WATCH BBC DVD's.  Please help I am going mad.

---

### Post by ubu-for on 2008-01-13
> **sandyjo said:**
> I have been trying to sort this for a few days now and have installed about 20 different codecs and have got both libdvdcss2 and libdvdread3 installed using Synaptic but I STILL CANT WATCH BBC DVD's.

Try VLC, Ogle or Totem-Xine instead.

---

