---
title: "Default Boot + Modem Troubles"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by mitchmaster on 2006-09-05
Hi, my name is Mitch and I am having troubles with two things on my pc with Ubuntu 6.06 LTS. The first one should be easy but I just cannot figure it out (sorry, I am noobish in Linux) I cannot figure out how to get the Default operating system to be XP... I don't know what kind of info you guys would need but that's all I can tell ya...


The second problem I am having is that I cannot get my Agere Soft Modem to work. It is V.92 and I don't know what else kind of information I could give you... But if you reply telling me what you need I will definitely get it for you... (I don't even know how to set any of it up, sorry)


Thank you so much guys you're the greatest!

Mitch

---

### Post by jISh on 2006-09-05
About the modem I'm not sure, there might be drivers for you, sarch around the forums.

As for default OS being Windows, open up terminal (applications > accessories > terminal) and type
sudo nano /boot/grub/menu.lst

Change the default option to one number less than where Windows is listed in your grub menu (confusing maybe, it's because GRUB counts from 0 instead of 1).

So if it's the second option if your menu, default would be 1.

CTRL+O and enter to save, CTRL+X to quit.

---

### Post by ieee488 on 2006-09-05
For your modem, start with this HOWTO
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

Basically, it tells you to download scanModem.gz and install it to learn more about your modem.

It is highly likely your modem won't work with Linux.
There are few that do though.

If you don't want to go through all the hassle, the thing to do is buy a used **serial** external modem on eBay and plug it into your COM port. You should be able to get one for about $10.

---

### Post by mitchmaster on 2006-09-06
Thanks Guys I'll have to try both of those after i get home from school:(

seeya later!


Mitch

---

### Post by mitchmaster on 2006-09-07
Well, the default boot was easy to change:) Thanks a lot dude...

But the modem troubles are not so easy to do...
is there anyone who could maybe walk me through everything after getting scanmodem and running it?

Thanks again,

Mitch

---

### Post by ieee488 on 2006-09-07
executing *scanModem* will generate a couple of files.
You'll need to read your read1st.txt and modemdata.txt files to see what it says.

---

