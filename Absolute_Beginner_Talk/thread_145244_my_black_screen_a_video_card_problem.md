---
title: "my black screen: a video card problem?"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by must_golf_more on 2006-03-15
Hi all--I spent a good 5 hrs so far trying to rebuild my old box that used to run WinNT, but I'm having problems. (I encountered the same issue after trying to install both ubuntu 5.10 and kubuntu 5.10 from CDs.) Here's what happens:

After a smooth install, the system does it's final reboot. Eventually, I get to the dark loading screen where it shows "ubuntu" in cool graphics, and at the bottom I see stuff like "Loading modules.... ok". After a bunch of stuff seems to load without issue, my screen eventually turns completely black. No cursor...nothing.

I tried researching my issue in the forums, and eventually learned how to boot via recovery mode with the [Esc] key. Since I suspected my video card config might be the cultprit, I tried mucking with my settings using: sudo dpkg-reconfigure xserver-xorg

Unfortunately, I couldn't find much info for my stinkin card (Creative Labs Graphics Blaster MA202) on the internet, so I wasn't sure which values to choose. Some postings suggested to try "ati" or "vesa". Did that--neither worked.

I'm now kinda stuck, so I'm desperately seeking advice on what to try next. I'm fairly good with vi and shell scripting, but pretty clueless about real system administration. :cry: 

I understand that you forum vets aren't going to babysit a noob like me, but I would be most grateful if you could help me get pointed in the right direction.

Thanks in advance!

---

### Post by dickohead on 2006-03-15
Try changing the driver in your /etc/X11/xorg.conf from X to : vesa. So if your graphics card driver currently says: nv or nvidia or creative or whatever, change that value to vesa, then retry, failing that, browse through the file and try changing some resolution options, ie: set the default colour depth to 16bit and the resolution to 1024x768 or something safe for your monitor, 800x600 should work on anything from the last 10-15 years.

---

### Post by must_golf_more on 2006-03-15
Thanks for the quick response. I tried the "vesa" setting, and picked the resolution at 800x600, and color depth at 4. Now, when the system tries to boot up, it stops with a blinking cursor after this:
* Checking battery state... [ ok

---

### Post by must_golf_more on 2006-03-15
Not sure if this is relevant, but I also checked out my syslog, and here's what I saw:

localhost kdm: :0[6411]: IO Error in XOpenDisplay
localhost kdm[6393]: X server for display :0 terminated unexpectedly
localhost kdm[6393]: Display :0 cannot be opened
localhost kdm[6393]: Unable to fire up local display :0; disabling.

---

### Post by must_golf_more on 2006-03-16
YEAAAHHOOOO! I didn't think of this earlier because I'm a ding dong:

I simply removed the video card, and used the mobo's COM1 port! Voila--I now see the login screen! It's horrible resolution, but at least I see somethin!

---

### Post by Brunellus on 2006-03-16
[QUOTE=must_golf_more]YEAAAHHOOOO! I didn't think of this earlier because I'm a ding dong:

I simply removed the video card, and used the mobo's COM1 port! Voila--I now see the login screen! It's horrible resolution, but at least I see somethin![/QUOTE]
that's AMAZING.  I have never heard of such a thing.

---

### Post by Gorgazm on 2006-04-28
so boot through com1 port instead of card for display? (im pretty sure I can still get my 2000somethingx1000 something display rate through that, it'd just be a bit slower)

---

