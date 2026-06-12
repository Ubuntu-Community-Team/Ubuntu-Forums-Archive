---
title: "Can’t install ubuntu 16.04 on mac mini"
date: 2017-08-17
forum: Apple Hardware Users
---

### Post by boblazar on 2017-08-17
I have a nastyproblem that I just haven’t been able to solve. I have a mac mini(late 2009) and I really would love to replace the osx with ubuntu. Ihave read all the tutorials I can find on the topic with no luck, soI have to ask some personal help. The dvd-drive is deceased, so theonly option is bootable USB.




So, I have managedto make an bootable usb  but when I get to the GRUB menu (viarefind), where I can choose between installing, or trying ubuntuwithout installing it ”black screens” regardless the choice I’vemade. I suppose it could be graphic card/driver related problem... Ifound some various instructions to edit the commands before bootingby pressing ’e’ to enter the editing mode. I have tried to editthe lines but regardless the changes, it won’t reboot by pressingthe suggested ’ctrl-x’ or ’F10’. Absolutely nothing happens. 


At this point, I’mwell passed frustration, so I would be extremely pleased if anyonecould help me out with this one...

---

### Post by bench on 2017-09-19
Hi @boblazar,

Have you seen this thread that I posted a few years ago: [https://ubuntuforums.org/showthread.php?t=2287767]("https://ubuntuforums.org/showthread.php?t=2287767").

I haven't got the same model as you (mine is older), but the technique may still work.

When you boot into OS X in the "About this Mac" screen, what model number have you actually got (eg. MacMini 2,1).  You could find out if this has a 32-bit EFI like the 1,1 does, in which case, my thread will help you.

Cheers.

---

### Post by capriotti-carlos on 2017-10-16
boblazar, Bench's comment is very accurate. 

macminis 1,1 and 2,1 can be tricky to handle, installing Ubuntu.

I had to use a dirty trick to get my 1,1 to run Ubuntu: I used a DEBIAN CD installer to install a small Debian system on it, and then installed Ubuntu.

This is due to a problem on hose early macminis: the EFI is 32 bits, while the system is 64, and Ubuntu's installer cannot handle that properly, while Debian can. 

It is not ideal, I know, but it is a solution that will save you hours of frustration. Remember, boot from CD and not from USB, which does not work. After that you will have a very happy macmini on Ubuntu.

---

### Post by ratell on 2017-10-17
I was installing on an Imac and having endless troubles.
The first trick is setting nomodeset when you edit grub.
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

That worked to get installed but after a kernel update I got black screens again. Ultimately changing the following line allowed the computer to boot.
GRUB_GFXPAYLOAD_LINUX=auto

I'm a newbie so have no idea why these things worked but it seems worth a try.

Good luck

---

