---
title: "eth0 disappeared"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by dupa on 2006-10-24
I had a ethernet adapter on eth0
And a common ps2 mouse correctly working

I was trying to disable ipv6 (for some problems with my router) and I did some changes (following some online threads) to the files:

```

/etc/modules
/etc/hosts
/etc/resolv.conf
/etc/modprobe.d/*

```

I rebooted the system but ipv6 was still active.
I did many attemps, but when I rebooted the system, ipv6 was always active. ](*,) 

The last time i had try to execute some commands from the shell, i can remember to had executed "rmmod", "lsmod", "ifconfig" and stuff like that, but I DIDN'T manually changed any files apart the files listed above.

I rebooted ubuntu and... "eth0" disappeared from my system!!! and the ps2 don't work anymore! when X starts the mouse is fix at the center of the screen.

At first time i supposed it was an hardware problem, but rebooting in windows, my mouse and lan adapter works fine!

I tryed to boot with ubuntu live, and also on ubuntu live my eth0 and ps2 mouse, works!!

I restored all the file (listed above) I had manually edited to the original version (i'm ABSOLUTELY SURE of this, i did a backup the original version.. and i restored it, i had check one thousand of times that the stuff inside them is reset to the original...)

On ubuntu desktop live and on my installed ubuntu (before having this problem)

```
lspci
``` lists my lan adapter
```
dmesg | grep eth0
``` shows some rows of messages about my eth0
```
ifconfig
``` shows my eth0

Actually on my installed ubuntu:

```
lspci
``` lists my lan adapter
```
dmesg | grep eth0
``` SHOWS NOTHING
```
ifconfig
``` DON'T show my eth0

I finally repeat: I have restored ALL the files i manually changed, the only things i did the last time trying to disable ipv6 was to executed some commands like "rmmod", "lsmod" "ifconfig".

Please can someone help me? I don't want to completely re-install Ubuntu. i want to understand how restore it ](*,) 

PS: after doing this stupid thing to my ubuntu i discovered that to disable ipv6 i just need to add the simple line "blacklist ipv6" to the "/etc/modprobe.d/blacklist" file

---

### Post by Tamil on 2006-10-24
See [Problem with net connection](http://www.ubuntuforums.org/showthread.php?t=266334)

---

### Post by dupa on 2006-10-24
> **Tamil said:**
> See [Problem with net connection](http://www.ubuntuforums.org/showthread.php?t=266334)

it seems that we have the same problem ](*,) 
right?

---

### Post by Tamil on 2006-10-24
> **dupa said:**
> it seems that we have the same problem ](*,) 
right?Yes.

Did you try the suggestions by [dannyboy79](http://www.ubuntuforums.org/showpost.php?p=1605474&postcount=20)?

Did you install any programs today/recently?

---

