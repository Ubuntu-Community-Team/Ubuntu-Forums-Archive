---
title: "Computer problems"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by cristiaana sabella on 2008-01-10
My computer was giving me trouble so my son installed Ibuntu. I love it and all seemed fine. Now when I turn on the computer some things come up on the screen that keep things from functioning. Does anyone know what this may be? 
When it starts is says Error 16: Inconsistent filesystem structure. So I turned it off and tried again and then it gave me an Error again and to press any key to continue. I did and it gave me a menu of Ubuntu 'general' and a secondary one in case of emergency so I pressed the 'general' on and it then worked. What do you
think of this behavior? It has happened twice now when trying to start the computer.
Thanks,
Cristiaana

---

### Post by Pevichaey5 on 2008-01-10
do you have a dual boot with anything?

---

### Post by taurus on 2008-01-10
Sounds like a corrupt filesystem.  How do you normally shut down Ubuntu?  Do you go through the shutdown button or do you just turn it off with the power button?

---

### Post by nowshining on 2008-01-10
keep rebooting and fsck should come up and auto-check it or in live cd u'll need to fsck it.

info. u'll need beforehand?

the mount point of the drive, i'm assuming it's /dev/sda1
(since by default the main drive is)

in live cd, open up applications - terminal

type the following or copy and paste it,

[B][I]sudo fsck -a -w -v /dev/sda1

that should fix it, reboot and try again.
[/I][/B]

---

### Post by nowshining on 2008-01-10
oh by the way fsck is a file-checking/repairing program for unix/linux, it's like scandisk and checkdisk in windows.

---

### Post by cristiaana sabella on 2008-01-11
Thank you we will try that and let you know ...wonderful, thanks!

---

### Post by nowshining on 2008-01-11
hope it works

---

