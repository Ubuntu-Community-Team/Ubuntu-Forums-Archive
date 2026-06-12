---
title: "Grub Boot with Vista and Ubuntu 6.06LTS"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by pez6_9 on 2007-01-09
I have installed Ubuntu, and then vista, both fine.

Then i tried to install the grub, but It didn't find vista.

Is there a grub out there that works with vista.

Oh, and does anyone know how to install drivers for wireless network cards?

---

### Post by Sasa_Ivanovic on 2007-01-09
GRUB works with every OS. Maybe it isn't set up right ...
Boot Ubuntu ( recovery mode ) and see if /boot/grub exsists.

---

### Post by pez6_9 on 2007-01-09
It does a lot of setting up, and then stops at "root@pezlaptop:~#" ... ?!?

---

### Post by pez6_9 on 2007-01-09
[CENTER]<Bump>[/CENTER]

---

### Post by meng on 2007-01-09
Be patient. 16 minutes is not that long to wait. Complicated problems often wait longer before someone comes along who know hows to solve it.
root@pezlaptop:~# is a root user prompt in Linux, I'm not sure how you got there, are you booting in recovery mode or something?

---

### Post by pez6_9 on 2007-01-09
Yes, ^^^ Ubuntu 6.06 (Recovery) ^^^

---

### Post by meng on 2007-01-09
Then you could TRY this:
fdisk -l

---

### Post by tonyr1988 on 2007-01-09
What's inside /boot/grub/menu.lst? (sudo gedit /boot/grub/menu.lst)

---

### Post by pez6_9 on 2007-01-09
Excuse my ignorance but how do I type the letter that looks like a capital [COLOR="Red"]I[/COLOR]

---

### Post by pez6_9 on 2007-01-09
doesn't matter, i'm there (it's the key under the esc right?!)

---

### Post by meng on 2007-01-09
It's an L for Larry.

---

### Post by pez6_9 on 2007-01-09
i'm in fdisk-l, what now?

---

### Post by meng on 2007-01-09
Well tell us what the output of the command was.

---

### Post by pez6_9 on 2007-01-09
it just comes up with an arrow ">", nothing more

---

### Post by meng on 2007-01-09
Exit then (ctrl-d or ctrl-c, I'm not sure)
Are you sure you typed
fdisk<space>-l<as in Larry>

---

### Post by pez6_9 on 2007-01-09
it boots up ubuntu

---

### Post by meng on 2007-01-09
Well, either we're going around in circles or you're having more than one conversation.

fdisk -l isn't supposed to fix the problem, it's meant to tell us where your Vista is installed, so that then you can go and edit the /boot/grub/menu.lst and create an option to boot Vista. It's a two-step process.

---

### Post by pez6_9 on 2007-01-09
can i do it in terminal, or will I have to boot ubuntu (recovered) again?

---

### Post by meng on 2007-01-09
You can do it in the terminal, but you'll need to
sudo fdisk -l
(and enter your user password when prompted)

this should tell you the device name of the partition where Windows is, e.g. /dev/sda1 or something like that

then you
sudo nano -B /boot/grub/menu.lst
and add something like

title Windows Vista
rootnoverify (hd1,1)
makeactive
chainloader +1

but the numbers 1,1 will vary depending on the device ID.

---

### Post by pez6_9 on 2007-01-09
right, in fdisk -l, what do you want me to tell you?

there are three partitions, one for linux, one for swap and another that system says "HPFS/NTFS" useful?

---

### Post by meng on 2007-01-09
Yeah, what's the /dev/??? on the HPFS/NTFS one?

---

### Post by pez6_9 on 2007-01-09
/dev/hda3

---

### Post by meng on 2007-01-09
then replace the numbers 1,1 with 0,2

What you want to do is edit the /boot/grub/menu.lst file
sudo nano -B /boot/grub/menu.lst

and at the end, create a new section as in my earlier post (but use (hd0,2))

then save it and reboot!

---

### Post by pez6_9 on 2007-01-09
I have restarted btw, I'm not in terminal!

---

### Post by pez6_9 on 2007-01-09
after being in the fdisk -l, I enter the command "/boot/grub/menu.lst"

and it comes up with Permission denied!

---

### Post by pez6_9 on 2007-01-09
i'm in the sudo nano -B /boot/grub/menu.lst what now?

---

### Post by pez6_9 on 2007-01-09
[CENTER]<Bumpage>[/CENTER]

---

### Post by meng on 2007-01-09
Seriously that bumping is annoying me, are you really in that much of a rush?

sudo nano -B /boot/grub/menu.lst

then add this to the end of the file:

title Windows Vista
rootnoverify (hd0,2)
makeactive
chainloader +1

then SAVE and REBOOT.

---

### Post by pez6_9 on 2007-01-09
I've tried that, but i get error23: Error while parsing number!

---

### Post by pez6_9 on 2007-01-09
Oh, and i am in a rush, i've got a maths exam tommorow, i need to be able to wake up for it!!! :D

---

### Post by meng on 2007-01-09
Well I'm not sure what's going on then. Good luck with the exam. You should probably get some rest rather than stress yourself trying to get the computer working.

---

### Post by pez6_9 on 2007-01-09
Cheers for the help by the way, I can feel it, only a few steps away. It's much appreciated! :D

---

### Post by meng on 2007-01-09
I would have liked to have helped you get this working, but my advice is not to muck around with Linux when you have a deadline. It just adds to the frustration and spoils your experience of Linux.

---

