---
title: "Opening mounted drives / Change DVD Region"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by arqbrulo on 2007-12-13
I've really tried looking all over the internet and these forums but have not found anything (maybe I did not look hard enough, but I've been trying for hours). Every time I insert my usb device (flash/HDD) it automatically mounts them and then opens the drives. I don't want the drives to open by themselves. How can I prevent that?

Also, is there a way to change the DVD region of my DVD drive? I know there's a way to do it in windows. Or, if I do it inside windows, will the change be automatic inside ubuntu? Thanks to all.

---

### Post by zcal on 2007-12-13
Go to your Mountable/External Media (argh, can't remember what it's called in English) in the preferences menu.  You can change the setting to not open external drives automatically when they're mounted.

As for your DVD drive's region...

apt-get install regionset

But be CAREFUL!  You can usually only change a drive's region a few times before it locks you out of doing it again.  [read this]("http://linvdr.org/projects/regionset/")

---

### Post by arqbrulo on 2007-12-13
That simple? Hmmm.
Regarding the region code, I'm aware of that, it's just that I live in Mexico and all of my DVD players are region 1. Every now and then I would like to see a region 4 DVD, so I'm going to change the code on my laptop to be able to see region 4 (just a one time change).

Thanks for your help.

---

### Post by arqbrulo on 2007-12-13
You know, after right-clicking=>properties AND opening my device=>edit=>preferences I did not find anything about not opening external drives automatically. Is there another way?

---

### Post by zcal on 2007-12-13
> **arqbrulo said:**
> That simple? Hmmm.
Regarding the region code, I'm aware of that, it's just that I live in Mexico and all of my DVD players are region 1. Every now and then I would like to see a region 4 DVD, so I'm going to change the code on my laptop to be able to see region 4 (just a one time change).

Regardless of the drive's setting, libdvdcss2 should be able to play any DVD.  [Check it out.]("http://www.videolan.org/developers/libdvdcss.html")

> You know, after right-clicking=>properties AND opening my device=>edit=>preferences I did not find anything about not opening external drives automatically. Is there another way?

You're looking in the wrong place.  You need to go to the Preferences menu under the System button on your "start" bar.  It's up in the left hand corner of your screen on the panel, unless you moved things around (right next to Programs and Places).  Click on Removable Media (I think that's what it's called) and uncheck the box for the option to show the contents of external drives when they're mounted.

---

### Post by arqbrulo on 2007-12-17
Thanks for your help. I WAS looking in the wrong place. I managed to figure it out. Thanks.

---

