---
title: "Installing Ubuntu on Mac"
date: 2011-09-12
forum: Apple Hardware Users
---

### Post by dmubu on 2011-09-12
Hello,

I have installed Ubuntu on PC so that upon booting the machine I can choose my OS.

What is the best way to install Ubuntu on a Mac?  Is it possible to  install so that I can choose the OS upon booting the machine?  Or is it  better to run it through a program like VirtualBox?

Thank you!

---

### Post by yokohama1970 on 2011-09-16
I like Sun Micro Systems/Oracle's VirtualBox a lot. Especially, because you are able to run Ubuntu inside Mac OS. I am not a Windows user, although Windows 7 has great functionality, updated features & great compatibility. 

If you are using an Intel-Based Mac, I would strongly suggest VirtualBox. Besides, Installing Ubuntu does not require any Disc Partitioning.

---

### Post by entangled on 2011-09-18
I have already installed ubuntu on a Mac partition but I tend to agree that virtualbox is the best way. 
To use a Mac partition you have to get round the problem of it being a GPT disk (and create a pseudo MBR). After failing with the normal build, I used the special 'alternate-amd64-mac' build of ubuntu to install on the Mac. It installed fairly easily and mostly runs very well. I used refit on the Mac to make booting a bit smoother.

One problem is power use. 
Firstly, ubuntu usually takes about 30w more while running than does OSX. Doesn't sound much but it adds up.
Secondly, sleep and resume has a bug. OSX does this very quickly and easily, resuming in 3 secs. Ubuntu sleeps OK but it always resumes with a black screen. I have an intel iMac and it chooses the Display Port output instead of the main screen each time it resumes. If you don't have a second screen connected on that port you have to hit the power button and restart. If you do have a second screen you have to pull windows over and reset the Monitor to the main screen. Very frustrating. There was a time when ubuntu always chose the Display Port during installation, so you never saw the installation screens and it was impossible without a second screen. The problem with sleep and resume seems to confirm that the original screen selection problem was in KMS.

---

### Post by srs5694 on 2011-09-18
> **entangled said:**
> To use a Mac partition you have to get round the problem of it being a GPT disk (and create a pseudo MBR).

Actually, it's quite possible to boot Linux on an Intel-based Mac using a pure GPT configuration without a hybrid MBR. See [this Web page](http://www.rodsbooks.com/ubuntu-efi/index.html) I wrote on one way to do this. Unfortunately, most installation procedures you see on the Web assume using Apple's Boot Camp to get things started, and Boot Camp creates a hybrid MBR and boots the computer in BIOS mode. To do it in another way you'll have to either do it the usual way and then reconfigure things or figure out how to do it directly using an EFI boot -- and Ubuntu's EFI-mode installation is still pretty new and bug-laden.

---

### Post by Lars Noodén on 2011-09-18
If you decide to do dual boot, then [rEFIt](http://refit.sourceforge.net/) helps a lot.  It allows you to choose which OS you are going to boot.  You can also choose whether it defaults to OS X or to Ubuntu.

---

