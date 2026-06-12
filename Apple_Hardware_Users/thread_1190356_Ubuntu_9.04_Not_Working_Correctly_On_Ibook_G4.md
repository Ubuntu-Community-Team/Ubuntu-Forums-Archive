---
title: "Ubuntu 9.04 Not Working Correctly On Ibook G4"
date: 2009-06-17
forum: Apple Hardware Users
---

### Post by Masamune12003 on 2009-06-17
Hey ho crew!

Just grabbed myself a copy of Ubuntu 9.04 so that I could follow the instructions given at: [http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-904/#more-1605](http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-904/#more-1605).
I want 9.04 on a usb stick and this seemed the only way to do it, they also have a tutorial for 8.04 but it turns out that there is no live-cd for powerpc so that was a bucket of fail.
I whacked 9.04 onto a cd burned through windows and put in the mac, the first couple of times it would get to radeaonfb (insert weird number with lot's of 0's) and then hang on a black screen.
After using Live-Nosplash-powerpc (or something like that) I have managed to get Ubuntu to load.
I get to the desktop and the CD is spinning away and then it brings up several error messages of things it has just failed to load, lovely.
So with no date, desktop viewer and a host of other applet's (wifi just doesn't work but tbh I was expecting that) I am feeling a bit stuck.
I decided to try going along with the tutorial regardless because it never mentioned any of these problems being...problematic?
# mkdir -p ubcd/boot/grub seems to work.
# cp /usr/lib/grub/i386-pc/stage2_eltorito ubcd/boot/grub however does not, it gives me a missing destination file operand (operand?) after 'cp /usr/lib/grub/i386-pc/stage2_eltorito ubcd/boot/grub'.
What the hell do I do?
Somebody?
Anybody?
It's taken me all day to get this far and I only have access to a working windows machine until friday so any help will be greatly appreciated.

System: Ibook G4, 128mb RAM (I think), Haddrive does not work so no OS, CPU is 1.26 Ghz I believe (Long time since I've seen it, it may be more.)

All I want is an operating system I can boot from usb and get online.

Thanks for your time!

Masamune12003

---

### Post by MikeTheC on 2009-06-17
A quick glance reveals you're using the x86-based version of Ubuntu 9.04.

Try this: [http://cdimage.ubuntu.com/ports/releases/9.04/release/](http://cdimage.ubuntu.com/ports/releases/9.04/release/)

---

### Post by Masamune12003 on 2009-06-18
Cheers muchly!
Will try it when I get home tongiht, I really want to get my Airport Extreme card working soon :)
Thanks again!

P.S. Is it the Desktop version I should use?

---

### Post by MikeTheC on 2009-06-18
I would imagine so, though I'm by no means an expert on current generation PPC release options and choices for Ubuntu. I've mainly dealt with Debian on PPC hardware.

---

### Post by Masamune12003 on 2009-06-19
Didn't work, wouldn't boot at all.
I'm going to go a different route and try and put a malfunctioning HDD from an IBM Thinkpad into the Ibook and see if I can install Ubuntu 9.04 straight to it.
Wish me luck lol
Thanks for the advice!

---

### Post by tgalati4 on 2009-06-19
PPC macs in general can't boot from USB, but can boot from external drives using firewire.  Hold Apple-c or Apple-t during power-on and a bootup manager will show up so you can choose the disk that you want to boot from.

You'll get more mileage (and less frustration) putting Tiger on the first partition.

---

### Post by MikeTheC on 2009-06-19
> **tgalati4 said:**
> PPC macs in general can't boot from USB, but can boot from external drives using firewire.  Hold Apple-c or Apple-t during power-on and a bootup manager will show up so you can choose the disk that you want to boot from.

Nope and nope. There's no such thing as CMD + C or + T for startup purposes.

Besides, the "correct" form of those only forces it to try and boot from the optical drive or to put itself into "Target Disk Mode", respectively, neither of which is of use here.

Personally, if I were the OP, I'd try using (in this order) Debian, Fedora and OpenSuSE on that system, since they maintain current version PPC releases. I know for a fact Debian will work; the only question is are there things it won't have (Debian being Debian) that the other two will have *which the OP will actually need or care about*.

---

### Post by billyjmc on 2009-06-27
> **tgalati4 said:**
> PPC macs in general can't boot from USB, but can boot from external drives using firewire.

Okay, I poked around in the Open Firmware quite a bit when I first installed various flavors of Linux on my iBook G4. The reality is that you can boot from USB, but you can't do it without modifying the open firmware.

I *want* to say that the reason they can't boot from USB by default is that while OF detects the USB devices, it doesn't pass that information on to the bootloader. The OS is expected to re-detect USB devices, and the bootloader was simply programmed without USB support. My explanation/memory may be wrong, but USB booting *is* possible, nonetheless.

_[This website]("http://www.macosxhints.com/article.php?story=20060301112336384")_ describes the procedure. One key point to note is that the linked article is for booting OS X, but when you have linux installed on a disk, the commands described won't work, AFAIK. Where he reccommends to type:
```
boot ud:2,\\:tbxi
```you'll probably need to type instead:
```
boot ud:2,yaboot
```IIRC, the first command tells OF to look for a file of a certain type, wheras the second tells it to look for a specifc filename, which cooresponds to the PPC linux bootloader (the partition it resides on must be HFS+, I believe). The link describes in more detail what these commands mean, but this should get you going in the right direction. My iBook was picky about which USB drives it would read from OF. Try several different USB disk enclosures if the first one doesn't work.

---

### Post by justmehere on 2009-07-09
I just found this thread. I've not managed to get it to work yet but refering to previous posts:

You need to download and burn community supported powerpc version not the i386 version.
You can boot the ibook from the CD/DVD just turn it on whilst holding down the C key. You may need to hold the C key down for a few seconds.

I've had success with previous versions but 9.04 seems to just result in a black screen during the boot process. I have tried several different startup options.

:¬}

---

### Post by billyjmc on 2009-07-16
> **justmehere said:**
> 

I've had success with previous versions but 9.04 seems to just result in a black screen during the boot process. I have tried several different startup options.

:¬}

Maybe you should try the kernel option below. It's worked wonders for me, but you may be having different issues than I was.  ```
video=radeonfb
```

---

