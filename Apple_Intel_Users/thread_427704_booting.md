---
title: "booting?"
date: 2007-04-29
forum: Apple Intel Users
---

### Post by kozo819 on 2007-04-29
[SIZE="4"]ok so i have the ubuntu on the disk that i burned so problem.  it couldn't varify but when i open the cd i'm able to open like the picture files and stuff.  now what do i do?  i'm so confused.  i shut down my computer with the disk in the drive and when i started it up again it booted mac os x.  i don't know what i'm doing wrong.  i just wanted to try linux for fun.  thanks for the help!![/SIZE]

---

### Post by davidgarcin on 2007-04-29
Ummmmm..... if I understand you correctly, you just need to hold down a key so that it lets you choose the CD as the boot device.  I don't know what that key is on a Mac, but it should tell you at the boot screen.  On PCs its usually F8 or F12.

---

### Post by davidgarcin on 2007-04-29
a little googling goes a long way:  just hold down 'C'.

---

### Post by ronocdh on 2007-04-29
> **davidgarcin said:**
> a little googling goes a long way:  just hold down 'C'.
Another option is to use [rEFIt]("http://refit.sf.net") as a bootloader. It will prompt the user with a graphical interface allowing a boot from CD. REFIt is extremely handy when dual or triple booting.

---

### Post by kozo819 on 2007-04-29
[SIZE="4"]holding down "c" worked  but i had another problem

after it rebooted i got excited because it wasn't loading th mac os x and then a black screen came up and it said 
Your CPU does not support long mode.  Use a 32bit distribution." i picked the 64bit because it said intel and my macbook has an intel processor.  i guess the 32bit one is the standard personal computer so thats what i'm trying now.[/SIZE]

---

### Post by davidgarcin on 2007-04-29
yup, you definitely need the 32-bit verison.

---

### Post by ronocdh on 2007-04-30
> **kozo819 said:**
> [SIZE="4"]holding down "c" worked  but i had another problem

after it rebooted i got excited because it wasn't loading th mac os x and then a black screen came up and it said 
Your CPU does not support long mode.  Use a 32bit distribution." i picked the 64bit because it said intel and my macbook has an intel processor.  i guess the 32bit one is the standard personal computer so thats what i'm trying now.[/SIZE]
This is a common mistake due to poor branding on Intel's part. First came the Core Duo, which was so named because it had two cores; however, it was still a 32-bit processor. Shortly thereafter came the Core2 Duo, which was dual core and truly 64-bit. With a Core2 Duo (often abbreviated as "C2D"), it's possibly to run the AMD64 version of Ubuntu, and get the most out of your processors. For a Core Duo set up, though, just use the regular i386 version.

The default kernel, which the i386 image will install, has support for SMP and so you will be to utilize both cores.

---

