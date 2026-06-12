---
title: "Issues with 15.10 on Mac Mini"
date: 2015-12-08
forum: Apple Hardware Users
---

### Post by lordy2 on 2015-12-08
Hi guys,
I managed to install ubuntu mate 15.10 via USB (not sure if it fully compeleted) but the livecd always reloads on reboot
when I unplug my USB stick I just get the mac folder with a question mark

does anyone know what to change the open firmware to boot linux hd first?
I used "setenv" to change my boot-device to USB. right now it's set to
[COLOR=#808080]usb0/disk@1:2,\install\yaboot[/COLOR]

it seems that the boot loader keeps on looking for this when USB is not present
[COLOR=#808080][FONT=Monaco]hd:,\\:tbxi
[/FONT][/COLOR]
I'm not sure if that's normal or due to Ubuntu not being fully installed
I had to reboot several times before ubuntu actually started installing, since the live desktop always hangs after a while
P.S.: I run a 2005 ppc mac mini G4 1,42Ghz

---

### Post by lordy2 on 2015-12-08
topic can be closed

15.10 doesn't run stable on my mini
live cd boots fine but freezes approx. 10 sec after ubuntu desktop is displayed
I guess I need more RAM to run this

P.S.: thanks for moving

---

### Post by Bucky Ball on 2015-12-08
Just thought I'd throw this in. Have you seen any of the [Mac images here]("http://cdimage.ubuntu.com/releases/14.04/release/")? Does your model need to use it? Although I'm not an expert, another user and I have been stumbling through this on another thread (different Mac) and I discovered the Mac images linked. Don't know if they'll make any diff.

You could have a bash (no pun) at installing the Mac server there and if that is successful and once you've logged in to the CLI on first boot proceed with:

```
sudo apt-get install ubuntu-desktop
```

Or a [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD")? That requires an ethernet cable, think server does, too.

---

### Post by Dsoslglece on 2015-12-09
Hi Lordy2,
You say that you unpluged the usb device… but did you just unplug it or did you first eject it? I'm sorry if the answer seems obvious to you, but when your car stops in the middle off a trip, first thing is to see if there is fuel… ;)
Second question: did you change in the system prefs the booting choice?
If when starting your system you see this « ? », just restart and keep pressing the "C" key, and then you'll be presented with the different booting systems present on your machine, just click then the one of your choice.
Hope it answers your question

---

