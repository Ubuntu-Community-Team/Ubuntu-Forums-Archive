---
title: "Upgrading and the Internet (and more)"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by Drok on 2007-08-05
I have noticed a couple of threads dedicated to upgrading to 7.04, I just started with Linux, but I'm pretty much a windows power user, with a great understanding of how systems work, I just set up a LAMP server off the server CD, got it up and running, and it works great, but I was curious if there was a command line utility that is similar to the package managers on the desktop distro. ( just want to make sure my apache my SQL and PHP stay up-to-date). I was hoping that this could be accomplished over the internet, as my server no longer has a CD-ROM... =(

I was also wondering how to copy files over SSH. I set up SSH and over puTTY I have some of the commands down, but how do I transfer files from my windows computer to the server, I currently use filezilla, but I was curious as to how I can do it through puTTY, I don't think you can, but I was just curious if I could...

Thanks in advance for your assistance.

** I just noticed, [https://help.ubuntu.com/7.04/add-applications/C/advanced.html#apt](https://help.ubuntu.com/7.04/add-applications/C/advanced.html#apt), contains information on how to upgrade and install packages **

---

### Post by enderwig on 2007-08-05
You can transfer files over ssh by scp.  Type
```
man scp
```
in a terminal for more info on scp.

---

### Post by Dr Small on 2007-08-05
If you want to copy files from windows to ubuntu over ssh, use a scp client, found on PuTTY's download page called PSCP.
[http://the.earth.li/~sgtatham/putty/latest/x86/pscp.exe](http://the.earth.li/~sgtatham/putty/latest/x86/pscp.exe)

That should copy files for you ;)

Dr Small

---

### Post by Drok on 2007-08-05
Sweet thanks! I will fiddle!!

---

