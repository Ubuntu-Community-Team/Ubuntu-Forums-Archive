---
title: "Problem with break=bottom on Grub after 6.10 installation"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by EGE-FB on 2007-03-26
I installed 6.10 on my Toshiba laptop (with X700 ATI Radeon graphics card) after reading these two links: 

[http://ubuntuforums.org/showthread.php?t=389980&highlight=install+grub+remove+break%3Dbottom](http://ubuntuforums.org/showthread.php?t=389980&highlight=install+grub+remove+break%3Dbottom)
[https://wiki.ubuntu.com/EdgyKnownIssues/59618](https://wiki.ubuntu.com/EdgyKnownIssues/59618)

In the 2nd link, at the end, it says 

If you use the Desktop CD to install Ubuntu to your hard drive, it will (in some cases, this has been reported in Dapper, but I have seen the opposite in Edgy) copy all extra boot parameters (that you added when booting the CD) to your grub configuration so that they will be used every time you boot. Therefore, after installation, edit /boot/grub/menu.lst and make sure there is no break=bottom on the # defoptions= line:

sudo nano +86 /boot/grub/menu.lst

I did this but when I press "e" to edit in the grub menu and look into the "kernel" portion, the "break=bottom" part is still there, even though I deleted it with the "sudo nano +86 /boot/grub/menu.lst" command before. This prevents me from booting into Ubuntu, unless I manulaly delete the "break=bottom" bit before each boot up. 

How can I completely delete this "break=bottom" part so that Ubuntu boots automatically without me manually deleting "break=bottom" each time? :(

---

