---
title: "Suspend to RAM / Hibernate help on iMac G5"
date: 2010-02-15
forum: Apple Hardware Users
---

### Post by mjwalfredo on 2010-02-15
I got a new toy today, it's an iMac G5 that wouldn't boot up anymore.  I slapped Karmic Koala for PowerPC on the disk and the machine works quite well!  The only problem I have is with getting it to suspend / hibernate.


When I select suspend from the Gnome menu, the screen saver shows and the user is locked out (must enter password to get back to desktop).  It never tries to sleep and I don't see any messages in the logs.

When I select Hibernate from the Gnome menu, the screen goes black but the system never shuts down.  I have to turn it off manually at that point.


I read about pbbuttonsd and have been trying to get that working for me but no dice with that either.  Here is the output I get from pbbcmd:

```
mark@whiteimac:~$ pbbcmd query SLEEPSUPPORTED
ERROR: Problems with IPC, maybe server is not running.
```

Any ideas?

---

### Post by mjwalfredo on 2010-02-15
Update:  pbbuttonsd is not running on the iMac.  When I start it up, it complains that "/dev/pmu does not exist" and exits immediately.  I do not have /dev/pmu or /dev/abd on the machine.  Should I have those two devices or not?

---

### Post by linuxopjemac on 2010-02-16
I don't exactly know how it works, but you might want to compile pbbuttonsd with pmud enabled. I even don't know if pbbuttonsd is working on imacs, it was written for laptops.

[http://sourceforge.net/projects/apmud/](http://sourceforge.net/projects/apmud/)

for compilation pbbuttonsd:
./configure LAPTOP=<model> <other options>
Following models/families were supported:

LAPTOP=[POWERBOOK | powerbook | pb | PB]
    Apple PowerBooks or iBooks, all models.
LAPTOP=[MACBOOK | macbook | mb | MB]
    Intel based Apple MacBooks or MacBook Pros, all models.
LAPTOP=[I386 | i386]
    Generic support for Intel based laptops. Up to now support for powermanagement and specific laptop features is missing but it's also up to you to push this tool forward. 

Additional modules could be activated at compile time by calling the configure script with the option --with-<MODULE>:

pmud: 	Additional code will be integrated in PBButtonsd to use pmud as low level power manager. Normally PBButtons will do all necessary jobs by its own, but for special applications it could make sense to keep pmud running. In this case PBButtons must be compiled with pmud support to cooperate and don't conflict with it. Compiled with pmud support PBButtonsd uses pmud to trigger sleep mode and release cover control. If the machine went to sleep after closing the lid would be the responsibility of pmud then.

[http://pbbuttons.berlios.de/projects/pbbuttonsd/doc.html#install](http://pbbuttons.berlios.de/projects/pbbuttonsd/doc.html#install)

---

### Post by mjwalfredo on 2010-02-16
After reading your post and some other research, I have come to the conclusion that pbbuttons and pmud are not designed for the iMac and I should probably approach the suspend problem from a different angle.

So I am trying to figure out why suspend does not do anything at all.  If I run "sudo pm-suspend" nothing happens.  The only log file that even changes is auth.log showing that "sudo" was executed by my user id.

No information comes back from pm-is-supported --suspend either.

Do you think I might be missing some needed packages?

---

### Post by linuxopjemac on 2010-02-16
[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/189851](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/189851) ?

what happens if you do:

/usr/lib/hal/hal-system-power-pmu sleep

Edit: you don't have /dev/pmu :( it won't work...

---

### Post by linuxopjemac on 2010-02-16
If /dev/pmu is not present, you might want to add it yourself:

> Ok i have a fix for this o so very annoying problem all you have to do is open the following:

/etc/udev/makedev.d/50-udev.nodes
now scroll down to the bottom of this file and type:
pmu

yes its that easy it should now look something like this:
-----------------------------------------------------------------------------------------------------------

# These device have to be created manually
tty1
tty2
tty3
tty4
tty5
tty6
loop0
loop1
loop2
loop3
loop4
loop5
loop6
loop7
parport0
parport1
parport2
parport3
net/tun
ppp
console
null
zero
pmu
-----------------------------------------------------------------------------------------------------------
Enjoy and thanxs for your input if i didnt read your posts i dont think i would have figured it out. from [here]("http://www.yellowdog-board.com/viewtopic.php?p=9599")

---

### Post by mjwalfredo on 2010-02-16
Thanks for the suggestions linuxopjemac, they are keeping me from getting too discouraged with this iMac.  I'll try these out when I get home from work.  I really hope I can get this working as this iMac is a sweet little machine.  As a backup option I was thinking about buying a copy of OS X for it since the original disks are missing.  However, I cannot find an older version of OS X for a cheap price anywhere.  It would be much better to get Ubuntu working anyway :)

---

### Post by linuxopjemac on 2010-02-16
If Ubuntu doesn't satisfy your needs, I am pretty sure Debian Lenny will. It has better OOTB support for PowerPC.

---

### Post by mjwalfredo on 2010-02-17
Well, it turns out that the iMac G5 does not use the PMU but rather it uses something called SMU (System Management Unit) and it is not well supported by the PowerPC kernel.

Unfortunately, it sounds like suspend, hibernate, etc will not ever be supported in Linux.  I hope this post helps someone from spending as much time as I have on getting it working.

The latest info I could find on the subject is a year old and can be found here:  [http://wiki.debian.org/iMacG5]("http://wiki.debian.org/iMacG5")

---

### Post by linuxopjemac on 2010-02-17
I didn't know that, interesting link...What a shame that SMU is built in. I also can't find anything to support such a unit.

What are you going to do about it ? Buy OSX ?

---

### Post by mjwalfredo on 2010-02-17
> **linuxopjemac said:**
> I didn't know that, interesting link...What a shame that SMU is built in. I also can't find anything to support such a unit.

What are you going to do about it ? Buy OSX ?

Unfortunately, yes I think I will buy OS X or aquire it from another "source" ;)     I'd really love to run Ubuntu or Debian on the machine but I wanted to use this machine in either the bedroom or the living room for browsing the web and watching videos and I think the ability to suspend to RAM is something I would defintely want.  I don't want to waste electricity and I don't want to have to wait for it to cold boot everytime I want to check my email.

If I decide to repurpose this machine later on I may switch back to running Linux on it but for now OS X it is.  Thanks for the help by the way.

---

