---
title: "Compiling the Kernel"
date: 2012-07-08
forum: Any Other OS
---

### Post by Geffers on 2012-07-08
I have a Raspberry Pi and want to use this to learn a wee bit more about the command line; I am using the Debian version.

If I recompile the Kernel does it have to be done on the system I am using or could one machine be used to compile a kernel on a different disk.

Geffers

---

### Post by iponeverything on 2012-07-08
google "raspberry pi cross compiler"

short answer is yes.

---

### Post by Geffers on 2012-07-08
> **iponeverything said:**
> google "raspberry pi cross compiler"

short answer is yes.

Thanks for quick reply.

Geffers

---

### Post by pe7er on 2012-07-13
> **Geffers said:**
> I have a Raspberry Pi and want to use this to learn a wee bit more about the command line; I am using the Debian version.
You could also use ArchLinuxARM to learn the command line.
However it's not a .deb distribution like Ubuntu/Debian/Mint, so you can't use apt-get etc.
However, IMHO Arch is a good way to learn how to use the command line.

btw: to improve my command line skills I am reading "Ubuntu Linux Toolbook - 1000+ commands for Ubuntu and Debian Power Users" at the moment. 
So far it's the best book I have come accross...

---

### Post by Geffers on 2012-07-14
> **pe7er said:**
> You could also use ArchLinuxARM to learn the command line.
However it's not a .deb distribution like Ubuntu/Debian/Mint, so you can't use apt-get etc.
However, IMHO Arch is a good way to learn how to use the command line.

btw: to improve my command line skills I am reading "Ubuntu Linux Toolbook - 1000+ commands for Ubuntu and Debian Power Users" at the moment. 
So far it's the best book I have come accross...

I'll look in to ArchLinuxARM, I used to program in basic and machine code on my old Acorn machine (I know command line is different) so that may be interesting.

I will look at the Ubuntu Linux Toolbook.

Thanks,

Geffers

---

### Post by Perfect Storm on 2012-07-14
Thread moved to Other OS/Distro Talk.

---

### Post by Bachstelze on 2012-07-15
> **Geffers said:**
> I have a Raspberry Pi and want to use this to learn a wee bit more about the command line; I am using the Debian version.


Why not use your computer with Ubuntu?

---

### Post by pe7er on 2012-07-15
> **Bachstelze said:**
> Why not use your computer with Ubuntu?
The Raspberry Pi is not a "normal" computer, meaning that it does not have an Intel processor (i686 and x86-64 architectures) like "normal" computers have.

The Raspberry Pi has an ARM processor (ARMv6). 
There's a current Ubuntu version available for ARMv7, 
but lower ARM versions are not supported.

Therefore I would recommend using ArchLinuxARM for the Raspberry Pi. 
Or Debian (because software + installation method on Ubuntu and Debian are very similar).

---

### Post by Bachstelze on 2012-07-15
I know very well what a Raspberry Pi is, thank you very much. My question still stands: why not use your x86 computer if you want to "learn the command-line"? If anything, the "unusualness" of the ARM is going to get in the way of learning, not improve it.

---

### Post by pe7er on 2012-07-15
Yes, you are right: any computer will do to learn Command Line Linux...
However, the topic starter has a Raspberry Pi and wants to master the command line with it.

IMHO using different Linux distributions will learn you more about Linux in general, but also about the differences between distributions.
e.g. I was used to the "sudo" command in Ubuntu.
But when I installed Arch Linux, that command wasn't available and I had to install it myself (which was very easy to do).
I had always thought that "sudo" was part of Linux / available in any distro.

---

