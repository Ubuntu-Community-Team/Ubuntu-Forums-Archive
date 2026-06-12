---
title: "can a virtual machine cope with high-end video edit app?"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by ICEcoffee on 2007-11-14
Hi all.

Does anyone know for sure, assuming I have adequate system resources, if I installed Windows XP in a virtual machine under Ubuntu Linux, would a high-end video editing app such as Adobe Premiere or Sony Vegas run smoothly, and perform all it's functions?

This is the only thing that would keep me dual-booting. I like Linux and want to migrate as much as possible.

Thanks

---

### Post by kpkeerthi on 2007-11-14
Apart from a marginal loss in performance (which I believe should be acceptable) , the only issue I see is getting your guest Windows XP recognize your Camcorder. You should bear in mind that if you can't get your Ubuntu detect your camcorder properly, you cannot get your XP detect it either. 

How are you connecting your Camcorder to download the movies? USB? Firewire? You will have a better chance if you are using USB as most virtualization product support USB pass-through to the guest OS. I suggest you to try it out yourself and see if your guest OS is detecting the capturing interface properly in your setup. If it does, your adobe premiere should be fully functional.

---

### Post by ByteJuggler on 2007-11-14
Just an aside: The speed of virtualisation is also affected by your CPU as some new CPU models now have some hardware support for virtualisation.  If your CPU does not have this, then you'll take a bigger hit in performance when virtualising.  What CPU have you got (or intend for the VM box?)

---

### Post by ICEcoffee on 2007-11-14
I currently have an Intel CPU P4 2.9ghz, which is 3 years old now, but I am considering buying a new machine for Linux, so if a new dual core, virtualized enhanced, 64bit CPU is the way forward, then I'm happy to go that route.

If I had such a computer, would running Adobe premier under a VM, be similar to that of Windows?

---

### Post by KCPokes on 2007-11-14
I was running VideoReDo through a VM for a while, but then after some upgrades (Gusty and VirtualBox) I no longer have any luck actually getting it to work.  I thought it was originally due to a network issue (wireless) but I was getting the same result hardwired; the video would stutter and eventually I had only audio.  I'm running this on a newer laptop (6 months old) with an Intel CoreDuo processor.  

Perhaps there are some variations that will work for you, but thus far I've had no luck.  Keep in mind that I am editting video that is not local to the machine, over the network, thus that may have some bearing as well.  Sadly though, that is how I edit the video, on the same machine, if I wanted to boot directly into Vista, thus that shouldn't have much of a bearing on the overall performance.

---

### Post by ByteJuggler on 2007-11-14
Such a setup certainly should help, but not having experience with Premiere and/or the hardware you would like to use I obviously can't say for certain.  I'm currently running a Core2Duo based Linux machine with VMWare hosting several VM's, I can perhaps download and do some tests with the Premiere trial/demo if there's something I can do to get an idea of whether it will work as you expect?

---

### Post by ICEcoffee on 2007-11-14
Bytejuggler, that would be awesome, and would save me taking the sledge-hammer route, ie buying a £500 system to find out my £1000 software doesn't work with my £1000 video camera. Much better to know that the editing software works FIRST, then spend the dollars.

I take the previous poster's comment that Linux needs to be able to connect to my video camera, so I'll test that later today.

Bytejuggles, please if you can, download the Sony Vegas 8 trial version instead of Adobe Premiere CS3, I did this under Windows XP and the installation is massive and takes a long time, Sony vegas is quicker and lighter to install.

If Vegas functions without problems then, I'll get the new computer and setup WinXP under a VM, becoming free from dual-booting doom.

---

### Post by ByteJuggler on 2007-11-14
OK, I know nothing of video editing apps, so you'll have to provide me some steps/tests to perform.  As an aside, I'll get Sony Vegas but will also try to get Premiere anyway - I've got quite a fast internet connection so shouldn't be too bad.

---

### Post by rosegarden78 on 2008-01-26
> **ByteJuggler said:**
> OK, I know nothing of video editing apps, so you'll have to provide me some steps/tests to perform.  As an aside, I'll get Sony Vegas but will also try to get Premiere anyway - I've got quite a fast internet connection so shouldn't be too bad.

You should try VMware converter.  Most applications circa 2002 and earlier work with WINE if you make a symlink to Common Files.

---

