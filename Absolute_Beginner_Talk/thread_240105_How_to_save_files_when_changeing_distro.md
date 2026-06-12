---
title: "How to save files when changeing distro?"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by vaazu on 2006-08-20
I want to change my xubuntu to debian, because Xubuntu crashes when I use any torrent program (wireless card). But I have allready downloaded about 10GB of files that I want to save. The thing is I don´t know how to do that. I think if I would creat an new partition and move my files there and then format the other half of the disk would do. But I havent created any partitions in linux and even dont know which program do use. I really dont want to lose this data so could anyone give me any advice what do to.

---

### Post by taurus on 2006-08-20
Boot with the LiveCD (desktop CD) and use gparted to resize your harddrive...

---

### Post by vaazu on 2006-08-20
That one just doesnt work nothing happens. Is there anyway I can do it in linux not from cd, just download a program like partition magic and resize it?

---

### Post by Tortanick on 2006-08-20
Unless I'm mistaken you can't resize or otherwise modify a partition thats mounted. And you can't unmount root while you're useing that OS.

I'd say a live CD is your only chance at this, Can you say exactly what dosn't work with resizeing from the live CD? And what Live CD are you useing? Ubuntu? Gparted? Knoppix?

---

### Post by vaazu on 2006-08-20
xubuntu and gnome partition manager. I started it resized my current partition and made a new from the free space. Pressed apply a gray box appeared, waited for about 30 minutes and then gave up, because nothing happened.

---

### Post by vaazu on 2006-08-20
Is it possible to use mp3 player as usb disk? I have 256mb creative zen nano mp3 player and it can be plugged into usb so can I use it as a usb disk to boot GParted Live CD? And If I can do I just have to extract those iso files to the player?

---

### Post by taurus on 2006-08-20
> **vaazu said:**
> xubuntu and gnome partition manager. I started it resized my current partition and made a new from the free space. Pressed apply a gray box appeared, waited for about 30 minutes and then gave up, because nothing happened.
You CANNOT resize a partition when it's in use!  You need to boot from a LiveCD and use gparted from the LiveCD to resize your partition.  Otherwise, good luck trying to resize it while booting into Ubuntu...  ](*,)

---

### Post by vaazu on 2006-08-20
> **taurus said:**
> You CANNOT resize a partition when it's in use!  You need to boot from a LiveCD and use gparted from the LiveCD to resize your partition.  Otherwise, good luck trying to resize it while booting into Ubuntu...  ](*,)
I tried to use it with xubuntu live CD but it didn´t work. Nothing just happened I explained it above.

---

