---
title: "PowerPC install problem: &quot;[...]/boot/vmlinux: No such file or directory&quot;"
date: 2011-04-13
forum: Apple Hardware Users
---

### Post by amount on 2011-04-13
Hello,

I'm having some trouble installing Ubuntu 10.10 on a PowerBook G4. The install appeared to proceed without any problems, but now I'm unable to load the kernal. I may be in over my head with this, but if anyone is willing to help me out I'd greatly appreciate it!

Here's what happened:

I downloaded the Mac (PowerPC) and IBM-PPC (POWER5) desktop CD .iso file from this page: [http://cdimage.ubuntu.com/ports/releases/10.10/release/](http://cdimage.ubuntu.com/ports/releases/10.10/release/) (Specifically: [http://cdimage.ubuntu.com/ports/releases/10.10/release/ubuntu-10.10-desktop-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/10.10/release/ubuntu-10.10-desktop-powerpc.iso))

I burned the image to a CD using another computer and started up the PowerBook with the disc in the drive. After going through the usual pre-install questions, I selected the option to erase the hard drive and do a clean install. It took a long time to finish (two hours maybe?), but it did. The computer restarted automatically, but it didn't get very far.

Here's what I'm seeing on my screen:

```
Welcome to yaboot version 1.3.13
Enter "help" to get some basic usage information
boot: Linux
Please wait, loading kernal...
/pci@f4000000/ata-6@d/disk@0:3,/boot/vmlinux: No such file or directory
boot: _
```I have to admit that I'm flummoxed! Anyone have any ideas? (I'm kind of a newb, so dumbing it down for me would be appreciated.)

Thanks!

---

### Post by uRock on 2011-04-13
Moved to Apple Users sub-forum.

---

### Post by linuxopjemac on 2011-04-14
You have a problem with yaboot. I would do an expert installation, don't do anything in the installer, only to install the yaboot bootloader. I know that Debian installers can do this kind of work automatically.
Other solutions:
[http://mac.linux.be/content/yaboot](http://mac.linux.be/content/yaboot)

---

### Post by amount on 2011-04-14
Thanks for the reply, linuxopjemac. Just to clarify, are you suggesting that I used my PPC desktop CD to install the yaboot bootloader? 

I'm not exactly sure how to do this. Do you know of any tutorials or websites that I could look at? (I followed your link, but quickly found that I was unfamiliar with much of the terminology.) I'll take a stab at it in the meantime and will report back if I'm still having trouble.

---

### Post by Dutch70 on 2011-04-14
There is something wrong with that download. It's 710MB which is obviously too big for a cd.

You're not the only one having problems with that download right now.
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?p=10678338#post10678338[/COLOR]]("http://ubuntuforums.org/showthread.php?p=10678338#post10678338")

It's marked as being too big on the Natty download...
[[COLOR="Red"]http://hr.archive.ubuntu.com/ubuntu-cdimage/daily-live/[/COLOR]]("http://hr.archive.ubuntu.com/ubuntu-cdimage/daily-live/")

"ya-boot file is too big for ya-cd" :)

---

