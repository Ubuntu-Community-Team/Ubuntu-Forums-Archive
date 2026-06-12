---
title: "I have no sound on my HP tx2000 with Gutsy"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by temp0 on 2008-03-23
hi everyone, I have only been using ubuntu for a few weeks - which means im a noob to linux.
I bought this new laptop a few day ago, it has sound on Vista but not in ubuntu.
and i ve done some search for it and i got this website:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

I have tried method b and c

but, on both method, when i typed in : ./configure --with-cards=hda-intel

it gives me that:

checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

and i dont know how to check my sound card details, the detail i can only get is from the device manager:

**Vendor:** nVidia Corporation
**Product:** MCP51 High definition Audio
**OEM Vendor:** Hewlett-Packard Company
**OEM Product:** Unknown (0x30e5)

Could anyone help me out there??
Thanks in advance...

---

### Post by diablo75 on 2008-03-23
Open a terminal windows and type in:

```
sudo apt-get install linux-ubuntu-modules-2.6.22-14-386
```

And then...

```
sudo modprobe snd-hda-intel
```

You should have sound after that.

Found the solution [here]("http://ubuntuforums.org/showthread.php?t=585909").

---

### Post by rajb1 on 2008-06-30
after typing this in:
sudo apt-get install linux-ubuntu-modules-2.6.22-14-386
 
output is:
personal@hp:~$ sudo apt-get install linux-ubuntu-modules-2.6.22-14-386
[sudo] password for personal: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-ubuntu-modules-2.6.22-14-386
personal@hp:~$

---

### Post by diablo75 on 2008-07-01
> **rajb1 said:**
> after typing this in:
sudo apt-get install linux-ubuntu-modules-2.6.22-14-386
 
output is:
personal@hp:~$ sudo apt-get install linux-ubuntu-modules-2.6.22-14-386
[sudo] password for personal: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-ubuntu-modules-2.6.22-14-386
personal@hp:~$

It appears you are trying to install a kernel module that is no longer supported (out of date, #2.6.22-14).  We need to see what version you are using.  To do this, type this into a terminal window:

```
uname -r
```

The output will say something like:

```
username@ubuntu:~$ uname -r
2.6.24-19-generic
```

In my case, I'm using version 2.6.24-**19**.  So if I were you, I would type in the following command:

```
sudo apt-get install linux-ubuntu-modules-2.6.24-**19**-386
```

This may not exactly be the case, but depending on the output you get from the uname -r command, you can alter this command to download the correct modules.

Good luck!

---

