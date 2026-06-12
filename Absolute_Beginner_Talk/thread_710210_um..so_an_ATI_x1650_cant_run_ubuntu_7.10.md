---
title: "um..so an ATI x1650 cant run ubuntu 7.10?"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by cpu_medic on 2008-02-28
so i installed ubuntu on my laptop lastnight, and i love it. now i want to dual boot my vista and ubuntu on my desktop. i read all about it with a little help from google, and was fairly sure that i under stood what i was getting myself into. well i go and stick the live cd in my cd drive, and it looks like it loads up fine, but the screen loses signal but the log on sound still works. im stuck..i need help. again please.:confused:

---

### Post by spamzilla on 2008-02-28
Have you tried booting into 'failsafe graphics mode' when booting to the livecd?

---

### Post by cpu_medic on 2008-02-28
yes i have, and it did the same thing.

---

### Post by spamzilla on 2008-02-28
> **cpu_medic said:**
> yes i have, and it did the same thing.

Try this:

On the livecd, go into the terminal / command line and enter the following:

> sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
startx

Good luck

---

### Post by cpu_medic on 2008-02-28
how do i get to a terminal?

---

### Post by spamzilla on 2008-02-28
> **cpu_medic said:**
> how do i get to a terminal?

Does alt + f2 get you to a command line interface with the livecd? I haven't used a livecd for a while (nor do I have access to one right now), so I can't tell yuo for sure.

edit

ctrl + alt + f2

---

### Post by cpu_medic on 2008-02-28
i think im gunna quit on my desktop for now, im kinda tired. thank you for helping though

---

### Post by dcook727 on 2008-03-02
Spamzilla,
Absolutely brilliant.  I had this same problem and running the fglrx driver setup (while under a live session) worked beautifully.  I had no idea you could run those ATI drivers under a liveCD.

Thank you!!

---

