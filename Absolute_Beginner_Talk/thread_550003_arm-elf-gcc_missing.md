---
title: "arm-elf-gcc missing"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by sitec on 2007-09-13
Hi.
I have just installed ubuntu and I'm trying to compile one project (openpcd firmware).

I always get error message saying:

sh: arm-elf-gcc: not found

I have spent hours and hours but without success. Is there any package i should install? (apt-get install ...) ?
or what am i supposed to do to have it?

I'm sure there is another way than downloading sources of binutils, gcc and building it by myself...

please help.

thanx.

---

### Post by justleen on 2007-09-13
sudo apt-get install build-essential


should install all the tools you need to compile


edit: 
on second thought .. are you sure you got the right package?  i see ARM , thats not normally in anyones PC..
> he OpenPCD Firmware is the code that actually runs on the hardware, specifically the SAM7. It has been written in the C programming language, and is compiled using GNU GCC for ARM. We are not utilizing any OS (such as real time OS), but are actually coding everything by hand, which gives us full control and minimal overhead.

quick read, and i think you should not compile it on your normal pc, but on an ARN based one..

---

### Post by sitec on 2007-09-13
thanx for fast answer.

however, i have already installed 'build-essential' package. and arm-elf-gcc is still missing...

I need to compile firmware for embeded device (openpcd) using arm proc.
so i need to compile it on my pc and upload it to the device...

---

### Post by st14n on 2007-11-24
> **sitec said:**
> thanx for fast answer.

however, i have already installed 'build-essential' package. and arm-elf-gcc is still missing...

I need to compile firmware for embeded device (openpcd) using arm proc.
so i need to compile it on my pc and upload it to the device...

You can install the GNU ARM toolchain, but I believe you must compile it on your own. [This page]("http://www.doctort.org/adam/nerd-notes/getting-started-with-the-olimex-sam7-p256.html") describes one way of installing it.

---

