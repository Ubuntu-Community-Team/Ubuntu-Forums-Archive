---
title: "Installing Ubuntu over Mandrake 10.1"
date: 2005-08-21
forum: Absolute Beginner Talk
---

### Post by jacatone on 2005-08-21
I wanted to replace Mandrake 10.1 with Ubuntu on my dual boot XP/Mandrake setup. Would I have to use Partition Magic to wipe my Mandrake partition clean first or can I just do it? Could someone give me a link to how this would be done? Thanks.

---

### Post by mit on 2005-08-21
If you boot to the Ubuntu CD it should go through set-up and detect there is 2 operating systems already on the hard drive and ask you where you want to install.
Let us know how you get on  :)

---

### Post by Henrik on 2005-08-21
I did this a few days ago on a friend's computer. We were using 5.10, but I think the 5.04 installer is similar. Just run the installer until you get the partitioning step. You will then see the mandrake partitions: most likely a system partition '/', a home partition '/home' and a swap. If you want to wipe the whole system including the data (ie. you have backups), then just delete those partitions and allow the installer to auto-partition the free space. 

Alternatively you could keep the mandrake partition as your /home partion (just leave it where it is) though this will start you off with cruft in the home directory of your new system. You could avoid this by choosing a new user name.

We decided to keep the data partition but leave it unmounted. We then mounted it after the install was complete is a sub-directory of his home directory. He has now sorted through his old files and finally we will convert that space to a fat32 partition that he will use to transfer files to and from WinXP (which was set up as NTFS).

So, you have some options :)  Good luck!

If you do use partition magic I would suggest you just leave the space blank and allow te Ubuntu installer to partition it.

---

