---
title: "How to get the mouse to work?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by myCharlie on 2007-10-24
Okay, I hope someone can help me on this. I installed my Ubuntu inside of Microsoft Virtual PC 2007. Ubuntu started fine, I can logged in fine now. The problem is, the mouse doesn't work. Anyone know how to get the mouse to work in Ubuntu when it is instaleld inside of MS Virtual PC?

Thanks so much!

---

### Post by Dr Small on 2007-10-24
MS Virtual PC must be something like VirtualBox..
On VirtualBox, I press CTRL and then I can move the mouse around inside of the system.

Is this your problem, or did I misunderstand ?

---

### Post by myCharlie on 2007-10-24
That is exactly my problem. I tried the CTRL and it's not working. I still can't move my mouse inside the OS?

---

### Post by Dr Small on 2007-10-24
Look through the options of your MS Virtual PC and see if you can find some way to *control* the system.

---

### Post by myCharlie on 2007-10-24
Okay, I went into Edit/Settings and I saw this under Mouse:

With pointer intergration enabled, you can move the pointer between the virtual machine window and the host operating system. Some programs might be incompatible with pointer integration. Pointer integration is available only after Virtual Machine Additions is installed.

So I guess that's why the mouse is not working. The problem is, the Virtual Machine Additions are only availble for Windows and OS/2. So is there some VM Addition somewhere for Linux?

One other thing, right now the Ubuntu screen is black. Nothing is showing anymore on the virtual machine window. This happens everytime I'm not interacting with the Ubuntun OS.

---

### Post by myCharlie on 2007-10-24
So does anyone have any idea on how to install Virtual Addtions for Ubuntu? And where do I download the Addtions?

---

### Post by myCharlie on 2007-10-24
Okay, according to this [article]("http://arcanecode.wordpress.com/2007/04/25/ubuntu-704-and-virtual-pc-2007-mouse-issue-workaround-sort-of/"), it is a problem within the kernel of Ubuntu 7.04. However, since I'm using the latest version of 7.10, is this the same problem? Has this problem been fixed in the 7.10 version?

---

### Post by johnspartan6000 on 2007-10-24
Good question. From what I understand, there are Vm Additions for Linux - but they were specifically designed for Virtual Server, not Virtual PC, and though you can supposedly use them for Virtual PC, this configuration is "unsupported", and, even using with with VPC, to make it work with other linux flavors than the ones it was designed for (none of which are Ubuntu),  you need to edit.... something, in the linux additions. I have no idea how to do this.

I'm in the same exact boat.

---

### Post by myCharlie on 2007-10-25
Yes, I have seen those addtions for the other Linux flavers and not Ubuntu. It is really useless if Ubuntu does not support mouse. According to that article, this problem occurs in version 7.04 but apparently this problem is not resolved in version 7.10. I'm very dsapointed my first attempt to use Linux turned out to very unpleasant.

---

### Post by johnspartan6000 on 2007-10-25
well, I've had lots of luck installing regular (i.e. not the 'x' lite flavor, or server - no experience with that) ubuntu on desktops, but they weren't inside a virtual machine.

---

### Post by myCharlie on 2007-10-25
I assumed that Ubuntu will work outside of virtual machine...but I want to test this new OS to see if I like it or not that's why I decided to use it inside a virtual machine and so far it's not working like I expected. I wonder if Novel SUSE Linux Enterprise Desktop 10 is working isnide of a virtual machine. I guess I'll have to ask their forum.

Thanks for your reply.

---

### Post by myCharlie on 2007-11-01
Okay, despite the great support from this forum, I am unable to use ubuntu without the mouse working. I decided to trash the ubuntu partition and instead install Novell's SUSE Linux Enterprise 10 sp1. It's free too with the execption of updates. Anyway, so far the installation went very well compare to Ubuntu. For one thing, the mouse is working just fine and unlike Ubuntu, I don't have to install Ubuntu in Text Mode. I'm sure that I will not have all these problems if I'm not installing ubuntu inside of Virtual PC.

---

