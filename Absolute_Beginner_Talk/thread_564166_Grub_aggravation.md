---
title: "Grub aggravation"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by silverace99 on 2007-09-30
So I tinkered with grub's bootloader text file to move some things around....not the first time I've done it

but this time I do it and restart, and now Ubuntu doesn't even show up in my boot loader! I can't access my ubuntu anymore :(

does anybody know of a way that I can get back in to the OS?

---

### Post by eph1973 on 2007-09-30
What choices do you have on GRUB?

---

### Post by silverace99 on 2007-09-30
Right now I only have Windows XP as a choice for some odd reason

Is there anyway I can edit the grub file outside of Ubuntu, or get into Ubuntu itself?

---

### Post by eph1973 on 2007-09-30
Use the Ubuntu CD you used to install Ubuntu, boot from the CD.

You should then see all of your drives, including the drive your Ubuntu is installed in.  Check under the /media directory.  If you type ls you should see something like disk disk-1 disk-2 or whatever, depending on how many partitions you have.  From the /media directory, type ls disk, then ls disk-1 and so on until you see one that looks like your root directory from Ubuntu.  Change directories to that.
Let's say your Ubuntu root partition was under disk-1.  You would type the following:

```
sudo chroot /media/disk-1 su
sudo update-grub

```You'll then want to check your menu.lst that grub should have generated.  Open it up using:
```
sudo gedit /media/disk-1/boot/grub/menu.lst
```Check over the last part, as it sounds you are familiar with.  You want to make sure you still have access to your Windows partition, as well, so you should see a block that looks like this:

```
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```If it still looks hosed up, you can making a backup of menu.lst and deleting the old, and generating a new one one by typing:
```
sudo cp /media/disk-1/boot/grub/menu.lst /media/disk-1/boot/grub/menu.lst.bak
sudo rm /media/disk-1/boot/grub/menu.lst
sudo update-grub

```Then, of course, you are going to need the Windows bit I posted above manually to the end of the file, so you still get Windows as a choice on GRUB.

Let me know if this works out for you.

---

### Post by silverace99 on 2007-10-01
Ok! I used the live cd to access ubuntu, fixed the grub file, and now I'm back in business. Thanks for your help :)

---

