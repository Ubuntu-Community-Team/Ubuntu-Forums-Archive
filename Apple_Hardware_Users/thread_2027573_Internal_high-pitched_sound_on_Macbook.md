---
title: "Internal high-pitched sound on Macbook"
date: 2012-07-16
forum: Apple Hardware Users
---

### Post by dingenis on 2012-07-16
I have a MacBook 2.1 with a fresh Ubuntu 12.04 64bit. There is a weird high-pitched sound coming from inside, somewehere located below the middle-left of the keyboard. It's always there, unless the CPU is working, after that then the sound comes back immediately.

I tried installing Ubuntu 8 on the same MacBook a couple of years ago, but I removed it again because it also had this sound. I'd almost think it's a hardware issue, were it not that osx works fine; without the sound.

I'm pretty sure it does not come from the speakers (the speaker/ headphone sound works fine, and the sound is not on the headphone). 

Does anyone know what it could be? Apart from being annoying, is it harmful? Thanks in advance!

---

### Post by |{urse on 2012-07-16
My guess is it's a squealing capacitor by the gpu. You're gonna want to talk to Apple about that. This is a fairly well known issue and the capacitors typically settle down.

Increase the brightness on your display and tell me if the squealing gets louder or not, please.

---

### Post by piwacet on 2012-07-17
This is a well known problem with macbook 2,1.  I have one of these laptops as well.  The cpu enters a certain c-state and then it makes the high pitched noise.  If I remember right it's a hardware bug.  The solution is to prevent the cpu from entering this c-state.  Going into this c-state is supposed to be an energy saving thing, but the last time I looked into this (a long time ago), making this change didn't really cause any problems.

In a terminal:
```
sudo su
nano -w /etc/default/grub

```Change the line in this file that reads like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```to:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash processor.max_cstate=2"
```Save file (ctrl-x)
execute:
```
update-grub

```Then exit the terminal and reboot.

---

### Post by dingenis on 2012-07-17
Piwacet, you were absolutely right about the c-state, it works in one go.

To answer |{urse's question: increasing or decreasing the brightness did not change the sound, apart from the fact that the sound pauses for a second just to think about it.

Both of you, thanks a lot for the quick reply! You saved me from switching back to osx in fear of an explosion or something...

---

### Post by animalk on 2012-07-23
> **piwacet said:**
> This is a well known problem with macbook 2,1.  I have one of these laptops as well.  The cpu enters a certain c-state and then it makes the high pitched noise.  If I remember right it's a hardware bug.  The solution is to prevent the cpu from entering this c-state.  Going into this c-state is supposed to be an energy saving thing, but the last time I looked into this (a long time ago), making this change didn't really cause any problems.

In a terminal:
```
sudo su
nano -w /etc/default/grub

```Change the line in this file that reads like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```to:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash processor.max_cstate=2"
```Save file (ctrl-x)
execute:
```
update-grub

```Then exit the terminal and reboot.

Thank you piwacet!

---

