---
title: "Start-up Failure"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by Kid G on 2006-01-30
Hi,

My computer is freezing during startup, specifically at: *Checking Battery state [ok]*

I was using the outside-of-GUI command prompt following instructions from the  installing latest Nvidia drivers how-to and entered my password incorrectly a few times (num lock off - keep forgetting that!). I was unable to exit this screen so I turned off my PC by the power button. Now when I attempt to boot Ubuntu I get the above problem.

I dont know If the the two are related but I would appreciate some help.

Thanks

---

### Post by ecto on 2006-01-30
This is sort of a hunch but perhaps your BIOS battery is dead? Try that. Sorry if it doesnt help though. What you can do is try loading the boot cd. If the time is out of sync that means your battery is probably dead.

---

### Post by Kid G on 2006-01-30
I'm dual-booting and the Windows XP Os loads ok :confused:

---

### Post by benplaut on 2006-01-30
try pressing Ctrl+C when it hangs, report back on what happens

---

### Post by Kid G on 2006-01-30
Ok this time when I tried to boot up I didnt get as far as the above problem - after the Ubuntu Logo loading screen I went to a GUI-less command prompt:

 *Ubuntu 5.10 "Breezy Badger" Ubuntu tty1*

I was prompted for my username and password but only got the user@ubuntu prompt - I'm really stuck now :(

---

### Post by benplaut on 2006-01-30
once you're at the prompt, type these two commands (write them down)

sudo killall gdm
sudo gdm

and tell us what happens :)

---

### Post by Kid G on 2006-01-31
My X graphical server was not configured correctly. I restored the backup I made of 
* /etc/X11/xorg.conf* when I was attempting to install my Nvidia driver and everything seems to be ok again - I think!

Thanks

---

