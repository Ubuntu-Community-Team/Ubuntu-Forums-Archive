---
title: "ubuntu 7.04 installation on dell inspiron 9400 [unique problem?]"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by TMulder on 2007-05-07
Hi,

First post, too bad i start with a problem.

I'm trying to install ubuntu on my Dell inspiron 9400 with ATI.
I'm not completely new to gnu/linux (this actually worked with ubuntu 6).
I searched the forums for help.

The problem is that when the system boots the screen stays black. So i press ctrl-alt-F1 to get the login prompt.
I login, then i do all kinds of stuff i read on this forum like:

sudo dpkg-reconfigure xserver-xorg (nearly all variations- VESA-VGA-ATI)
doesn't work, also automatic detection doesn't work.

Next step i think is to install fglrx right?.
So i did: sudo apt-get update

Well here is the 2nd problem. Networking doesn't work. Maybe it's my wireless... So i plug in a LAN cable and did:
REBOOT -> sudo dpkg-reconfigure dhcp3-client

still not working

then i tried: sudo /etc/init.d/networking restart - still not working

So i booted back into winXP(sigh) and my lan seemed to work fine.

I think i'm going to cry.. Please help me!

I think that when my networking... works- i can just follow instructions to install the fglrx drivers and everything will be fine.

---

### Post by TMulder on 2007-05-07
Do i need to supply more information?

I have a DELL Inspiron 9400
1GIG RAM
intel dual core
ATI Mobility Radeon X1400

intel pro wireless 3945 ABG network connection
broadcom 440x 10/100 integrated controller

---

### Post by Diversion on 2007-05-07
Looks to me that you're installation went wrong or something.
Tried reinstalling Ubuntu using another CD? Did you check the CD on errors before installing?
I also have an 3945 intel wireless adapter and it works out-of-the-box at my installation. It should also work out-of-the-box for you're installation

---

### Post by TMulder on 2007-05-07
Thanks for the quick reply!

I did check the cd image for errors.
I did not try to reinstall.

I forgot to mention that i used the alternate installer with wubi(the ubnuntu windows installer)
I know that isn't supported.

Maybe i should just burn the desktop cd en check if it will work that way, What do you think?

---

### Post by Diversion on 2007-05-07
it's worth the try if you've just installed Ubuntu. It doesn't take that long to reinstall it.
Using the desktop version here, installed it a bunch of times on my laptop without any problems.

Hope this helps.

---

### Post by TMulder on 2007-05-07
I'll try it some other way- never had a smooth gnu/linux install before. I'll get there.
My girlfriend is very angry now. (tonight.. linux is more important:) )

now i think of it...
They always warn that a linux install may require a couple of reboots to get everything working, but they never take into account the 'angry girlfriend factor' which really adds to the complexity.

---

### Post by TMulder on 2007-05-08
I did a re-install en everything is functioning now.
It turns out that if you can't boot into x initially and you have wireless network. it won't work
Plugging in a LAN cable won't help

But when i re-install with the LAN cable plugged-in, it did recognize it and allowed me to install ATI drivers.

---

