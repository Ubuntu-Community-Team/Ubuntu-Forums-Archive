---
title: "GRUBless startup"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-11-27
I am currently using ubuntu on a dedicated desktop and loving it.  Now I want to play with it on the go by using ubuntu on my laptop.  
The problem is when I do this I am going to have to to a tri-boot (XP, Vista, Linux)  
I was wondering if there is a way to get ubuntu to run wihout GRUB or if there is a distro that doesn't use it.

---

### Post by master_kernel on 2007-11-27
Why do you want it without GRUB if you're going to tri-boot?

---

### Post by climatewarrior on 2007-11-27
Im not 100% sure but as far as I know the windows bootloader can only boot windows and thus your only option is GRUB or Lilo but from what Ive heard GRUB is better so I guess its probably better to stick with Ubuntu's default bootloader. Also from what Ive heard Windows doesnt like to be isntalled second so its better if you first configure the VIsta/XP dual boot and then install Ubuntu.

---

### Post by irw on 2007-11-27
You can load linux from the Windows bootloader -  I have done it in the past, until I finally got rid of Windows a year ago.

I tried various methods; i think [Bootpart]("http://www.winimage.com/bootpart.htm") was the one that worked the best - the windows boot manager loaded Grub, from which Linux was loaded (with 0 sec delay).

I cannot remember all the details, but the bottom line was that it worked  :)

---

### Post by drcranium on 2007-11-27
You can use EasyBCD to configure the boot but you're better off using grub.  The Ubuntu install does a pretty good job of detecting other OS's.  And editing /boot/grub/menu.lst is not too complicated.
EDIT:
[http://www.pcworld.com/downloads/file/fid,66204-order,1-page,1/description.html](http://www.pcworld.com/downloads/file/fid,66204-order,1-page,1/description.html)

---

### Post by bodhi.zazen on 2007-11-27
Why ? GRUB is so much easier :)

Searching Ubuntu forums yield the best guide : [http://ubuntuforums.org/showthread.php?t=220452](http://ubuntuforums.org/showthread.php?t=220452)

See also :

[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx)

Or with GRUB : [http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

---

### Post by Dapman01 on 2007-11-28
The reason why I don't like GRUB is because everytime I use it I get the GRUB Error 2 message and I have never had help on the forums forfiguring out how to fix it

---

### Post by Computer Guru on 2007-11-30
> **drcranium said:**
> You can use EasyBCD to configure the boot but you're better off using grub.  The Ubuntu install does a pretty good job of detecting other OS's.  And editing /boot/grub/menu.lst is not too complicated.
EDIT:
[http://www.pcworld.com/downloads/file/fid,66204-order,1-page,1/description.html](http://www.pcworld.com/downloads/file/fid,66204-order,1-page,1/description.html)

Here's a picture-by-picture tutorial on dual-booting Ubuntu and Vista with EasyBCD:
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

