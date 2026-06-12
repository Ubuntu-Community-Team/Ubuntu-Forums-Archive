---
title: "linux-restricted-modules-2.6.20-16-server  WHERE???"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by brooksbp on 2007-06-21
Just did a fresh Ubuntu Server 7.04 install. Installed packages necessary to run GNOME and X and all that.  Went to get drivers for the nVidia card on the machine... System -> Administration -> Restricted Drivers Manager and...

I get this error message:

```
You need to install the package

linux-restricted-modules-2.6.20-16-server

for this program to work
```

So went through apt-get... found nothing. Went to synaptics, all repos... found nothing. Did a google search... found NOTHING.  Where the hell is this package and why hasn't anyone else had a problem with this (assuming this because of no results from the Google search)?

Thanks for your help.

---

### Post by Jimmyfj on 2007-06-21
You find that through aptitude. Go to the Not Installed section and seek it out

---

### Post by Bachstelze on 2007-06-21
There are no restricted-modules packages for the server kernel. Either build them yourself or use a generic kernel.

---

### Post by brooksbp on 2007-06-21
How can I build them? Why aren't they already built?

---

### Post by mikewhatever on 2007-06-21
Could it have been linux-restricted-modules-2.6.20-16-generic, because the package ending with -server is not there.
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules-2.6.20-16&searchon=names&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules-2.6.20-16&searchon=names&subword=1&version=feisty&release=all)
I think it has to fit your kernel version, so check that with 'uname -r' command.

---

### Post by brooksbp on 2007-06-21
Right. So how do I build the server pkg

---

### Post by zer0fill on 2007-06-27
> **mikewhatever said:**
> Could it have been linux-restricted-modules-2.6.20-16-generic, because the package ending with -server is not there.
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules-2.6.20-16&searchon=names&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules-2.6.20-16&searchon=names&subword=1&version=feisty&release=all)
I think it has to fit your kernel version, so check that with 'uname -r' command.

I'm having the same issue now. Unfortunately, -generic isn't the same as -server (still asks for the -server version). I'm just going to "downgrade" until the -server version is created.

---

### Post by dabbner on 2007-08-26
I am having the same issue.  Did anyone ever find a resolution to this issue?

---

### Post by rayde on 2007-08-29
same question...  anybody care to give some instructions on either A) how to build these restricted modules or B where to find pre-built modules?
:confused:

---

### Post by slew on 2007-09-28
> **zer0fill said:**
> I'm having the same issue now. Unfortunately, -generic isn't the same as -server (still asks for the -server version). I'm just going to "downgrade" until the -server version is created.

How does one 'downgrade?'

---

### Post by kajta on 2007-10-18
> **mikewhatever said:**
> Could it have been linux-restricted-modules-2.6.20-16-generic, because the package ending with -server is not there.
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules-2.6.20-16&searchon=names&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules-2.6.20-16&searchon=names&subword=1&version=feisty&release=all)
I think it has to fit your kernel version, so check that with 'uname -r' command.

I have the same problem and version is 2.6.20-16-server... I guess it should work.. or?

---

### Post by erbrecht on 2007-12-03
I have been looking at this for a while and I am currently using the generic kernel instead of the server kernel.  I did find these instructions for building the module

[http://blog.0xb.org/2007/05/ubuntu-server-kernel-and-nvidia-driver.html](http://blog.0xb.org/2007/05/ubuntu-server-kernel-and-nvidia-driver.html)

but I wasn't able to get the module to load properly (or at all).  Maybe one of you will have better luck with it.

---

### Post by Fooshnik on 2007-12-13
I don't know why it asks for that when it doesn't exist. You can get the nvidia driver installed on ubuntu server fairly easily by running the install script on Nvidia's site under their linux driver section. You may need to 'apt-get install build-essential' first as well as the kernel source. The script will build a new kernel then reboot, you should have it set to boot into console incase X fries.

---

