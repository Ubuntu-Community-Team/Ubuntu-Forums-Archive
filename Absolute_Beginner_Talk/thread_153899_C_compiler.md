---
title: "C compiler?"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by bathwater on 2006-04-02
Does ubuntu 5.10 come with a C compiler?...or can i download one for it that has instructions on how to install it?...just wondering because I downloaded vmware player for virtual server and when i tried to install it said there wasnt a correct version or somthing but it asked if i wanted it to compile one and asked for the c compiler directory. Any assistance would be very helpful and appriciated.

---

### Post by tkiesel on 2006-04-02
Run this in a terminal and you're mostly set!

```
sudo apt-get install build-essential
```

---

### Post by bathwater on 2006-04-02
Thank You for that info..i did it and now it comes up with this when i try to install it...



None of the pre-built vmmon modules for VMware Player is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [no] yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Your kernel was built with "gcc" version "3.4.5", while you are trying to use
"/usr/bin/gcc" version "4.0.2". This configuration is not supported and VMware
Player cannot work in such configuration. Please either recompile your kernel
with "/usr/bin/gcc" version "4.0.2", or restart /usr/bin/vmware-config.pl with
CC environment variable pointing to the "gcc" version "3.4.5".


any clue on what that means or how to do it?

ps.sorry for asking so many questions.

---

### Post by Sutekh on 2006-04-02
You need to install the GNU C Compiler v3.4, which is what the kernel was built with.
```
sudo apt-get install gcc-3.4
```
Then before you can use it in preference over gcc-4.0 you need to do this
```
CC=gcc-3.4
export CC
```

---

### Post by bathwater on 2006-04-02
ok i did that now it says this...



None of the pre-built vmmon modules for VMware Player is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]


i swear if it isnt one thing its another...lol..sorry for being noobish but im trying to learn.

---

### Post by Harleen on 2006-04-02
You need to install the Linux kernel headers that fit to your installed kernel.
```
uname -r
``` will give you the version of your installed kernel. For me it's 2.6.12-10-k7. The package I'd have to install would be "linux-headers-k7". Just try ```
 sudo apt get install linux-headers-<last_part_of_kernel_version>
```

---

### Post by belikralj on 2006-04-02
I'm a bit of a newb my self and though I can't help extremly I was wondering whether it would be possible to even update his kernel? I mean a newer version is usually better and I'm sure I saw something like that in Synaptic.

Sorry I couldn't help. :-k

---

### Post by bathwater on 2006-04-02
Thank you all so veryu much. I believe that worked..all i need to do now is download a pre-built virtual machine to try it out.

Thanks to all who replied again..they were all very helpfull.

---

