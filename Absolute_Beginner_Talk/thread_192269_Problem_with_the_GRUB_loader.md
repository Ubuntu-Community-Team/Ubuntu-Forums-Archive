---
title: "Problem with the GRUB loader"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by Detro on 2006-06-08
Yes, I'm a Linux newbie - so please don't flame too hard :wink: 
I've tried to edit the GRUB loader by using gedit. But now, whenever I try to load either the Ubuntu OS or the Windows XP OS this happens :
Savedefault
Boot 
Error 8: Kernel must be loaded before booting.

Is it possible to ever make my computer boot an OS again?
Feel free to help and flame me - but not just flame ;)

---

### Post by Jagot on 2006-06-08
You can restore grub:

[http://ubuntuos.com/2006/03/howto-restore-grub](http://ubuntuos.com/2006/03/howto-restore-grub)

---

### Post by Jagot on 2006-06-08
oops.  double posted.

---

### Post by grandpa-geek on 2006-06-08
Hopefully, you copied the grub config file (grub.conf on some OS's, something.1st on Ubuntu).  So just restore it.  If you used gedit and didn't save it several times, there may be a file out there with a ~ at the end of the name.  That is the previous version before your last save.

Otherwise, the best thing to do is find an example and follow it.  I know there will be something like the following:

title (whatever you want to appear in the menu)
root (hd0,1)
kernel something root=something_else
initrd more stuff.

The (hd0,1) (where 1 is replaced by whatever) tells grub where to look for the kernel and other stuff.

For windows there will be something about rootnoverify and a chainloader that all points to the Windows partition.

I hope this helps.

---

### Post by hajk on 2006-06-08
If the OP has not yet tried to run grub-install after editing /boot/grub/menu.lst, then 
all he needs to do is edit it as indicated by grandpa-geek. He can do that by booting 
with the Dapper liveCD (or with the Knoppix liveCD), then mount the partition the file is in, and edit it.

A chroot is required, however, if he has tried to install grub from some other partition...

---

### Post by catlett on 2006-06-08
Do you have the Ubuntu live cd? If you do we can mount your ubuntu hard drive with the live cd. Then we can get to your grub menu and rewrite it. When you reboot from the live cd after the editing, grub will work again.
First, Do you have the Ubuntu Live CD? (the new Dapper install cd that installs from the Dapper desktop, is a live cd and we can use that or we can use the Ubuntu Breezy live cd. Actually we can use any Live cd but Ubuntu would be the easiest because the commands are the same.)

---

### Post by Detro on 2006-06-08
Thank you all for your great help and support, but after trying numerous times, both following your suggestions and searching the web, I decided to take the easiest way: format. Now everything seems to be working just fine
But thanks again for helping a newbie who didn't know what he was doing :grin: 

Cheers from a hopefully more experienced Ubuntu user in the future 8-)

---

### Post by catlett on 2006-06-08
Any time you change something, make a backup first . In linux it is easy. The command is "cp". So next time you change your grub menu, do this first. ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
``` Then if there is a problem, all you do is this ```
sudo cp /boot/grub/menu.lst_backup /boot/grub/menu.lst
``` and your changed menu will be replaced with your backup.

P.S. If you had a backup like this, the live cd rescue would have been simple. We would  boot the live cd. Mount the partition and then execute the cp command to replace the file with the backup,. Problem solved.
Anyways, this is just for future reference. Glad you're up and running again.

---

