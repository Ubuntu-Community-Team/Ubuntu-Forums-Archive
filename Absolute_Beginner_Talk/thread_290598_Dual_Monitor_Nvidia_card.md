---
title: "Dual Monitor Nvidia card"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by Fusspils on 2006-11-01
Hi

Just installed Ubuntu 6.10 on a system using a 7300GT card and I'm having trouble getting a dual monitor setup working.  I've installed the geforce driver using automatix2.  I have checked out lots of "google" results but they all seem to say different things.  Any help would be great!

Fusspils

---

### Post by tronica on 2006-11-01
after you installed the nvidia drivers, you need to open up the xorg.conf

> sudo gedit /etc/X11/xorg.conf

then go down to the device section, and make sure the driver is nvidia, and not nv. Then at the bottom of that section you need to add 

> Option    "twinview"

should look like this

> Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"twinview"

then save and restart X by dong control+alt+backspace

---

### Post by Fusspils on 2006-11-01
Thanks alot Tronica, it was really that simple!
Next question ](*,)  I have one monitor above the other, is it possible to change the "left to right" config to a "Up down" view?

---

### Post by Beaucephus on 2006-11-01
Yes.  There is an option for configuring orientation of the second monitor in relation to the first. In your case you want this option  in your xorg.conf file.

> "TwinViewOrientation"	"Above"

The default orientation is with the second monitor to the right of the first.  

"Above"

I found this and other options/descriptions here
[http://wiki.arslinux.com/Twinview]("http://wiki.arslinux.com/Twinview")

---

### Post by tronica on 2006-11-01
i wasn't really to sure on this one, so i searched the forums and found this

>  The "RightOf" part can be changed to "LeftOf", "Above", or "Below"

so that should answer your question.

---

### Post by bodhi.zazen on 2006-11-01
> **Beaucephus said:**
> I found this and other options/descriptions here
[http://wiki.arslinux.com/Twinview]("http://wiki.arslinux.com/Twinview")

Nice link. Thank you.

---

### Post by Johnathon on 2006-11-02
A quick question: does twinview allow you to maximise windows on one screen or the other, without the window filling both monitors?

I'm currently running two instances of gnome, but I really want something like the Windows way of doing dual monitors - I want to be able to maximise windows on either monitor, with it filling that monitor, but still be able to drag programs/windows from monitor to monitor.

If not, is there a way of doing it?

Thanks,

Johnathon

---

### Post by Beaucephus on 2006-11-02
Yes.  You can maximize to just one monitor.  To move from one monitor to the other, just minimize the window, drag it to the other side and maximize in new monitor.  Twinview has been exceptionally easy and awesome.  A $20 garage sale monitor has made my setup much more robust.

---

### Post by civilian on 2006-11-20
Yeah really I use my laptop at home on my lcd and the laptop display is the second screen its awesome.

---

