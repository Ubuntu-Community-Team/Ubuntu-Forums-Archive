---
title: "Just Installed - A Couple Problems"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by Hexx on 2006-07-10
Well I just installed Ubuntu 6.06 today (dual booting with WinXP) after playing around with the live CD for a few days, and while I like it so far, I've already run into a couple problems.

My first problem is when I'm attempting to set up my Lucent Winmodem (yes, I'm on dialup...). Following the instructions of the wiki, I attempt to put my file "10-local.rules" in /etc/udev/rules.d/, but when I try to do this, I get an error telling me I don't have permission to do that. Must this be done via a sudo command in Terminal? If so, what's the command?

My second problem comes when I'm trying to uninstall programs. No matter what I try to uninstall, I get an error. For example: "'gnome-games' is not available in any software channel. The application might not support your system architecture." I get this error with anything I try to uninstall and it's baffling me.

Any help?

---

### Post by Paerez on 2006-07-10
1) the command to copy a file is "cp" so, if you have 10-local.rules in your home directory, you would do:
```
# sudo cp ~/10-local.rules /etc/udev/rules.d
```
the "~/" means "my home directory"

2) What kind of computer do you have?
Run this:
```
# cat /proc/cpuinfo
```
and paste it to us.

---

### Post by steve.horsley on 2006-07-10
2: What are you trying to uninstall, and how? I've never seen that message.

---

### Post by Hexx on 2006-07-10
> **Paerez said:**
> 1) the command to copy a file is "cp" so, if you have 10-local.rules in your home directory, you would do:
```
# sudo cp ~/10-local.rules /etc/udev/rules.d
```
the "~/" means "my home directory"

2) What kind of computer do you have?
Run this:
```
# cat /proc/cpuinfo
```
and paste it to us.

1) Thank you for the command, it worked perfectly!

2) I'm running on some seriously old hardware:

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 6
model name      : Celeron (Mendocino)
stepping        : 5
cpu MHz         : 501.219
cache size      : 128 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr
bogomips        : 1003.18
```

I hope I can get this figured out. Ubuntu is the first time I've tried anything with Linux.

---

### Post by Hexx on 2006-07-10
> **steve.horsley said:**
> 2: What are you trying to uninstall, and how? I've never seen that message.

I'm just trying to uninstall things like Evolution, things I'll never use. I'm doing it via the "Add/Remove" section under the Applications menu.

---

### Post by Paerez on 2006-07-10
ok I think the software channel stuff may be related to your repositories. Could you paste in the file:
/etc/apt/sources.lst

---

### Post by Hexx on 2006-07-10
> **Paerez said:**
> ok I think the software channel stuff may be related to your repositories. Could you paste in the file:
/etc/apt/sources.lst

```

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

Thanks for your help, I really appreciate it. One thing I like about Ubuntu is the fact that the people here at this forum are so ready and willing to help noobs like me.

---

### Post by Hexx on 2006-07-11
Well it seems I've managed to fix the Add/Remove Software problem! Just needed to update the repository lists and stuff.

Thanks for your help.

---

### Post by Paerez on 2006-07-11
ah ok, I was going to suggest adding the "multiverse" and "universe" repositories to get extra programs, but you got it.

If you need help getting your ubuntu up and running, try this:
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

---

