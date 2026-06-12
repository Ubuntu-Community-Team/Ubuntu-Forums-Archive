---
title: "Why Cant I Have ubuntu?"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by galego on 2006-08-07
OK Im not too new but trying to follow rules i thought id post here. i have the ubuntu cd (burnt-and checked- and the original) both cds work i know because i have checked them on a different box with windows only. when loading the live cd it fails when it tries to initiate the X console and gives error. both cds fail at the same spot. i am currently running a dual boot with MEPIS and Windows Vista. i tried and other distro (PCLINUXOS) and it loads no problem. i have no clue as to why it just wont start the X console?

BTW i tried the kubuntu cd and it gets hung up when it should begin to load the X console. does not give error message however.](*,) 

thnaks for any insight!!

---

### Post by taurus on 2006-08-07
Sounds to me like there is a problem with your graphic card.  Why don't you download the alternate CD and use it to install Ubuntu on your machine then!  It's a text base installer and once you have installed it but still have a problem with your video card, X, then you can configure it with

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by galego on 2006-08-07
is it that ubuntu just doesnt like it or just doesnt know where it is? 
my card: ATI Radeon X700pro PCie

there is no work around with the cds i have?

---

### Post by muep on 2006-08-07
Did you try the

sudo dpkg-reconfigure xserver-xorg

command?

For me, it has worked every time. If no other, at least the vesa driver tends to be very well working. After the reconfiguration, do this:

sudo /etc/init.d/gdm restart

If it still doesn't start, do the reconfiguration again.

By the way, Ubuntu doesnät install the official ATi drivers as default, because they are not free software. If you want to install them, use:

sudo apt-get install xorg-driver-fglrx

After that, reconfigure and do the gdm restart thing.

---

### Post by galego on 2006-08-07
Did you try the

sudo dpkg-reconfigure xserver-xorg

command?


...and i can do this from the boot prompt? 

I just thought of something. would running the official ATI driver in MEPIS cause the confusion, so if i remove the ATI driver from MEPIS could that have the same effect?

---

### Post by muep on 2006-08-07
Yes, you can run the command from the text-mode command prompt.

I am not sure if MEPIS has the official ATi driver or not. You can get graphics working either with or without it. MEPIS just seems to have a better automatic configuration of hardware. If it is configured to use the official driver and you remove it, it sure would not work after that, though MEPIS might have some recovery mechanism for even those situations. I don't know.

Ubuntu takes a little more work, but after you get it working, it works very well. Nowadays even those ATi cards aren't much of a problem, the drivers have improved a lot lately. There is still a lot to improve, but at least I usually can get the graphics acceleration working.

Ask here if you need any help with the reconfiguration. It asks a lot of questions, though with most of them, the default options work fine.

---

### Post by galego on 2006-08-07
thanks Muep, i will try when i return to my computer.
BTW, by default MEPIS does not have the ATI driver installed, but what they have which is pretty nifty, is more or less a link. you go the control center and configure display and has a tab for nvidia, and ATI. for ATI you simply click install and wait about 1 minute and restart. prety gosh darn simple heh? to me coming from SUSE that was just what i needed to remove SUSE 10.1.

sorry digressing, i will try thanks!

---

### Post by galego on 2006-08-07
Im writing from ubuntu. i just did my standard check of what works and what doesnt, and well... everything works! The printer wizard... it really is a wizzard. the sound after alsamixer .config works, well i still have to get the w32 codecs but thats a different story. anyways all i had to do from the begining is boot with safe display and boom boots right up did not have to do dpkg. thanks for the help and i think i found my distro!!!:p

---

### Post by -deadcats on 2006-08-07
Good for you! :)

I can personally recommend Automatix for your codec and other needs (there are others---I "hear" EasyUbuntu also mentioned--but Automatix is all I've ever needed).

Best of luck!

regards,
-dc

---

