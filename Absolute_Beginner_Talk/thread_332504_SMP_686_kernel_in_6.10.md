---
title: "SMP 686 kernel in 6.10"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by fo3 on 2007-01-06
I had to reinstall everything after changing mobo and CPUs, (constant crashes and lockup after changover)
Now I can't get SMP working, system monitor has just one cpu showing (I'm running dual p3s).  I swear I had two showing before installing nvidia drivers, now no matter what kernel I install, after reboot uname -a/-r just shows 2.6.17-10-386.
I've tried the smp kernel for the package manager, and apt-get install linux-686-smp, both still don't make a difference. I reinstalled the generic kernel and still no smp, the same 386 kernel shows up in uname 
Any help please?
I know i've had this system all set up before about 3 months ago, but nothing seems to work now.

---

### Post by zgornel on 2007-01-06
The generic kernel has SMP enabled. Do a *cat /proc/cpuinfo* and see if there are 2 processors reported.

---

### Post by fo3 on 2007-01-06
thanks for the reply, there's only one cpu.
I've done that already to identfy that there is a problem here.
not only that but I've got a 386 kernel, not a 686 one

---

### Post by zgornel on 2007-01-06
> **fo3 said:**
> thanks for the reply, there's only one cpu.
I've done that already to identfy that there is a problem here.
not only that but I've got a 386 kernel, not a 686 one
Hold on. The generic kernel is not 386 nor 686. What kernel exactly are you using when only one cpu is reported ?

---

### Post by fo3 on 2007-01-06
I think something occured when I used a nvida driver installer or something else I did.  I did mention that I thought I saw 2 cpus there originally, and that the only thing I did was install the nvidia driver.  
Somehow I ended up with a 386 kernel, and even trying to install a 686 or generic kernel again I couldn't get rid of it.  Eventually the whole OS was hosed when I tried to install an older smp kernel (which got rid of a lot of other things like the nvidia driver and killed the system). 

 From reading around it must have been that grub had multiple kernels and was keeping the 386 one as first priority, but I never got around to working out how to get to grubs menu because of the whole OS being lost.

Now it's all good, from default install with the generic kernell both cpus are there and now I'm installing nvidia drivers manually from their site

---

### Post by fo3 on 2007-01-06
ha, this is what this installer I used for nvidia drivers did!
from some other thread :
> **K.Mandla said:**
> For some reason, you seem to still be using the generic kernel. The nvidia drivers need the 386 kernel, but it's odd that they weren't installed when you pulled in the nvidia-glx driver. :-k

Try this:

```
sudo aptitude install linux-386
```
Then reboot, and hopefully it should work. [-o< If you get a boot options screen at startup, make sure Grub is loading the 386 kernel.
and I've had no luck installing nvidia drivers manually, get errors because they don't recognise the generic kernel.
Is there any work around to have both the smp kernel and nvidia drivers?

---

### Post by konst88 on 2007-01-06
Post you menu.lst
```
cat /boot/grub/menu.lst
```

---

### Post by fo3 on 2007-01-06
crap, I'm about to give up here.
After just installing samba and opera (plus libqt3-mt dependancy), the whole thing is crashing again after 30sec - 1 min (lock up).
I restarted in failsafe mode, managed to install all updates.  It all looks good after that
Then 5 - 10 min later everything is crashing again, 15 min later a lock up.
from another forum, here's the story after I built this PC:
[QUOTE=fo3]
I just bought 1ghz P3 CPUs, one with a S spec of sl52r, the other with sl5dv, now my PC crashes all the time.
The BIOS detects them OK, the OS detects them, but just using simple apps and browsers results in a crash after 15 min, the programs close themselves at first, then the system locks up.  

edit: just then opera just closed by itself losing all settings, so  I loaded firefox, 5 min later the whole system freezes and needs to be reset.
However problems go away when re - installing the 866Mhz CPUs, so it doesn't look like mobo, ram, video or anything else.

Someone told me the stepping is the same and they should work, the seller told me they were working fine in his old dual system.  I don't understand how everything would detect OK, and then run for a short while before crashing, temps are under 50C as well,[/QUOTE]
full thread here 
[http://forums.2cpu.com/showthread.php?p=674486#post674486](http://forums.2cpu.com/showthread.php?p=674486#post674486)

This PC was running dual mode for hours, running two instances of prime in windows XP with no faults before giving ubuntu another try.

through all the above in this thread (only running on one CPU), it never crashed.
As soon as I'm running on both CPUs with just samba and opera installed (and a failed attempt at nvidia drivers), ubuntu keeps crashing, but I've proven it's not hardware by running on windows without problems.



Late edit:


Ok it looks like I did something to the ram sticks ot mobo slots when changing CPUs.  I tried a few other distros overnight, some worked, some wouldn't install.  Found errors on memtest so something went wrong when changing the CPUs.

---

### Post by fo3 on 2007-01-07
ubuntu still won't get past the load screen, in fact even with previous problems it would install, now it's even worse with the bad stick removed.  Either a blank screen after booting and chosing install, or a page of errors.  I went out and bought a PSU, raided the supplies and fit new ram, burnt a new CD (all md5 checks are fine) but it seems I'm going backwards.

edit:
Nevermind, ubuntu will just not install on this PC at all now.  I've changed dvd rom, cable, psu, media, ram and still no progress so I've given up.  Mepis and Debian install with no problems though :confused:  I'm just going to stick XP back on and try another PC for ubuntu

---

