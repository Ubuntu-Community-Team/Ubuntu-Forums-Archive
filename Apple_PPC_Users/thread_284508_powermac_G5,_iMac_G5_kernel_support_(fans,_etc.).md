---
title: "powermac G5, iMac G5 kernel support (fans, etc.)"
date: 2006-10-25
forum: Apple PPC Users
---

### Post by stmiller on 2006-10-25
I have initiated a dialog with some folks who have @ubuntu.com email addresses to bring to the surface the problem of the PPC discs not supporting G5 machines with thermal support, among other problems. The main bug report here:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34723](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34723)

Has changed from 'importance: low' to 'medium.'

Also status of the bug has been confirmed. So hopefully there will be a fix, but with edgy already out the door pretty much, it will most likely be a kernel update later down the road to make the official fix from ubuntu.

---

### Post by Torrance on 2006-10-25
Thanks heaps stmiller. :D

---

### Post by mike_hore on 2006-10-25
Yes, many thanks from me too.  I've now subscribed to the bug so I can easily keep and eye on progress.

-- Mike.

---

### Post by stmiller on 2006-10-25
Looks like we have an Edgy fix. Look at the latest post at the bottom of the bug report:

"Can you post to the forum thread that I've got a workaround for the stock Edgy installs?  Clearly something is missing in the system to correctly load the right modules, but loading all the thermal drivers along with functioning cpu scaling seems to have solved it for me:

[https://launchpad.net/bugs/34723](https://launchpad.net/bugs/34723)

"

> On a stock Edgy install, this seems to have solved the problems:

# As root, type:
apt-get install powernowd
cd /lib/modules/$(uname -r)/kernel/drivers/macintosh
ls | cut -d. -f1 | xargs -n1 modprobe

Seems that what's missing in Edgy is the correct knowledge to load the right modules.


> To make these module load on bootup, I also did this as root:

lsmod | cut -d" " -f1 | grep windfarm >> /etc/modules

A better fix is for udev or similiar to notice the hardware and take the
right actions.

---

### Post by stmiller on 2006-10-25
And the bad news:

> As I said, the modules are there and just need to be loaded. The installer is supposed to configure the default /etc/modules file to force load these thermal modules.

Not something I can fix in the kernel. This will all be fixed in the next Ubuntu release, because the new kernel contains hotplug support for these modules.

---

### Post by thornomad on 2006-10-26
That's real interesting -- I noticed that when I ran a live CD of edubuntu on my PowerMac G5 before installing it on an old iMac ...

LOTS of whirring fans!

But, to be honest, I am not ready to turn my new Mac into a Ubuntu system ... I am too busy converting all my old PCs to Ubuntu.

---

### Post by stmiller on 2006-10-26
And to make edgy kernel matters even worse, ubuntu is not using the 2.6.18 kernel, which has MASSIVE improvements for powerpc hardware. And also the biggest aspect of being a realtime kernel.

[http://linux.slashdot.org/comments.pl?sid=202818&threshold=1&commentsort=0&mode=thread&cid=16592928](http://linux.slashdot.org/comments.pl?sid=202818&threshold=1&commentsort=0&mode=thread&cid=16592928)

I wish the ubuntu team had waited to release edgy with the new kernel. And ubuntu doesn't do kernel updates, so it will be May 2007 before ubuntu has the 2.6.18 kernel on a cd. Oh well.

---

### Post by RoadTripDK on 2006-10-27
I tried 'sudo -s ls | cut -d. -f1 | xargs -n1 modprobe' but got the following error message:

> /bin/ls: /bin/ls: cannot execute binary file

A listing of modprobe usage comes afterwards.

Anyone have an idea what is wrong?

---

### Post by stream303 on 2006-10-27
Just try sudo -s to get into a root shell prompt.

Once there, issue your commands.

---

### Post by Torrance on 2006-10-28
This worked fine for me:

```
 sudo -s
 cd /lib/modules/$(uname -r)/kernel/drivers/macintosh
 ls | cut -d. -f1 | xargs -n1 modprobe
 lsmod | cut -d" " -f1 | grep windfarm >> /etc/modules
```

You'll get a few errors, but these are fine: they are just the fan modules for other macs.

I would rather have recompiled the kernel and enable the thermal management in the kernel, but unfortunately there is some bug with Edgy that is stopping the compiling of kernels on ppc (a new kernel would also have mean 24 bit start-up splash screens ;) ).

---

### Post by RoadTripDK on 2006-10-28
Cheers.

24 bit start-up splash screens? That could be what I get already at startup. Man does it suck big time. All pixelated and stuck in the upper left two thirds of the screen.

---

### Post by Torrance on 2006-10-28
Then you're probably getting 8 bit or something. Mine looks terrible, as is purple and white, and stuck in the top right corner. I guess it's not that important - but I like things a bit more polished.

---

### Post by wagerrard on 2006-10-31
Are the late-model Rev C iMacs included in this discussion? Previous discussion, here and elsewhere, didn't deal with those machines.

---

### Post by gwon on 2006-10-31
I've got the last iMAc G5 before the iSight was added. Dunno what revision that is.

Anyway, I've never had a working install, until now.

Edgy+This Thread = Awesome.

---

### Post by wagerrard on 2006-10-31
> **gwon said:**
> I've got the last iMAc G5 before the iSight was added. Dunno what revision that is.

Anyway, I've never had a working install, until now.

Edgy+This Thread = Awesome.

The Rev. C iMacs are the iSight models and the last revision before the switch to Intel.

As I understand it, the fan control code for the earlier models was based on code from Darwin.  Since that project is apparently kaput, I wonder if we will ever see Linux work on those machines.

For what it's worth, I just grabbed an FC6 install CD and booted my 20-inch iMac with it.  Same result:  black screen, screaming fans.

---

### Post by stmiller on 2006-10-31
There is not any notion of importance from the ubuntu ppc team to find or fix any of these problems. When I was emailing one ubuntu ppc team guy of the problems, he said, 'Oh that only effects iMacs. My Powermac works fine.' As if he could care less.

But the gentoo ppc folks are trying hard, and are real people you can communicate with. I would say perhaps try contacting them through the gentoo forum, or irc:

[http://forums.gentoo.org/viewtopic-t-497222.html](http://forums.gentoo.org/viewtopic-t-497222.html)

Good luck.

---

### Post by stream303 on 2006-10-31
So did the workaround fix the issue for you Rev-C iMac owners?

It worked great on my G5 Rev-A 20" iMac.  I just let the fans scream during install.  Got faked out when booting from hd for the first time and things were quiet for a few minutes until the fans kicked in again.

Applied the necessary commands in this thred from the terminal and presto!  Normal operations.

Would like to have seen it in the kernel, but loading the module manually beats waiting for the next release and crossing fingers. :)

---

### Post by mike_hore on 2006-11-04
I can also confirm this works fine on my Rev A machine, which is at last nice and quiet  :-)

--  Mike.

---

