---
title: "Fdisk"
date: 2006-02-06
forum: Apple PPC Users
---

### Post by auke5 on 2006-02-06
i did my install of Kubuntu just fine, but cant figure out how to use fdisk.  is there a special codec i need to put in other than fdisk/dev/hda0.  the Konsole doesnt accept that, and just typing "fdisk" like i've also been told doesn't work too well either.  any help on re-partitioning/formatting my HD would be great.

also, when i formatted i noticed that i didnt have the option of doing HTS/apple HD formatting...how would i go about formatting it so that i could get my Tiger installed on here now that i wiped it out...?

---

### Post by krusbjorn on 2006-02-06
[QUOTE=auke5]i did my install of Kubuntu just fine, but cant figure out how to use fdisk.  is there a special codec i need to put in other than fdisk/dev/hda0.[/QUOTE]
Put a space between "fdisk" and "/dev/hda0" and execute the command with sudo.

I'm also curious on the apple filesystem formatting, since I'm sitting here with a fully legally aquired version of OSx86 ;)

---

### Post by LongTooth on 2006-02-06
I would doubt you don't have fdisk. But maybe that's the problem. Do a apt-cache search fdisk. Install it if you don't. I'd like to recommend cfdisk. Its easier to use. Much easier. I started off using fdisk until I discovered cfdisk. Since then, I haven't touched fdisk. 

Again do a cache search. smartjak@microatx:~$ sudo cfdisk /dev/hda
Password:

is the command to access cfdisk.

---

### Post by GMachine_24 on 2006-02-07
Hi:

If you want to use a partitioning/formatting device with a GUI, try QTParted, a free app

sudo apt-get install qtparted

similar to the Windows Partition Magic. You can partition and format your hd using QTParted. You still need to mount it, though, and enable it to be recognized on startup.

You should also be aware that there is a disk management tool under System>Administration>Disks

Good luck.

gmachine_24

---

