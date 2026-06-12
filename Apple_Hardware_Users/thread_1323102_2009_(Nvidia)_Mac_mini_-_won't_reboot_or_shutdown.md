---
title: "2009 (Nvidia) Mac mini - won't reboot or shutdown"
date: 2009-11-11
forum: Apple Hardware Users
---

### Post by youbuntu on 2009-11-11
Hi GNU people!. I own a 2009 Mac mini, and I have an issue (the only issue, mind). I wish to install Karmic on the Mac - when I run the 9.10 x86 liveCD, all works perfectly, *except* for reboot & shutdown. The disc is spat out as per usual, and I'm asked to press [enter] to confirm, but the Mac mini just hangs at a black screen (it is definitely still on, due to the while LED being lit up).

Has there been a patch for this issue yet?. I am dying to make free software my main OS, and gradually break my dependancy on Snow Leopard.

Many thank guys.

---

### Post by youbuntu on 2009-11-11
Noone yet? :(

I'm dying to get this Karmic installed, sorry, I shouldn't be so impatient; it's really not *urgent*, I am just wondering if there's a fix.

Have a great day, all.

---

### Post by linuxopjemac on 2009-11-12
what about the 32-bit version ? I have seen some problems with 64-bit.

---

### Post by lightsabersetc on 2009-11-12
I had the same problem on a deployment of the 32 bit version. I then used the alternate installer disc and it hangs at black screen on boot. I ended up installing with 9.04 disc and upgrading thru the upgrade utility.

---

### Post by linuxopjemac on 2009-11-12
I read this somewhere in the Ubuntu Apple forum:

> It should work fine because it has all the same system specs as the new macbooks, so the only thing that might not work is restarting. I would read the installing ubuntu on macbook 4"1, 5"1 guide, might not be the same for sounds either.

---

### Post by linuxopjemac on 2009-11-12
you can try to install Jaunty Jackalope and upgrade as was mentioned by lightsabersetc.
[https://help.ubuntu.com/community/Mac_mini3-1/Jaunty](https://help.ubuntu.com/community/Mac_mini3-1/Jaunty)

---

### Post by youbuntu on 2009-11-12
> **linuxopjemac said:**
> you can try to install Jaunty Jackalope and upgrade as was mentioned by lightsabersetc.
[https://help.ubuntu.com/community/Mac_mini3-1/Jaunty](https://help.ubuntu.com/community/Mac_mini3-1/Jaunty)

Yes, but it would be preferable not to install 64 bit - I hear there are issues with doing so, such as software incompatibilities etc, driver problems and more. Am I right?.

---

### Post by linuxopjemac on 2009-11-12
I don't know.

---

### Post by youbuntu on 2009-11-14
Okay, so now after installing & updating x86 Karmic, it DOES shutdown but DOES NOT RESTART... but it also locks up every now and again, the most recent occurrence of which left me at a COMPLETELY black screen, after having logged out.

Here is my syslog file:

---

### Post by pelle.k on 2009-11-14
> Okay, so now after installing & updating x86 Karmic, it DOES shutdown but DOES NOT RESTART..
Yes, Karmic doesn't reboot. There's no known solution as far as i can remember. It's been reported that reboot can be achieved with other kernel versions than the one in Karmic though.
> but it also locks up every now and again, the most recent occurrence of which left me at a COMPLETELY black screen, after having logged out.
I'm pretty sure this is because of the non-free Broadcom wireless drivers (without having looked at the kernel logs). It's a known "bug". There's little the linux devs can do about it as broadcom is writing this (closed source) driver i'm afraid. But maybe broadcom will release an updated version that may be released to karmic's backport repositories.

---

### Post by robertbub on 2010-06-06
Bump.

I assume that this still hasn't been resolved?  It's a bit annoying not knowing the right time to hard-power-down when restarting.

---

### Post by Yako no Kai on 2010-06-07
> **pelle.k said:**
> Yes, Karmic doesn't reboot. There's no known solution as far as i can remember. 

Karmic reboots fine on the mac mini.  Add this to your kernel boot options:

```
reboot=pci
```

That did the magic for me.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

The Karmic installer won't do this, so you have to remember to either hit ESC and modify the boot line or just shut down, but it's easy to set this once you get your system running.  Test it out on one boot, then reboot and if it works for you, make your changes to the grub config file.  Put your changes in the automagic kernels area to make them stay after you update your kernel.

---

### Post by pelle.k on 2010-06-07
> **Yako no Kai said:**
> Karmic reboots fine on the mac mini.  Add this to your kernel boot options:

```
reboot=pci
```

That did the magic for me.

AFAIK i did test that on my mac mini (late 2009), so that's strange. In any case, I should mention that lucid doesn't have this issue.

---

