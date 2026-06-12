---
title: "trouble installing xUbuntu"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by unicycler on 2006-06-09
I am trying to make good use of probably not good hardware. I have a scrap computer that was given to me. All I know is that there is a PIII sticker on the side. I tried using the Ubuntu 6.06 disk, but it froze while loading the desktop manager. I downloaded and made an xubuntu cd, and it can boot, but when I click to install, nothing happens. Is there a way I can install from the command line?

---

### Post by loell on 2006-06-09
i think you have to use, the xubuntu alternate cd

---

### Post by glotz on 2006-06-09
When you boot with the CD, hit esc to exit the graphical front and type in **server** to install the installation without desktop. Then install Xfce. Here's instructions [https://wiki.ubuntu.com/InstallingXubuntu](https://wiki.ubuntu.com/InstallingXubuntu)

Then you might want to upgrade to i686 kernel. See [http://www.ubuntuforums.org/showthread.php?t=85917](http://www.ubuntuforums.org/showthread.php?t=85917)

And then you'll need to upgrade your signature! Tertiary: PIII something :)

---

### Post by unicycler on 2006-06-09
I get the prompt
```
boot:
``` where I enter "server" and it says kernel image cannot be found: server

After running the memory test, ubuntu showed that the system is 670MHz PIII with 128 MB RAM

---

### Post by glotz on 2006-06-09
Try hitting the function keys when you're in the boot menu, it should show you the correct command. (Or then they've just changed it since 5.10...)

670Mhz is just fine but 128 megs of memory is quite little. Maybe Xubuntu will work on it though...

---

### Post by gbw69 on 2006-06-09
Hi guys
I installed ubuntu from the internet, and it worked fine for a bit.
after some updates it wouldn't start and for some reason i couldn't boot back into windows. i ran a dos command 'fdisk /mbr' that removed the grub menu.
Any idea how i can get it back?

---

### Post by anaconda on 2006-06-09
Sorry if this is a stupid comment, but in xubuntu 
You must double-click the install icon...

Not just click.

---

### Post by unicycler on 2006-06-09
I quintuple clicked the shit out of that install icon, but it wasn't doing anything. I just finished installing from my ubuntu 5.x as a server install and I am working to get it 6.06.

---

