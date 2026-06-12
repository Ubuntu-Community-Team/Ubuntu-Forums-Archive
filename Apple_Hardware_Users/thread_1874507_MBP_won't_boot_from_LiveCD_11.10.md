---
title: "MBP won't boot from LiveCD 11.10"
date: 2011-11-03
forum: Apple Hardware Users
---

### Post by Tonksy on 2011-11-03
Hi people

I have searched the forum, and googled, but I can't seem to find the answer to my question so apologies if this has been raised before.

Basically I can't get my MBP to boot from the 11.10 CD and was wondering if anyone is experiencing the same thing and/or has a solution.

Machine:  MacBook Pro (3.06GHz Core 2 Duo, 8GB RAM), Mid 2009 running OS X Lion 10.7.2.
Ubuntu ISO:  ubuntu-11.10-desktop-i386.iso

The MBP recognised the disc and starts to boot ok, the loading screen appears (light purple right at the beginning) and the disc continues to be accessed (can clearly be heard spinning).  But then a blinking cursor appears at the top left of my screen appears and that is as far is it gets.  The disc stops spinning at this point.

Now I know the CD works fine because I have tried it on our work MacBook which boots from it perfectly fine, so what's the deal?  Am I missing something?

Work Machine:  MacBook 5,2 (2GHz Core 2 Duo, 2GB RAM) running OS X Snow Leopard 10.6.8.

---

### Post by HotForLinux on 2011-11-03
I couldn't boot neither from Natty nor from Oneiric 64bit versions live CDs in a MBP, 3,1. But the symptoms were different, there was a message question but nothing happened after selecting "1" or "2". I don't know if there's the same problem with the 32 bit version. But after searching I discovered that there's an issue with that. So I dowloaded special Cds named:  something--amd64+mac.iso, not only amd, that don't have REFIT things.

[http://cdimage.ubuntu.com/releases/11.04/release/](http://cdimage.ubuntu.com/releases/11.04/release/)

And those worked well. In any case you have to wait a long while after selecting to use the LiveCD

---

### Post by jvic on 2011-11-03
is it necessary to have refit installed to boot the live CD?

i suppose to install Ubuntu the answer is yes (?), but what about the live cd?

---

### Post by Hatsune Miku on 2011-11-04
> **jvic said:**
> is it necessary to have refit installed to boot the live CD?

i suppose to install Ubuntu the answer is yes (?), but what about the live cd?

It wouldn't be a bad idea to use rEFIt to boot the CD. rEFIt seems to handle the hand-off from EFI to GRUB better then what the OS X boot loader does.

---

### Post by B Pearce on 2011-11-04
Hey Everyone,

I address this problem here:

[http://ubuntuforums.org/showthread.php?t=1872470](http://ubuntuforums.org/showthread.php?t=1872470)

I am running 11.10 on MacbookPro8,1.

Brad

---

### Post by Soren470 on 2011-11-06
> **Tonksy said:**
> Hi people

I have searched the forum, and googled, but I can't seem to find the answer to my question so apologies if this has been raised before.

Basically I can't get my MBP to boot from the 11.10 CD and was wondering if anyone is experiencing the same thing and/or has a solution.

Machine:  MacBook Pro (3.06GHz Core 2 Duo, 8GB RAM), Mid 2009 running OS X Lion 10.7.2.
Ubuntu ISO:  ubuntu-11.10-desktop-i386.iso

The MBP recognised the disc and starts to boot ok, the loading screen appears (light purple right at the beginning) and the disc continues to be accessed (can clearly be heard spinning).  But then a blinking cursor appears at the top left of my screen appears and that is as far is it gets.  The disc stops spinning at this point.

Now I know the CD works fine because I have tried it on our work MacBook which boots from it perfectly fine, so what's the deal?  Am I missing something?

Work Machine:  MacBook 5,2 (2GHz Core 2 Duo, 2GB RAM) running OS X Snow Leopard 10.6.8.

I have this same problem when trying to install ubuntu on my Macbook Pro. I have tried to boot from the CD using the Mac OS X bootloader thingy and reFIT, and it always does that blinking underscore symbol in the top left corner. I feel like there should be a solution to this that doesn't involve all of the steps and things that the person above me said made it work for them...I just want it to work...

---

