---
title: "macbookpro 5,3 ? what disto works"
date: 2012-05-04
forum: Apple Hardware Users
---

### Post by matthewwallace on 2012-05-04
I'm really wanting to dual boot my macbookpro 5,3 using Ubuntu 12.04. I've gotten through what seems to be at least the install process but once I select Linux to boot into it gets as far as a really jacked up looking purple screen and that's as far as it gets.

The Live CD works just fine but trying to run after install just doesn't work. I've tried both 32 and 64 bit installs.

I'm wondering if anyone has had any luck with this. After searching through the following page [https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)  it seems to suggest that the latest I can use is 10.04. Is this page just out of date, am I doing something wrong or can someone point me to some documentation that will help me get through the install and get it working with no issues ?

---

### Post by Dave75 on 2012-05-04
Hi Mattew,

Macbookpro 5.1 and same story, same bad luck.

I've tried both standard desktop distro and the one mentioned as for MAC, but without any difference.

I'm thinking to try the old 10.xx distro, then install this on USB and then try to upgrade from 10.xx to 12.04, but not sure at all if it can work or not.

Bye,
Davide

---

### Post by matthewwallace on 2012-05-04
@Dave75 ... if you do give it a try let me know how it goes for you. I may also give this a try over the weekend.

---

### Post by Stradijeri on 2012-05-04
I had 11.10 working on my triple-boot MacBook Pro, but when I updated to 12.04 it hangs at boot. 
I made a video detailing the issues further, and requesting assistance. 
[http://www.youtube.com/watch?v=j21h-r0t3lw](http://www.youtube.com/watch?v=j21h-r0t3lw)
I'm sure the issue is simple, I'm just not experienced enough to know :(

---

### Post by matthewwallace on 2012-05-04
@Stradijeri - This is pretty much what is happening to me but instead of a solid purple boot screen mine looks all jumbled and messy. I'm willing to bet these are related. 

Hoping someone with more experience with Ubuntu is working on a fix. I'd love to switch over to using the OS fulltime but I'm not willing to get a new machine or run on a VM.

---

### Post by Grumpey on 2012-05-04
have you tried setting nouveau.noaccel=1 in the boot options for the kernel.

Info on how to change here:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Loading mine(5,1), I had to do it for the initial install, and after the first boot until  I installed the nvidia drivers.

---

### Post by Hatsune Miku on 2012-05-04
Its nouveau, it does the same thing for me for an older NVIDIA GPU on my old desktop. I always hated nouveau.

---

### Post by jrminter on 2012-05-04
I can't even use either live CD. Just get a jumbled screen. Tried F1 to use a boot option, but no luck. I really wish there was some way to force a VGA install until I get to add the proprietary Nvidia drivers.

---

### Post by matthewwallace on 2012-05-05
YES!  I totally figured this out for the macbookpro 5,3

I've installed Ubuntu 12.04 amd64 version. After installing you need too boot using the again. Get to the advanced screen and selected the last item in the list that says Boot from Hard Drive, then tab down and add the following to the boot options  nouveau.noaccel=1

That should get you into Ubuntu the first time. Then you can figure out what drivers you need to fix your boot issue.

---

### Post by Stradijeri on 2012-05-05
> **matthewwallace said:**
> YES!  I totally figured this out for the macbookpro 5,3

I've installed Ubuntu 12.04 amd64 version. After installing you need too boot using the again. Get to the advanced screen and selected the last item in the list that says Boot from Hard Drive, then tab down and add the following to the boot options  nouveau.noaccel=1

That should get you into Ubuntu the first time. Then you can figure out what drivers you need to fix your boot issue.
"Boot from hard disk" booted me into Windows 7. Can I somehow specify which partition to use in "boot options" as well?

---

### Post by Dave75 on 2012-05-06
> **matthewwallace said:**
> YES!  I totally figured this out for the macbookpro 5,3

I've installed Ubuntu 12.04 amd64 version. After installing you need too boot using the again. Get to the advanced screen and selected the last item in the list that says Boot from Hard Drive, then tab down and add the following to the boot options  nouveau.noaccel=1

That should get you into Ubuntu the first time. Then you can figure out what drivers you need to fix your boot issue.

It works for me too! on MackBook Pro 5.1! Then I've been able to install it on USB flash key and boot from it, actually I'm writing from 12.04 installed on USB flash key on my 5.1 (with some tricks)!

Davide

:popcorn:

---

