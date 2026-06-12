---
title: "Installing Ubuntu on a Macbook Pro Mid-2012 (9,1)"
date: 2012-08-09
forum: Apple Hardware Users
---

### Post by Ad1217 on 2012-08-09
I have been trying to install Ubuntu 12.04 on a Macbook Pro 9,1 and have run into some problems.
I tried to use a cd, both 12.04 amd64 and amd64+mac, but I just get a blinking cursor when I try to boot them.
I have also tried rEFIt and iso2usb efi (with 12.04 amd64, 12.04 amd64 +mac, and 10.10 amd64), but that gets stuck loading the kernel.

Edit: The one thing I did not try (which worked) was booting from a normal usb stick.

---

### Post by CrazyDymond88 on 2012-08-14
This is marked as solved, was it?  If so, what was the solution?

---

### Post by marsokod on 2012-08-14
Hi,
I was trying to boot from the CD and had the same problem as you when I saw your post.

I am currently trying to boot from a USB stick (created with unetbootin) as you advised. But now I get a kernel panic with the amd64 and amd64-mac version. I will try with the x86 version but a 64bit OS would be nicer.

Can you tell us which image you used and how you build your USB stick (dd, ubuntu tool,...)
Thanks,

EDIT: I succeeded in running the live version of Ubuntu with the x86 iso on a USB stick. Is there any way to install the 64 bits version?

---

### Post by CrazyDymond88 on 2012-08-14
I just used the image off of ubuntu's web site, created a usb stick from a windows machine.  When booting you have to add noapic to the end of the boot string or it will kernel panic.

---

### Post by Ad1217 on 2012-08-19
I used this method to create the boot usb: [https://help.ubuntu.com/community/Installation/FromUSBStick/#From_Mac_OSX](https://help.ubuntu.com/community/Installation/FromUSBStick/#From_Mac_OSX)

---

### Post by JumpingJackFlash on 2012-10-20
HI

Can someone make a tutorial for this, in layman's terms? I've got really frustrated trying to put Ubuntu onto my 2012 MBP, so a simple tutorial would be fantastic! :)

Thanks!

---

### Post by SMOKE14 on 2012-10-20
> **JumpingJackFlash said:**
> HI

Can someone make a tutorial for this, in layman's terms? I've got really frustrated trying to put Ubuntu onto my 2012 MBP, so a simple tutorial would be fantastic! :)

Thanks!
Since you are on a Mac
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx) for USB
[http://www.ubuntu.com/download/help/burn-a-dvd-on-mac-osx](http://www.ubuntu.com/download/help/burn-a-dvd-on-mac-osx) for DVD
Hope I helped :)

---

### Post by JumpingJackFlash on 2012-10-20
No, sorry. I've burnt the disk image fine, but when I try to boot from it, I just get the blinking cursor, and I don't know how to fix it :/ I appreciate your quick response, though! :)

---

### Post by SMOKE14 on 2012-10-20
Which .ISO image did you use?

---

### Post by piratpalle on 2012-10-20
I have kinda the same issue, i use : Ubuntu 12.04 LTS

---

### Post by JumpingJackFlash on 2012-10-20
> **SMOKE14 said:**
> Which .ISO image did you use?
I used Ubuntu 12.04.1 i386 and I've tried the 64Bit one as well.

---

### Post by holibut on 2013-01-31
Why marked as [SOLVED], how?
I am stuck by this issue. I've burn at least 3 CD and format  a USB disk.
Reboot and reboot, wait and wait, the cursor on the screen blink and blink.

So, please give some hints, I will be very appreciated!

---

### Post by holibut on 2013-01-31
I follow this post: [http://cberner.com/2012/07/10/installing-ubuntu-12-04-on-macbook-pro-retina/](http://cberner.com/2012/07/10/installing-ubuntu-12-04-on-macbook-pro-retina/)

Then can install Ubuntu, but got the error: "Executing ‘grub-install /dev/sdb’ failed. This is a fatal error."

It seems that I can not install grub.
After reboot, I use try ubuntu, and try to re-install grub, but every device I mounted is read-only. So I can not install to anywhere. I want to triple-boot. There was a Win7 already installed and can boot OK. 

sudo fdisk -l&#12288;&#12288;

&#12288;&#12288;sudo mkdir /media/tempdir&#12288;&#12288;

&#12288;&#12288;sudo mount /dev/sda9 /media/tempdir (mounted as read-only), I tried every disk.

&#12288;&#12288;sudo grub-install --root-directory=/media/tempdir /dev/sda

reboot, enter the Ubuntu just installed, then:

&#12288;&#12288;sudo update-grub2


Any idea?

---

### Post by cwalburg on 2013-02-12
I hope I'm posting this in the right place.... I am having a similar problem. I'm completely new to Linux and have very limited programming experience. I want to install Ubuntu 12.10 on my Macbook Pro (mid 2012 OSX 10.8.2) in a dual environment using rEFIt.

I partitioned my drive using Disk Utility, creating another Macintosh HD box on the "partition" tab with 50 GB. Then I burned Ubuntu to a DVD and restarted. When I was lucky enough to have it show up on rEFIt, Linux would pretty much go straight to a black screen with a blinking cursor.

When installing via USB drive, I can get a purple loading screen, quickly followed by the dead-end cursor screen. If I press the DOWN arrow key I can access a menu with a language menu, then options for trying linux, installing linux, etc. Clicking on either one will lead me to this screen:

[ATTACH]231326[/ATTACH]

I can type in whatever I want, just nothing will happen. I'm assuming this is "GRUB," but I'm not sure. I've tried a few GRUB commands but can't get a response.

There are way too many boot options:

[ATTACH]231325[/ATTACH]

All I want is an Apple and a Penguin! I've seen a lot of info about new Mac computers having some fatal flaw in the software that must be fixed using an alignment(?) command in rEFIt, but even after trying that nothing happens.

I'm sorry if this isn't in the right place, but I'd really appreciate any sort of advice.

---

### Post by Ad1217 on 2013-02-12
cwalburg: You should be able to edit boot commands, I think with an F-something key (it says at the bottom of the try/install menu). Add noapic to the end.

holibut:I remember having that issue with Grub, but cannot remember how I solved it.

Also, I ended up using Linux Mint, but can't get the Nvidia driver to work nicely. Nouveau works fine.

---

### Post by cwalburg on 2013-02-12
Thanks! I tried that, and managed to "try" Ubuntu. However, the graphics were really laggy and my macbook's keyboard/trackpad were unresponsive. I had to use my roommate's mouse to do anything. Unless I can find an easy solution for the graphics, I'm going to close the book on this endeavor. Thank you for responding quickly. :D

---

### Post by Ad1217 on 2013-02-12
It did get a lot better after I actually installed it, and the correct drivers helped a lot. These two repositories really help:

[URL="https://launchpad.net/~mactel-support/+archive/ppa"]https://launchpad.net/~mactel-support/+archive/ppa
[/URL]
[https://launchpad.net/~mpodroid/+archive/mactel](https://launchpad.net/~mpodroid/+archive/mactel)

---

### Post by nsicad on 2013-02-12
> **cwalburg said:**
> Thanks! I tried that, and managed to "try" Ubuntu. However, the graphics were really laggy and my macbook's keyboard/trackpad were unresponsive. I had to use my roommate's mouse to do anything. Unless I can find an easy solution for the graphics, I'm going to close the book on this endeavor. Thank you for responding quickly. :D

You should use 13.04 ubuntu for this machine. Macbookpro mid 2012 has support in 3.8 linux kernel. 13.04 ubuntu uses 3.8 linux kernel.

Get the iso from here.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

