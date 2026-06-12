---
title: "Proper keyboard backlight support available (i.e. no pommed, yay!)"
date: 2011-02-24
forum: Apple Hardware Users
---

### Post by alexmurray on 2011-02-24
If anyone is interested I've finished integrating proper keyboard backlight support into gnome-power-manager (which in turn uses upower to actually control the keyboard backlight) which with any luck will be [available in Natty out of the box]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/724324"). 

[A similar patch]("https://mail.gnome.org/archives/gnome-power-manager-list/2011-February/msg00017.html") should also land upstream too so Fedora etc should get it for free too in their next release too.

In essence this allows us to provide the user with greater feedback and control than say just using pommed (ie. we can dim the keyboard on idle like the lcd display etc, and can display nice notifications of the keyboard backlight level too - see attached screenshot).

If anyone is interested in testing this out, you can use the [packages in my ppa]("https://launchpad.net/~alexmurray/+archive/ppa") and let me know how it works out for you.

---

### Post by _mario_ on 2011-02-25
Hi,

thanks for your work. According to a first test, it works fine. However, I'd like to mention some notes:

[LIST=1]
[*] When running fullscreen applications (e.g., XBMC, World of Goo), that grab input, it is not possible to change the backlight (screen **and** keyboard) anymore. With pommed running, it worked, because pommed responded to input events beneath the X subsystem.
[*] This also means, that with pommed running, there previously where two applications pommed **and** gnome-power-manager, that changed **screen** backlight. A problem, that's now solved without pommed.
[*] According to some other thread, users preferring the fnmode=2 keyboard option, will loose this setting after resuming from suspend, because apparently the module doesn't save it. Pommed could restore this option.
[/LIST]

Hence, it's not that simple to abandon pommed completely, but it's a major step forward.

BTW: Does this also work with other desktop environments (KDE, XFCE), that don't use gnome-power-manager?

ciao,
Mario

---

### Post by linuxopjemac on 2011-02-25
Well done Alex. Will it also work in 10.04 ?

---

### Post by _mario_ on 2011-02-25
Hi,

and some additional minor note: Is it possible to change the implementation to not repeatedly set backlight/send dbus notifications if keyboard brightness is already off/maximum but the user still presses the decrease/increase key? Screen backlight works like this.

ciao,
Mario

---

### Post by alexmurray on 2011-02-25
> **linuxopjemac said:**
> Well done Alex. Will it also work in 10.04 ?
Probably not unless someone feels like trying to port my patches to the older version of upower and gnome-power-manager which 10.04 uses.

---

### Post by alexmurray on 2011-02-25
> **_mario_ said:**
> 
BTW: Does this also work with other desktop environments (KDE, XFCE), that don't use gnome-power-manager?

If KDE / XFCE add support for controlling the KbdBacklight interface over dbus (via upower) then it will work just as it does now for g-p-m since I've added that support to it.

---

### Post by alexmurray on 2011-02-25
> **_mario_ said:**
> 
and some additional minor note: Is it possible to change the implementation to not repeatedly set backlight/send dbus notifications if keyboard brightness is already off/maximum but the user still presses the decrease/increase key? Screen backlight works like this.

This should be quite do-able, will see what I can come up with.

---

### Post by alexmurray on 2011-02-27
[Upstream has accepted the updated patch]("http://git.gnome.org/browse/gnome-power-manager/commit/?id=7e5fedb32bfb9dc6428c5b0eb21ef48a27602a27") so g-p-m 3.0 will support keyboard backlights out-of-the-box. Unfortunately Natty is stil shipping g-p-m 2.32 so I've just [filed an FFE for Natty]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/724324") to merge this patch in so hopefully we'll get out-of-the-box support in Natty too.

---

### Post by siwelchungster on 2011-04-05
I read through the various links. Is this feature supposed to be available in natty now?

I have a samsung laptop with the option to increase/decrease the backlighting on the keyboard with fn + F7/F8, but it doesn't seem to be working on Natty Beta 1.

---

### Post by alexmurray on 2011-04-05
Yes natty has all this now - you also need kernel support for this - either via ACPI events or a driver which provides a /sys/class/leds/xxx::kbd_backlight interface - so I assume a particular driver will be needed in the kernel to actually set the backlight itself - what is your laptop model?

---

### Post by siwelchungster on 2011-04-05
It's the Samsung 900x3a, or Samsung 9 series laptop. I must say that besides the backlight issue, it's been a VERY pleasant ubuntu experience and I'm glad that you've put in the work to get keyboard backlighting toggles working.

I looked into /sys/class/leds and theres nothing there - is that the correct place to look?

Thanks a bunch beforehand.

---

### Post by joskapista on 2011-05-23
Thanks, it works great! The only thing what I miss the automatic light turn off function, because it never stops to light, even though I don't use the keyboard. So that's why I installed pommed, but It isn't so good like with Maverick (maybe because this built in support).

---

### Post by heavisidee on 2012-01-05
Is the solution still working under 11.10, especially with the Samsung 900 Series?

I couldn't figure it out. Thx!

---

