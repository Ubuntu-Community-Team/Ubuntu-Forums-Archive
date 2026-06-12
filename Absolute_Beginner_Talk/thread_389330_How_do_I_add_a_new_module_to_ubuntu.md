---
title: "How do I add a new module to ubuntu?"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by cobrn1 on 2007-03-20
Hi everybody. I'm quite new to linux and just starting out (but really enjoying it!) Anyway, I've managed to get most things working but i've hit a slight annoyance:

To connect to the internet i have to use a USB to ethernet adaptor (the DM9601)- this isn't a problem as i found someone who'd build a module to enable it's support in ubuntu 6.10. However, in order to get the internet working, each time I boot up into ubuntu, I have to go into the terminal, change directory to my home one (where I have the module) and then add it, ie:

cd /home/me/internetstuff
sudo insmod dm9601.ko

The internet then works perfectly. I wanted to know if there was a way to get ubuntu to do this automatically at startup. Like I said, I'm quite new to linux, so please explain any answers as fully as possible as vagueness will only confuse me! ;-)

---

### Post by jadda on 2007-03-20
I am quite new myself, and may be wrong, but:
System-->Preferences-->Sessions, go to Startup Programs and add:

cd /home/me/internetstuff
insmod dm9601.ko

I

---

### Post by cobrn1 on 2007-03-20
unfortunately, it doesn't seem to work... but thanks anyway.

BTW, I forgot to put in the 'sudo', ie, the line is:

sudo insmod dm9601.ko

but that didn't work either in the session preferences...

---

### Post by cobrn1 on 2007-03-21
Ah - finally cracked it!

first I made a new folder as root:

```
sudo mkdir /lib/modules/2.6.17-10-generic/dm9601
```

then copied the module dm9601.ko into it. Made sure that the permissions for the folder were ok for everyone to read it, etc...

Then went into the terminal and typed in:

```
sudo /sbin/depmod -ae
```

To ensure that the module had been recognised and added to ubuntu's list of availiable modules.

Then opened up the file 'modules':

```
gksudo gedit /etc/modules
```

and added:

```
dm9601
```

to the bottom.

Voila! All working - module loaded at startup and no more messing about in the terminal to get the internet! One satisfied ubuntu user!!! :-)

---

### Post by Tomosaur on 2007-03-21
If only everybody was as patient as you :P
Many people give up as soon as they have a single little problem!
Congrats on getting it all running smoothly anyway, and welcome to the forums.

---

### Post by windjohnson on 2007-04-25
Would you PLEASE PLEASE PLEASE send the dm9601.ko file to me???
I've tried for so many times trying to build the modul but it just never works.
Thank you!

[email]johnson_tsai_1987@hotmail.com[/email]

---

### Post by Mike71 on 2007-04-28
Where did you get the module? I tried using the 2.6.21 kernel but it doesn't really work so I would really appreciate if you could tell me where you got it from!

---

### Post by cobrn1 on 2007-05-15
Sorry for taking so long to reply. I found the ported version (for 2.6... kernel) at:

[http://alcopop.org/unix/linux/dm9601/](http://alcopop.org/unix/linux/dm9601/)

hope this helps

COB

---

### Post by ghmercado on 2007-05-27
hi i still cannot find the dm9601.ko in the 

[http://alcopop.org/unix/linux/dm9601/](http://alcopop.org/unix/linux/dm9601/)

site you mentioned. In his repository:

[http://alcopop.org/unix/linux/dm9601/git/](http://alcopop.org/unix/linux/dm9601/git/)

I only see the contents of the dm9601-2.6.tgz (Makefile, dm9601.c, dm9601.h, readme.txt). Are you supposed to rename that file?

PLEASE PLEASE someone send me that dm9601.ko file?

[email]ghmercado@gmail.com[/email]. MUCH thanks.

---

### Post by kiyakerkan on 2007-05-28
Please someone send me 9601.ko. I have tried to compile this module but i coudnt. i need this 9601.ko file. my mail adres is [email]kiyakerkan@gmail.com[/email]

---

### Post by cobrn1 on 2007-06-11
Hi everybody,

sorry I've taken so long to reply (again), but I've been a little bogged down at the mo and haven't been here for a while.

Anyway, I guess I wasn't clear enough last time I posted. The file you're looknig for for making the dm9601.ko module is: dm9601.GZ

This contains the make file (and an all important readme on how to use it).

It can be downloaded from:

[http://alcopop.org/unix/linux/dm9601/](http://alcopop.org/unix/linux/dm9601/)

It's down near the bottom of the page under the historical / misc heading and is called ***alternative 2.6 port*** (3rd option down).

You shouldn't have any problems make using the makefile (assuming you're using the 2.6.... kernel).

Only prob is that you'll have to insmod it at startup. However, if you look above I managed to fix that and enable the module automatically on startup (but this was only for Ubuntu 6.10 - haven't a clue if it works for any other version, sorry folks...)

PS: Sorry I can't just send you the dm9601.ko module, but I had to wipe the installation and don't have a copy of it anymore.

Hope this helps and best of luck,

Cobrn1

---

### Post by cobrn1 on 2007-06-11
I don't like direct linking, but this is the direct link to the dm9601.GZ file:

[http://www.silencio.ro/DM9601.GZ](http://www.silencio.ro/DM9601.GZ)

---

### Post by cobrn1 on 2007-06-11
BTW, kernel version 2.6.21 has a native driver for the dm9601.

Though you might like to know...

:-)

---

