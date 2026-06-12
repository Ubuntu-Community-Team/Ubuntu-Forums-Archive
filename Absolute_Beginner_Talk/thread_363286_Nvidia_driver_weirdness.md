---
title: "Nvidia driver weirdness"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Muppeteer on 2007-02-16
A while back when i upgraded my gfx card from an x800 to a nvidia 7800gtx, i installed the drivers and everything was fine. One problem though. The other day i installed Beryl and it put different drivers on. 

When i ran glxgears on the previous drivers i was getting 14k and WoW was playable. Now i get about 9k in glxgears and WoW is awful. I can't remember which drivers i used first, but the nvidia splash screen was white and now it is grey. That is all i remember...I can remember the install process wasn't very hard...

Anybody have any idea which drivers i'm referring to? 

At the minute Synaptic shows i have nvidia-kernel-common installed...

Thanks in advance :)

---

### Post by taurus on 2007-02-16
I believe the white background is a legacy driver while the gray or darker background is the latest version of nVidia driver.

---

### Post by Tomosaur on 2007-02-16
You may want to give the official nvidia linux drivers a go, I got a great performance increase from them. They're available from the nvidia website. The open source nvidia drivers just don't cut it at the moment for me, games just refuse to run at an acceptable rate with them for me.

---

### Post by Muppeteer on 2007-02-16
Hmmmm....that's weird, why would a legacy driver work better than the official one?

I believe i am using the official one, 1.0-9746...

How could i get the legacy driver back to do a comparison? :confused:

---

### Post by taurus on 2007-02-16
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by Muppeteer on 2007-02-16
Thanks man! :)

---

### Post by Muppeteer on 2007-02-16
Ok, well i figured out the problem...Beryl...

When i have it set as the window manager it hogs a helluva lot of cycles on the gfx card...:(

---

### Post by Maestro23 on 2007-02-16
.

---

