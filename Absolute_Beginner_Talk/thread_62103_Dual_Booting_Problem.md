---
title: "Dual Booting Problem"
date: 2005-09-03
forum: Absolute Beginner Talk
---

### Post by Unit #134679 on 2005-09-03
I have two drives, Windows XP and Ubuntu. When I installed Ubuntu, I made Windows slave and the Ubuntu drive master. Since I couldnt boot Windows as slave, I asked around and switched Windows to master and Ubuntu to slave, just now GRUB isnt loading and on top of that, I tried reinstalling it to the master and slave drive and it wouldnt work. Any ideas?

---

### Post by Strangerdave on 2005-09-03
You might want to try going back to the beginning and trying once again.  Hook up the drive that has windows as master.  From what I gather you aren't booting right?  Well if you stick your Windows CD back into the CD drive, and boot from it.  Choose to run the rescue program.  After typing in your passwd, you will be taken to a DOS command prompt.  Type:  bootcfg /rebuild.  Then type: fixboot <enter> fixmbr <enter>.

Once you get windows up and running again, you can either wipe your other drive clean with fdisk, or try reinstalling Ubuntu.

I think that you might want to leave windows as master, and ubuntu as slave.  When you start, you will always be asked which OS you want to boot into.  I too have two drives with windows as master and ubuntu as slave.  However, I am using Windoze less and less, so it may eventually disappear.

Hope this helps. :) 

-SD-

---

### Post by Unit #134679 on 2005-09-03
[QUOTE=Strangerdave]You might want to try going back to the beginning and trying once again.  Hook up the drive that has windows as master.  From what I gather you aren't booting right?  Well if you stick your Windows CD back into the CD drive, and boot from it.  Choose to run the rescue program.  After typing in your passwd, you will be taken to a DOS command prompt.  Type:  bootcfg /rebuild.  Then type: fixboot <enter> fixmbr <enter>.

Once you get windows up and running again, you can either wipe your other drive clean with fdisk, or try reinstalling Ubuntu.

I think that you might want to leave windows as master, and ubuntu as slave.  When you start, you will always be asked which OS you want to boot into.  I too have two drives with windows as master and ubuntu as slave.  However, I am using Windoze less and less, so it may eventually disappear.

Hope this helps. :) 

-SD-[/QUOTE]
 The beginning was Windows as slave and Ubuntu as master. I *can* boot to Windows fine, but GRUB doesnt load so I cant boot into Ubuntu. I want to fix this without wiping out any drives. As we speak I'm on my Windows drive thats master and Ubuntu is slave

---

### Post by Unit #134679 on 2005-09-03
No one can help?

---

### Post by Steve1961 on 2005-09-05
Don't be downhearted, there is a solution.  You can install Ubuntu as your first master drive and XP as the slave, but you have to trick XP into thinking it's on the first primary partition of the master drive.

If you swap the discs round you won't be able to boot the windows drive from the grub menu to start off with, but once you're in Ubuntu you can modify your grub /boot/grub/menu.lst file and insert a couple of extra lines in the XP entry so that it looks something like:

title windows XP
map (hd0) (hd1)
map (hd1) (hdo)
root (hd1,0)
makeactive
chainloader +1

This tricks windows into thinking its the first hard drive so it will boot, although Grub isn't fooled as it still sees the second drive as the slave. As linux is now your first hard drive you don't need to install grub on the mbr of the windows disk. I haven't personally tried this but I've just read an article in Linux Magazine that covered this issue.  It's also mentioned in good old Linux in a Nutshell.

---

### Post by Unit #134679 on 2005-09-05
Steve1961, thanks for the reply...but I already reinstalled Ubuntu and set it up back to the way it was before. Thanks though :)

---

### Post by Steve1961 on 2005-09-05
No problem, glad you've got everything working.

---

### Post by Unit #134679 on 2005-09-05
Yep, thanks...but now I got another [problem](http://ubuntuforums.org/showpost.php?p=335434&postcount=1) ...haha

---

