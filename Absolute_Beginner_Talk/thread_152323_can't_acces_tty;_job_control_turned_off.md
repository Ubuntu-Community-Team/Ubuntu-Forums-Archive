---
title: "can't acces tty; job control turned off"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by Klaas Bruinsma on 2006-03-29
Hi there :) I've installed Ubuntu on my Packard Bell laptop, but it is giving me some errors. Here are the errors:

[B]Uncompressing Linux...Ok, booting kernel.
Loading, pleas wait...
FATAL: Module unkown not found.
mount: Mounting /dev/hda7 on /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or 
           directory
mount: Mounting /dev on /root/dev failed: No such file or directory
Target filesystem doesn't have /sbin/init

BusyBox v1.00-pre10 (Debian 20040623-1ubuntu22) built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't acces tty; job control turned off[/B]

Does anyone know how I can fix this? I've searched on google, but with no result :(

---

### Post by Pragmatist on 2006-03-30
When do you see these messages?  Can you boot at all?  Can you get to a login screen?

If you haven't go to that point, then tell us more about your system.  What kind of hard drive(s) and how many hard drives?  Do you know what partitions you chose?  Are you doing a dual-boot?  If so, what OS other than Linux is on the drive?

---

### Post by Klaas Bruinsma on 2006-03-30
I get this message directly when Ubuntu boots. I don't get to a login screen. It only shows me a hash (#) after the message.
I've got a AMD Athlon based Packerd B(H)ell laptop (WindowsXP) with one harddrive. 

Yes it is a dual boot, but I did not install GRUB in the MBR, otherwise I can't access my "Press F11 for Recovery". I use the Windows bootloader (boot.ini). 

Grub is installed on hda (within the first 1024 cylinders). Then I've made a copie of my /boot. I called it Linux.bin. I've put Linux.bin in my c:/ (root). Then I modified the boot.ini. I rebooted and it worked great :D  

Because I have a AMD Athlon cpu, I wanted to install the AMD based linux kernel (k7). The installation whent great. 1 kernel (k7) installed and 1 kernel(i386) removed. I rebooted, chose Ubuntu in the bootloader and voila....a lot of errors :( 

Thanx for the reply :D

---

### Post by Pragmatist on 2006-03-30
> Originally Posted by: **Klaas Bruinsma**
1 kernel (k7) installed and 1 kernel(i386) removed 
This was not a good idea. When you install a new kernel, you leave the old one in case the new one doesn't work. Also, it is no problem having multiple kernels on the system. The kernel is just a program (about ~40 MB compressed). So when you boot, you choose which kernel you want to run. You probably already have a few ubuntu kernels laying around from earlier versions of the 2.6 (like 2.6.12 2.6.10 2.6.8 etc...)

So, if you do have other kernels laying around, see if you can boot into one of those. From there we can try to see what is wrong with the k7 kernel.

Hopefully you didn't get rid of all your other kernels, but if you did, you'll probably need to use a LiveCD like Knoppix to access the drive and add a 386 kernel, get that to work, then, if you really want to, add a k7 kernel and keep **both** around.

---

### Post by Klaas Bruinsma on 2006-03-30
Yes, I did realy remove all my other kernels accept the K7. I've booted the Unbuntu Live CD, but it's al virtual. How do I install a new kernel when I'am in "Live mode"??

Thanx

---

### Post by Pragmatist on 2006-03-30
> Originally Posted by: **Klaas Bruinsma**
 How do I install a new kernel when I'am in "Live mode"??
 
Just like you can mount a floppy or CD or other partition when using Linux from your hard drive, you can mount your hard drive when running Linux from the CD.

So I would mount the hard drive, download a kernel tarball to the mounted hard drive, and compile the kernel on the hard drive. In this case you are using the compile tools (like gcc and make and a bunch of others) that are on your LiveCD to compile the kernel code which you've put on the mounted hard drive. Then, once you go through all of that, you edit your /boot/grub/menu.lst file to include the information for the new kernel.  Then you reboot without the CD and pray! :)  Just kidding.  It shouldn't be too bad if your comfortable with compiling kernels.

---

### Post by Klaas Bruinsma on 2006-03-31
Thanx for the help :D I'am gonna follow your advise. If I can't work it out, then I probebly do a total new installation. That's the easiest way I guess.

---

### Post by cocox on 2006-05-15
Here is the solution good luck

[http://www.ubuntuforums.org/showthread.php?p=1017808#post1017808](http://www.ubuntuforums.org/showthread.php?p=1017808#post1017808)

:mrgreen:

---

### Post by xyz on 2007-02-28
sorry...wrong post!

---

