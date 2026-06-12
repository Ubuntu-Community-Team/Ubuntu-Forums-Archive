---
title: "Ubuntu without Grub"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by howardepgco on 2007-08-14
Hello.

I have a PC with three hard drives.I want to install Ubuntu on one,but I want to be able to launch it from the BIOS by setting the Ubuntu drive as the boot drive and skip the grub bootloader. Can I do that?

---

### Post by Blutack on 2007-08-14
The grub is the bootloader, it is needed to start up the kernel.  If you do
sudo gedit /boot/grub/menu.lst
adjust the timeout to 1
and run
sudo update-grub
the timeout will drop to 1 second and you won't realise its there.

---

### Post by howardepgco on 2007-08-14
So what you are saying is that even if I only had one hard drive in my computer and I only had Ubuntu installed I would still need Grub?

---

### Post by Blutack on 2007-08-14
Yes.  Windows has a similiar, more limited system called NTLOADER - they just hide it with a flashing cursor.  An explanation of how it all works is here:
[http://en.wikipedia.org/wiki/GNU_GRUB#GRUB_boot_process](http://en.wikipedia.org/wiki/GNU_GRUB#GRUB_boot_process)

---

### Post by st33med on 2007-08-14
I'm curious... Don't try what I'm about to tell you, or do it at your own risk.

I've always wondered if I put a '0' or 'None' in that list, would it immeadiately go to Ubuntu, or just remain at the menu...:-k

'None', in theory, should mean no timer, it remains on the grub menu. '0' should skip the grub menu.

And what if I put a decimal number in there... What would happen if I comment the line? Hrmm...

---

### Post by howardepgco on 2007-08-14
What I want to try to do is keep my windows seperate.I don't want to have to pick the O.S I want to use  after the bios. I always run into big problems with this and have to take drastic steps to get my windows back.

---

### Post by Blutack on 2007-08-14
> I'm curious... Don't try what I'm about to tell you, or do it at your own risk.

I've always wondered if I put a '0' or 'None' in that list, would it immeadiately go to Ubuntu, or just remain at the menu...

'None', in theory, should mean no timer, it remains on the grub menu. '0' should skip the grub menu.

And what if I put a decimal number in there... What would happen if I comment the line? Hrmm...

It doesn't time out, it just sits.  Don't even try decimals.  I really don't think its a wise idea to muck with the bootloader too much.  Anyway, the second is handy for those Argh!  Need Recovery Mode!  Moments.  And ntldr takes that long anyway...

---

### Post by Blutack on 2007-08-14
Howard, yes you can.  In the installer for advanced options, where you get to choose where the bootloader goes, pick the drive you have installed ubuntu on.  Although are you sure your bios lets you do that?

---

### Post by howardepgco on 2007-08-14
Yes it does.That would make my install a lot safer.I will post how it worked.

---

### Post by w4ett on 2007-08-14
> **howardepgco said:**
> Hello.

I have a PC with three hard drives.I want to install Ubuntu on one,but I want to be able to launch it from the BIOS by setting the Ubuntu drive as the boot drive and skip the grub bootloader. Can I do that?


I have done exactly the same thing on one of my machines......What I did was just disconnect all of the HDDs except the one you want to install Ubuntu on...set it as the master drive...install ubuntu normally from the live cd using the whole drive for the installation.  Complete the installation, reset this drive back to slave and reinstall all remaining drives.  Upon bootup press F11 (or whatever key that controlls the drive boot order list) and select your desired drive to boot from.  Grub will still be there on the Ubuntu drive so you can select normal or recovery boot  and the individual kernels you may have installed, but it won't affect the MBR installation on your master windows drive.

Good luck

---

### Post by Blutack on 2007-08-14
w4etts method is way better than mind, although does involve opening your case.  Though with 3 drives I don't imagine it bothers you much.

---

