---
title: "Need to update kernel to get &quot;.config&quot;"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by khanoftartary on 2008-01-04
Hey all,

   I'm trying to install a program on my new Fiesty system that says I need a recent kernel. I figured that one would have come with the installation, but it says that the command **ls /lib/modules/`uname -r`/build** ought to yield both **.config** file, and **include** directory. I have**include**, but I don't have **.config**. If it helps, I also get **arch**, **block**, **crypto**, **drivers**, **fs**, **init**, **ipc**, **kernel**, **lib**,** Makefile**, **mm**, **Module.symvers**, **net**, **scripts**, **security**, **sound**, **ubuntu**, and **usf**. Can anyone give me instructions for how to fix this? Keep in mind that 1: I don't know what most of the above things mean, and 2: My knowledge base in terminal is about equivalent to a three-year-old, so if you're going to give terminal instructions, please be as specific as possible. 

Thanks!

---

### Post by ~LoKe on 2008-01-04
Which program?

Also...try:
> ls -la /usr/src/linux-headers-`uname -r`|grep .config
In the terminal.

---

### Post by khanoftartary on 2008-01-04
ndiswrapper (which explains why I can't just use synaptic and ignore the tarball, I don't have internet access on my Ubuntu machine). And the command you gave yielded **-rw-r--r-- 1 root root 83234 2007-04-14 23:23 .config**, and I have no idea what that means or how to use it. Rember, I don't know anything when it comes to terminal, and I'm pretty new to Ubuntu, though I have used Fedora and Suse in the past. Thanks for the effort though!

---

### Post by ~LoKe on 2008-01-04
> **khanoftartary said:**
> ndiswrapper (which explains why I can't just use synaptic and ignore the tarball, I don't have internet access on my Ubuntu machine). And the command you gave yielded **-rw-r--r-- 1 root root 83234 2007-04-14 23:23 .config**, and I have no idea what that means or how to use it. Rember, I don't know anything when it comes to terminal, and I'm pretty new to Ubuntu, though I have used Fedora and Suse in the past. Thanks for the effort though!

Basically that line tells you that you DO have the .config file that you were asking about. :)

Would you be able to download the tarball on the machine you're using now, then copy it over on a usb key or something?

---

### Post by khanoftartary on 2008-01-04
I already did that. I have the tarball, the problem is that the instructions for installation on it are already a bit cryptic, and when I try to use the commands they provide, I get massive amounts of errors. So, looking through the install and readme files, the only evidence I could find for what wasn't working was the absence of **.config** file. If I do have the file, then something else is wrong, and I really have no idea how to fix it.

---

