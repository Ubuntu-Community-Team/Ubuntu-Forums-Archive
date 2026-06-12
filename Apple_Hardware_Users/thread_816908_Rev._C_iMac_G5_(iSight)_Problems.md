---
title: "Rev. C iMac G5 (iSight) Problems"
date: 2008-06-03
forum: Apple Hardware Users
---

### Post by Cooner750 on 2008-06-03
Hello.

I've successfully installed Ubuntu alongside OS X on my Rev. C iMac G5, however I am having some problems with it.

&#8226; Fan control does not appear to be working at all. I'm using 8.04 and the **2.6.24-16-powerpc64-smp** kernel is installed, as far as I know this kernel should include thermal control support, correct?

&#8226; This is a minor thing, but when booting, the splash screen is blue colored and generally appears very garbled.

&#8226; Video seems sluggish in Ubuntu even with desktop effects disabled, but I assume this is due to the limited support for video hardware because of closed source drivers.
[B]
Edit: Some more info[/B]
  Model Name:	iMac G5
  Model Identifier:	PowerMac12,1
  Processor Name:	PowerPC G5 (3.0)
  Processor Speed:	1.9 GHz
  Number Of CPUs:	1
  L2 Cache (per CPU):	512 KB
  Memory:	1.5 GB
  Bus Speed:	633 MHz
  Boot ROM Version:	5.2.6f1

---

### Post by stream303 on 2008-06-03
> **Cooner750 said:**
> 
• Fan control does not appear to be working at all. I'm using 8.04 and the **2.6.24-16-powerpc64-smp** kernel is installed, as far as I know this kernel should include thermal control support, correct?

Drat.  I'm not sure that the Rev-C was covered in the 2.6.24 kernel, although I may be wrong.  On my Rev-A, the thermal control is supported after the first reboot, but during install the fans scream.  This issue was reported and is being looked into by Ubuntu devs for the next respin, ala 8.04.1.  Currently you just have to suffer through it during install.

You may want to check or run Debian Lenny-testing or Sid-unstable and see if thermal control has already been implemented for the Rev-C.  Or perhaps see if the 2.6.25 kernel covers it, in which case you could compile your own kernel, or maybe find a distro that uses it now, ie Fedora or possibly the upcoming new version of OpenSuse?  

Frustrating I know, screaming fans are a showstopper.  Fortunately devs are aware and the hope is that it would be included if possible with 8.04.1 due out next month, but you never know.

> • This is a minor thing, but when booting, the splash screen is blue colored and generally appears very garbled.

Splash screens have never really looked good on PPC for me, so I just do away with it by using the "nosplash" kernel parameter either at the second-stage yaboot boot: prompt, and if that works, I make it permanent in my /etc/yaboot.conf followed by a sudo ybin.  Try this by hitting -tab- at the yaboot: boot prompt:

```
Linux nosplash
```

If that works to just show dmesg boot messages rather than the splash screen we can go further... as long as screaming fans don't make it a moot point. :)

> • Video seems sluggish in Ubuntu even with desktop effects disabled, but I assume this is due to the limited support for video hardware because of closed source drivers.

I believe that the Rev-C uses ATI card, so you can perform some tweaks to your /etc/X11/xorg.conf file manually and see how that goes.  Check out the faq for some nice hints:

[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)

You just might have to hang in just a month or so to get some sort of PPC distro working with thermal support for the Rev-C ...

---

