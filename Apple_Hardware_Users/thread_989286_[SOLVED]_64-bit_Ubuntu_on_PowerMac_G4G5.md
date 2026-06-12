---
title: "[SOLVED] 64-bit Ubuntu on PowerMac G4/G5"
date: 2008-11-21
forum: Apple Hardware Users
---

### Post by IQRules on 2008-11-21
Can we run 64-bit version on G4/G5?
I have a PowerMac MDD 1.25G, is it 64-bit capable?

Anyone has done that just single boot with 64-bit version w/o OSX installed?

---

### Post by tiresia on 2008-11-21
Your PowerMac is a 32-bit architecture, like every g4. 
Anyway also in a powerpc g5, at least in Ubuntu, only the kernel is '64-bit capable', applications ('user space') are 32-bit. In debian there are some binary packages for 64-applications, but the situation is still 'under development'

From the Gentoo Installation Handbook:
'You really only need 64-bit applications when you need more memory than a 32-bit userland allows, or if you do a lot of 64-bit number crunching. If you run applications that require more than 4GB of memory or you run scientific applications, you should choose the 64-bit userland. Otherwise, choose the 32-bit userland, as it is recommended by the Gentoo/PPC64 developers.'

[http://www.penguinppc.org/ppc64/](http://www.penguinppc.org/ppc64/)
[http://debian-ppc64.alioth.debian.org/](http://debian-ppc64.alioth.debian.org/)
[http://www.gentoo.org/doc/en/handbook/handbook-ppc64.xml?part=1&chap=2](http://www.gentoo.org/doc/en/handbook/handbook-ppc64.xml?part=1&chap=2)

---

### Post by stream303 on 2008-11-21
Not having or wanting OSX make the job even easier.

At the second stage boot: prompt hit TAB to stop the countdown.  There you will see a number of options.  Depending on the release, you can type in the 64bit option which would look something like

[list]
install-powerpc64
install64[/list]

Or something to that effect.

A cli-only version can be obtained by installing the server image.

The problem with the average desktop, is that the installer doesn't know about the specific video requirements, and the defaults in many cases don't work, or are so far out of range that they may shut down the screeen when it tries to protect itself.  Thus, you have to go back in and manually edit the /etc/X11/xorg.conf by hand, usually with vi.

This means that after installation, assuming everything else goes ok (such as having to modprobe ide-scsi in the case of Intrepid), your reboot with the install disk again - only this time, at the second stage boot: prompt, you choose the rescue mode with something like one of these options if shown:

[list]rescue
rescue-powerpc64
rescue64[/list]

or you can get to rescue mode with

```
Linux single
```

At some point in rescue-mode, or Linux single, you need to drop into the root shell, which is typically /dev/hda3 or /dev/sda3 if you have used guided partitioning to "use the whole disk".  There you can make the necessary edits with the values listed in the faqs and threads.

So gather up your monitors' specific horizontal and vertical video freqs.  Then find your driver, typically ati, r128, radeon, or nv.

This is just the starting point unfortunately, as there may be other options you'll want to use, such as video=ofonly nosplash or other options specific to the radeon that needs to be used at either the second-stage boot: prompt, and when that works, you put it into your /etc/yaboot.conf and sudo ybin -v to make it stick.

---

### Post by stream303 on 2008-11-22
> **IQRules said:**
> I have a PowerMac MDD 1.25G, is it 64-bit capable?

Doh!  Tiresia's right.  I just figured out what MDD meant, and since that is a G4, no 64-bit kernel for you. :)

---

