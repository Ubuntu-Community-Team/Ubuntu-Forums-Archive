---
title: "PPC G4 Dual booting... HELP! SOS!"
date: 2010-07-31
forum: Apple Hardware Users
---

### Post by MacPenguin1972 on 2010-07-31
Hello,

I am running a dual-processor G4

  Machine Name:    Power Mac G4
  Machine Model:    PowerMac3,6
  CPU Type:    PowerPC G4  (2.1)
  Number Of CPUs:    2
  CPU Speed:    1 GHz
  L2 Cache (per CPU):    256 KB
  L3 Cache (per CPU):    1 MB
  Memory:    1.5 GB
  Bus Speed:    167 MHz
  Boot ROM Version:    4.4.6f2

I have two hard drives- an 80GB Master and a 300GB slave- I reformatted my 80GB with two partitions and moved all my mac stuff to the larger drive. I made two partitions on the first hard drive. On the first I loaded the latest version of Ubunto (10.x) that I got from an instructor at school on a CD. the CD works like a charm booting with the c command at startup.

I then loaded Mac OS X back onto the second partition on the reformatted 80GB HD.

What I want to know is- Mac OS now reboots every time since the reinstall and I cannot get back into Ubuntu.

How do I boot into the Ubuntu partition? Can I use a command in OPEN FIRMWARE? what can I do to cause the Mac to boot the Linux, and not Mac OS - I would like to have the choice of which system to load at startup. I cannot figure out how to achieve this.

I would appreciate any help. Thx. :-)

Cheers!
The Penguin

---

### Post by oswaldkelso on 2010-07-31
Zap the Pram is the quick way. If that doesn't reset it re-bless your yaboot.conf

To get into your Ubuntu install hold down the alt/opt key on boot. Then select it from the menu

---

### Post by Frostraver on 2010-07-31
You can boot into the different partitions by holding the Alt button when booting your computer. Then it gives you a new window where you can choose wich OS you want to boot. (This works if you have made a dual-boot with the software from mac itself)

Edit: didn't see that there already was a reply with the good answer...

---

