---
title: "[Need Help]Live Customized Lightweight Linux Environment[/Need Help]"
date: 2012-11-11
forum: Any Other OS
---

### Post by closed source on 2012-11-11
Salaam.

I hope you're all doing alright. I'll be straight forward with my concerns and questions.  
I'm looking to use a live lightweight linux environment that's bootable from cd, sd card, usb flash drive or external hdd. I'd like this live environment to be preconfigured for my machine(resolution/drivers/themes) with applications of my choosing  already installed(virtualbox etc). I was wondering if any of you wouldn't mind pointing me towards a decent lightweight linux distro, and maybe explain how I could go about customizing it for my needs before creating the live disc image. For the most part, I plan to use the live environment to launch virtual machines from an external hdd. 
All help is appreciated. 
Thank you. 
:guitar:

---

### Post by lykwydchykyn on 2012-11-11
Debian has a tool called "live-build" that works also in Ubuntu, which allows you to build a custom debian/ubuntu build for live booting.  It's command-line, but relatively simple for building a basic system.  If you can figure out using apt-get, you can probably figure out live-build.

A manual for live build can be found here:

[http://live.debian.net/manual-2.x/html/live-manual.en.html](http://live.debian.net/manual-2.x/html/live-manual.en.html)

It's in the repositories as "live-build".

---

### Post by closed source on 2012-11-12
> **lykwydchykyn said:**
> Debian has a tool called "live-build" that works also in Ubuntu, which allows you to build a custom debian/ubuntu build for live booting.  It's command-line, but relatively simple for building a basic system.  If you can figure out using apt-get, you can probably figure out live-build.

A manual for live build can be found here:

[http://live.debian.net/manual-2.x/html/live-manual.en.html](http://live.debian.net/manual-2.x/html/live-manual.en.html)

It's in the repositories as "live-build".

Thanks. Looks like just the tool I need. Do you have any recommendations for a lightweight linux distro? Or should I just build up my own lightweight system from a debian base?

---

### Post by mips on 2012-11-12
> **closed source said:**
> Thanks. Looks like just the tool I need. Do you have any recommendations for a lightweight linux distro? Or should I just build up my own lightweight system from a debian base?

Go have a look at crunchbang, should give you a decent base to build from.

---

### Post by lykwydchykyn on 2012-11-13
> **closed source said:**
> Thanks. Looks like just the tool I need. Do you have any recommendations for a lightweight linux distro? Or should I just build up my own lightweight system from a debian base?

The tool doesn't really allow you to start from an existing distro base; you start with a generic debian or ubuntu install, and build up from there.

It really depends on how much customization you want.  If you know what desktop you want, starting with a base like debian is the best approach.

---

### Post by Chdslv on 2012-11-13
> **closed source said:**
> Salaam.

I hope you're all doing alright. I'll be straight forward with my concerns and questions.  
I'm looking to use a live lightweight linux environment that's bootable from cd, sd card, usb flash drive or external hdd. I'd like this live environment to be preconfigured for my machine(resolution/drivers/themes) with applications of my choosing  already installed(virtualbox etc). I was wondering if any of you wouldn't mind pointing me towards a decent lightweight linux distro, and maybe explain how I could go about customizing it for my needs before creating the live disc image. For the most part, I plan to use the live environment to launch virtual machines from an external hdd. 
All help is appreciated. 
Thank you. 
:guitar:

Install Easypeasy 1.6 and you'd have your distro you can carry in your pocket. Very fast, faster than the newer distros.

---

