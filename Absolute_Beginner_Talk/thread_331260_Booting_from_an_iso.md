---
title: "Booting from an iso"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by tryby on 2007-01-04
Hello, i download the operating system ubuntu 6.06 live cd in .ISO format, but i don`t have an cd-rw to write it on a cd. I have the question if there is a program with i can boot with this iso ... so, is that possible to boot ubuntu from an iso on my hard drive?

---

### Post by jbayone on 2007-01-04
There are programs to mount an .iso as on a virtual drive.  But I don't think it would be possible to do that on a boot.

---

### Post by pmurnane on 2007-01-04
I think jbayone is right on this one.  Perhaps someone or some place (school or business) you know would burn it to a CD for you?

---

### Post by meng on 2007-01-04
It is possible to boot from an iso, but you have to use a virtual machine like qemu.

---

### Post by tryby on 2007-01-04
And what programs do you recomand me? i used Virtual machine but i get this error 
[http://www.marte.lx.ro/vm.html](http://www.marte.lx.ro/vm.html) is that because i don`t have enough space on my disk? or what? what can i do to make that run, what can i do to boot that .iso in virtual machine? or is a way to boot this iso.

Later edit : qemu, what`s that , where can i download it , where i can run the program and the requirements. PLease some info :D

---

### Post by meng on 2007-01-04
I can't connect to that link. What OS are you using? Windows?

---

### Post by tryby on 2007-01-04
Yes i`m using windows XP no service pack. and i have an pentium 2 at 300 mhz , 192 ram and 3 hdd one of 8 gb, one of 2gb and one of 3 gb. Thanks

Okay i have qemu ... but how i can boot that .iso image? :D

---

### Post by Sasa_Ivanovic on 2007-01-04
It's very complicated to do so. I have thought about it myself, but it's not worth the trouble...

What you could do ( maybe ) is extract all the files from iso on a hard drive (or a partrition ), reconfigure BIOS to boot from that hard driver, restart, and have luck.

---

### Post by meng on 2007-01-04
Well for a start I wouldn't recommend running the Live CD with only 192 MB RAM, and definitely not in a virtual machine. I would download the Alternate CD and get it burned. Another option is to use a flash drive if your BIOS can boot from one. Better search these forums for "livecd flash bootable" or something like that, otherwise look here for tips: [www.pendrivelinux.com](www.pendrivelinux.com)

---

### Post by tryby on 2007-01-04
Another advices? :( i`m desperate i wanna make this work, what commands should i use in qemu? :(

---

### Post by meng on 2007-01-04
Check this out.
[http://kidsquid.com/cgi-bin/moin.cgi/QemuOnWindows#head-ce843f687f49b03d5de4849c0edd501768cfc393](http://kidsquid.com/cgi-bin/moin.cgi/QemuOnWindows#head-ce843f687f49b03d5de4849c0edd501768cfc393)

Don't say I didn't warn you! I expect the result will be bad!

---

### Post by Sasa_Ivanovic on 2007-01-04
Even if you could make this run in qemu, it wouldn't run 'cause of your cpu slowness. And if it would run it would be very slow compared to booting from a CD or HDD.
So quit it.

---

### Post by gilbertr on 2007-01-04
It is not worth doing.

To run the live CD or install Ubuntu for that matter, you really need a minimum of 256MB RAM - you don't have it.

If you want to install Ubuntu on your PC, you would need to burn the CD (and add some RAM)
If you don't want to add RAM, I suggest you take a look at DSL (Damn Small Linux).

If you are looking at running Ubuntu in virtual mode, add RAM and install VM software.
This could be qemu, VMWare or MS Virtual PC 2004 (MS even offers this as a free download).

You will have tweaking issues whichever route you take and I have doubts about the performance on your PC - personally I would not even attempt it.

Good luck :-k

---

### Post by tryby on 2007-01-04
it works, slow , but still works, thanks for the help ;)

---

