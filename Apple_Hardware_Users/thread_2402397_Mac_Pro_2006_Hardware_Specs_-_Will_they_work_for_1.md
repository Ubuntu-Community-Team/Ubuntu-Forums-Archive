---
title: "Mac Pro 2006 Hardware Specs - Will they work for 18.04"
date: 2018-09-29
forum: Apple Hardware Users
---

### Post by Smack2k on 2018-09-29
Hey all,

New to the Ubuntu forums and new to Linux overall.  Have installed Ubuntu several times in VMs and have gotten to know the Terminal fairly well..but have a question about hardware specs...

I want to install 18.04 on my older Mac Pro 2006 model that has been upgraded to (2) Quad Core Xeon E5355 2.66 GHZ Procs and 32 GB RAM.  Can I install and run Ubuntu on here and have it run well?  I know Linux requires much less than Windows to run, but wanted to check with those in the know before I trudge forward.....

Appreciate the help!

Found this post - [https://mattgadient.com/2016/07/11/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/](https://mattgadient.com/2016/07/11/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/).  A little confused..  will downloading the mac distro I want to run and burning to DVD allow me to just boot it from DVD and install on my 32-Bit EFI, 64-Bit Proc MacPro 1,1?

---

### Post by oldfred on 2018-09-29
Moved to Apple hardware sub-forum where those with Mac may be able to help.

---

### Post by kevin160 on 2018-09-29
It should run.  I haven't fired up Ubuntu on my old 2006 pro in a couple years.  I went back to running El Capitan on it.  The problems you have to overcome include:

#1.  Early Intel Macs have a 32-bit EFI even though they are 64-bit otherwise.  You need to boot via the 64-bit version of grub-efi-ia32.  There are some good tips in [this thread.]("https://ubuntuforums.org/showthread.php?t=2287767")  Guides for installing Ubuntu on Atom tablets (which also have 32-bit EFI) should also help.  

#2.  The 2006 Pro is a giant pain to get anything to boot from USB.  It _is_ possible (vmware esxi 6.0 boots, for example), but the simplest method I found to install things on the Pro was to set up a hard drive on a different machine and then move it to one of the Pro's internal drive bays.  

#3.  Make sure you install a fan controller service like macfanctld or mbpfan so you don't overheat your Pro.

Enjoy!  I might give Ubuntu another try on mine.  I went back to El Cap because I couldn't get sleep/wake working under Linux and these old beasts suck over 100W when idle.

---

### Post by Smack2k on 2018-09-29
Thanks for the advice and information.  Will give it a shot....

I wasnt aware of the heated issues....

Let me ask you this.....would I just be better off if I installed it on an older PC that has (2009) AMD 3 GHZ Quad Core Proc with 8 GB RAM.  Or if I get things working on the Mac Pro, would I have better performance?

---

### Post by kevin160 on 2018-09-30
The heat issue is less about power output and more about Apple's design.  PC fans are usually controlled by their BIOS while Macs are all under software fan control.  It's the same for all macs running Linux as far as I know.  

As for running an AMD instead, you'd really have to test, as it will all depend on what services and apps you are running.  I can't imagine that a 2009 4c/8GB would give better performance than a 2006 8c/32GB.  Maybe you are using a modern video card that would see a bottleneck from the PCIe 1.0 in the Pro.  Or maybe if your primary purpose is running some single-core app.

---

