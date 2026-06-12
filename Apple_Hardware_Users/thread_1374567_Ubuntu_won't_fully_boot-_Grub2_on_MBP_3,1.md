---
title: "Ubuntu won't fully boot- Grub2 on MBP 3,1"
date: 2010-01-07
forum: Apple Hardware Users
---

### Post by Fox11 on 2010-01-07
I've been trying to get Ubuntu to boot from my usb thumb drive for hours, to no avail (I'm on a Macbook Pro 3,1 Santa Rosa with the latest EFI update 1.5). A full install with rEFIt doesn't work at all. I have booted with absolutely NO troubles straight from the Ubuntu CD. 

And I've ALMOST booted from a live usb install on my usb thumb drive, but it always seems to freak out. The boot-up commands will run for some time with no problem and then suddenly- BAM! The screen will start to flicker, bouncing from the Terminal command prompt (which will allow input when that screen appears) to some other screen with a few other boot-up commands (this screen also allows input, although nothing seems to happen when I press "Enter.") Basically it 'strobes' between the two screens fast, blinking from one to the other in an endless loop. If always stops at a different place in the boot-up process each time, sometimes further along than other times. If I press the power-off button, the screen immediately goes back to normal (back to original boot-up commands screen, no flickering) and then proceeds to shut down in an apparently normal way.

I booted the CD through Grub and had the same problem (boot seems to stop, flickering screen), so I would assume it's something wrong with Grub, and not the install? I got my copy from the last post on this page:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202039]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202039")
-----------------------------
[SIZE="1"]Here is a solution that worked for me:
[http://ubuntuforums.org/showpost.php?p=7275427&postcount=762](http://ubuntuforums.org/showpost.php?p=7275427&postcount=762)

If you place this (fat binary) file on your FAT formatted USB stick to
/EFI/BOOT/BOOTX64.EFI
/EFI/BOOT/BOOTIA32.EFI
then when you insert the stick into an Intel Mac and press "Alt", an icon called "EFI Boot" shows up and you can boot from this USB stick into GRUB2.

Place the following in /efi/boot/grub.cfg on your USB stick to boot Ubuntu Live automatically:

# Timeout for menu
set timeout=0

# Set default boot entry as Entry 0
set default=0

# Entry 0 - Load Linux kernel
menuentry "Ubuntu Live" {
fakebios
search --set /casper/vmlinuz
linux /casper/vmlinuz boot=casper video=efifb agp=off show-cow noprompt -- debian-installer/language=de console-setup/layoutcode=de max_loop=32
initrd /casper/initrd.gz
boot
}[/SIZE]
-------------------------------
And I added a grub.cfg file that is identical to the one in that post, except that I changed the initrd.gz to .lz, and the language and layout code =us instead of =de. This is what initializes the boot-up, otherwise I just get grub's command line (and I'm not 100% sure what command(s) will initialize a boot-up of Ubuntu from grub's command line, thus I'm using the grub.cfg, since it seems to be working- almost). Could this be the problem?

The other thing I though of was the GPU (nvidia 8600gt)- when the Ubuntu CD boots, it comes up with a little window that says I need to update the display driver. But it's obviously running fine off the CD, so it's hard for me to believe this would be the issue, right?...

If anyone has had this same problem and fixed it, or has some other way to boot Ubuntu that works on this particular MBP, I'd really appreciate your help! I just want to get it running off of the USB drive!

---

### Post by linuxopjemac on 2010-01-07
If I were you I would try Jaunty, as it uses Grub1. If that all works, you can update to Karmic. I haven't yet seen a guy who installed Karmic on a MBP 3,1 successfully.

---

### Post by linuxopjemac on 2010-01-07
Contact one of these guys in the following thread, they were able to install Karmic on this machine. Please write a manual for this machine and post your results here...This machine's manual is lacking.

[http://ubuntuforums.org/showthread.php?t=1299429](http://ubuntuforums.org/showthread.php?t=1299429)

---

### Post by linuxopjemac on 2010-01-07
here another guy who went from Jaunty to Karmic on your machine:
[http://ubuntuforums.org/showthread.php?t=1349225](http://ubuntuforums.org/showthread.php?t=1349225)

---

### Post by linuxopjemac on 2010-01-07
you can also first try to fiddle around with grub a bit:

[http://mac.linux.be/content/problems-refit-and-grub-after-installation](http://mac.linux.be/content/problems-refit-and-grub-after-installation)

---

### Post by Fox11 on 2010-01-07
Alright, I'm going to give 9.04 a try- I'm still convinced that it MUST be possible to use 9.10 (it is ALMOST booting, and, again, the CD boots perfectly!). I'll update with the results...

---

### Post by Fox11 on 2010-01-07
Man, this is frustrating! I'm almost 100% sure Ubuntu IS booting, but the GUI just isn't coming up. I got the Netbook Remix of Ubuntu 9.04 to boot all the way to the Terminal prompt again ('flickered'/'flashed' a little bit, but then it stayed on the one screen). I ran a couple basic commands (cd, dir, etc.) and they worked as expected, but no desktop, just a black screen with white text... Could this be a problem with GNOME? Or GRUB? Or my Nvidia card? As I said before, the CD booted up just fine on it's own, but not with GRUB, which makes me gravitate towards GRUB being the issue...

---

### Post by linuxopjemac on 2010-01-07
Why don't you just try the 'normal' Ubuntu versions? You are having a laptop, not a netbook.

---

### Post by Fox11 on 2010-01-07
Been messing with it a bit more- grub2 now boots a full install of 9.10- but again, same video issues (because of this, can't fully log in, since I can't tell if my password characters are taking or not, due to the flickering screen). Basically, there is no GUI- I think the flickering is Ubuntu TRYING to display a GUI, but not being able to for some unknown reason.

Is there something I can add to the grub.cfg to get the video to work? This is the grub.cfg, as of now:

```

# Timeout for menu
set timeout=0

#Set default boot as Entry 0
set default=0

#Entry 0 - Load Linux kernel
menuentry "Ubuntu" {
fakebios
root=hd0,2
linux /vmlinuz root=/dev/sdb2 video=efifb noefi
initrd /initrd.img
}

```

Note: As grub gets ready to start booting Ubuntu, it tells me that it'll be displaying in 1440x900- could this be too high a resolution or something? Or is this completely unrelated?

---

### Post by linuxopjemac on 2010-01-08
Try a lower resolution as described [here]("http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html"). I also saw something about it [here]("http://wiki.archlinux.org/index.php/GRUB2#Setting_the_framebuffer_resolution").

Some other people also reported problems
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/392680](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/392680)

ok, now I stop searching, the last link:
[http://forums.debian.net/viewtopic.php?f=5&t=41881](http://forums.debian.net/viewtopic.php?f=5&t=41881)

---

### Post by Fox11 on 2010-01-08
I got it working!!! I now have a full install of Ubuntu 9.10 booting from my USB thumb drive on my Macbook Pro 3,1!

I'll create a new thread soon with a detailed/simple guide as to what I did (took me long enough, trial-and-error and searching all over to get it working, so I figure I'll make it easier for the next person who attempts it).
linuxopjemac- thanks for your help! and thanks for the help in general, Ubuntu forums! You were a really good resource!

Edit: Link to EFI Boot Guide I created [http://ubuntuforums.org/showthread.php?t=1376277]("http://ubuntuforums.org/showthread.php?t=1376277")

---

### Post by linuxopjemac on 2010-01-09
Fantastic guide!! I will post this great manual on my own site if you don't mind. It's a great guide to have an Ubuntu installation on USB, bootable for Intel Macs.

One question: where did you get the blacklist-agp.conf and xorg.conf files from ?

---

### Post by Fox11 on 2010-01-09
You can post it wherever else you want- the idea is to get the info out there for others to use! It would be nice if people didn't have to go through the hours and hours of trial-and-error booting and searching high-and-low for answers that I did.

I got the code for the blacklist-agp.conf file from the first source link I posted at the end of my 'guide' (thread called "grub2 EFI Boot Loader internal/external booting"). I found the most basic xorg.conf code from some random site and added the "driver          fbdev" line as per the instructions in the above-mentioned thread. 

Note: In 9.04 (Jaunty) there's already an xorg.conf file which can simply be modified with the "driver            fbdev" line, but, as you might already know, 9.10 (Karmic) seems to have done away with the xorg.conf file, although upon searching, I found that it will still take instructions from the file if the user creates one and puts it in the correct directory.

---

