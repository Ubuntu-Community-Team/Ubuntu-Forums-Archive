---
title: "Grub not booting OSX"
date: 2015-08-25
forum: Apple Hardware Users
---

### Post by UpSignal on 2015-08-25
Hello guys! Hope you can help me out here. 
Some info first:

Dualbooting Xubuntu 15.04 and OSX Yosemite. 

I add the following line to /etc/grub.d/40_custom

> menuentry "Mac OSX" {
 exit
}

But when trying to boot it, the following errors occur

[[img]http://s12.postimg.org/8uksgd5u1/Untitled.jpg[/img]](http://postimg.org/image/8uksgd5u1/)

Any ideas on what i should do? At first grub not even showed up. It booted directly to xubuntu and if i want to go OSX i had to use the alt key. But i ran ubuntu boot-fix, and now i have grub access but cant get to osx from there. 
Heres my grub:

> GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="libata.force=noncq"
GRUB_FONT=/boot/grub/DejaVuSansMono.pf2

---

### Post by yancek on 2015-08-25
I can't see the entry you posted doing anything.  All you are telling it to do is 'exit'.  Your image shows you are using UEFI so did you install Xubuntu in UEFI mode?  If you have the boot repair software, run it again and select the option to Create Bootinfo summary and post the output here.  Someone familiar with a Mac might have an idea.

---

### Post by UpSignal on 2015-08-25
yeah, i installed as uefi,
i almost forgot...boot repair ended with an error, which is here:

> [http://paste.ubuntu.com/12193954/](http://paste.ubuntu.com/12193954/)

---

### Post by howefield on 2015-08-26
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by luciano.x on 2015-08-26
Did the ubuntu installer detected OS X Yosemite? Mine did not and it just boot into ubuntu like yours. That makes sense well if you do have only 1 SO why a boot manager?
Anyways I assume your entries in ESP are OK since you can still boot into OS X. 

rEFInd might be a solution. It worked here (iMac). 

**install rEFInd under OS X. **[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html) download binaries zip.
Open terminal, cd into refind's directory and execute: ./install.sh
Shut down (not reboot) and check if rEFInd menu shows up. It should shows at least boot EFI/grubx64.efi, MAC OS X from [partition], OS X recovery and so on.
Now reboot just to make sure it is working.

Hope it helps.

---

### Post by crystalocean on 2015-08-27
> **luciano.x said:**
> Did the ubuntu installer detected OS X Yosemite? Mine did not and it just boot into ubuntu like yours. 

You can hold the alt/option key when you hear the apple startup chime during boot and you will be able to select your OS X partition.

Also, consider installing rEFInd to its own partition--it makes it easier to uninstall rEFInd later (just delete the partition), etc.

---

