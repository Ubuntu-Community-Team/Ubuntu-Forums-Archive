---
title: "Installation directory"
date: 2005-07-28
forum: Absolute Beginner Talk
---

### Post by SweetTeaTurner on 2005-07-28
I have been searching for a while, and here is the problem. I used a relatively small hard drive for the installation of ubuntu so I may very well run out of space soon. When this occured in Windows I simply changed the default installation directory to my other hard drive, but I can not figure how this is done in ubuntu. Any help would be appreciated. Also I probably need to change the default download directory for apt-get?

---

### Post by pestilence4hr on 2005-07-29
[QUOTE=SweetTeaTurner]I have been searching for a while, and here is the problem. I used a relatively small hard drive for the installation of ubuntu so I may very well run out of space soon. When this occured in Windows I simply changed the default installation directory to my other hard drive, but I can not figure how this is done in ubuntu. Any help would be appreciated. Also I probably need to change the default download directory for apt-get?[/QUOTE]

I think the solution to this will be a little more involved in Ubuntu.  The most straightforward way would be to create a new partition, mount it, then "sudo cp -a / /newroot".  Then change the location of / in /etc/fstab and /boot/grub/menu.lst (here you should change what's under kopt=), run update-grub, and reboot.  You probably should do this from a rescue CD of some kind (hoary live would work, I bet).

Another idea is to make a partial move -- i.e. the same as above, only this time you only move /usr or /home to a new partition.  If the real space constraint is coming from /home, you might consider doing this.  My personal preference is to have a separate /home partition at the very least, so that if I choose to change the OS I don't have to mess with /home.

---

