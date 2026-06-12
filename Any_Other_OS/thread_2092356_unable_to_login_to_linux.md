---
title: "unable to login to linux"
date: 2012-12-07
forum: Any Other OS
---

### Post by ashbekah on 2012-12-07
Sorry for the really stupid post. I recently got a new computer. It has  linux mint. Anyway, when I first got it about a week ago, I set it up  with only one account- mine- the admin account. So I am off of the  computer for a week, and I go to log back in, and it says either wrong  user name or wrong password. Eventually I reset my password via [http://community.linuxmint.com/tutorial/view/339](http://community.linuxmint.com/tutorial/view/339)  .... So I know it isn't the password. I have tried everything for the  username. I do not have an installation disk or anything to reinstall  from. Any ideas how I could figure it out or reset it. If there's  something I can go to in GRUB like how I reset the password, and you  tell me the directions I could probably do it. Any help would be great! Oh and I do not have the Cd. I bought it as is from the store.

---

### Post by oldfred on 2012-12-07
Moved to OtherOS since Minty.

From liveCD if you look in /home you will see the user.

/home/fred

At grub go to command line. Instead of looking at /boot look at /home and do an ls?

manual boot instructions, but should be similar to look at any partition.
       Adjust drive, partition to your install:
ls (hd0,5)/  # Do you see 'vmlinuz' and 'initrd.img' ?
ls (hd0,5)/boot # Do you see the kernel and initrd image files ?
ls (hd0,5)/boot/grub # Do you see lots of *.mod files and grub.cfg ?

---

### Post by critin on 2012-12-07
>  I do not have an installation disk or anything to reinstall  fromIf you have another computer or can use a friends, go to   linux mint site and download the iso image.  That is a copy of your system.  If you're using a cd/dvd, burn the image to make it bootable.  

If you can boot from an usb flash drive, use unettbootin to make a bootable usb stick.  this will give a Live copy of your system and you can reinstall the OS from it if you can't fix it.

This time use a simple user name and password that you cannot forget.  I do.
You might want to try ubuntu 12.04 just to try it out.  You don't have to stay with mint.  lol

---

