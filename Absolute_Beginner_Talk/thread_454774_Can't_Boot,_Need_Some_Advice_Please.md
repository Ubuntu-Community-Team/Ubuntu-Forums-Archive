---
title: "Can't Boot, Need Some Advice Please"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Thanatos10 on 2007-05-25
Well, I thought I'd give Ubuntu another try after a year away.  It is a great operating system, but I always felt I was playing catch-up.  Now I have more time to devote to learning a new operating system so I'm back.  But I cant seem to be able to get it to boot-up with my current system configuration.

My first hard drive is partitioned into two drives (I thought).  The fist XP the second partition is a catch all file storage closet as it were, for misc. files, etc..  The second drive is also two partitions (well three now).  The first partition is Vista, the second and third are Ubuntu and a swap.

I'm using the Vista bootlaoder and I can boot into XP (default) or Vista without problem.  Then, I loaded Ubuntu onto the second drive, second partition using the live CD.  When prompted for a bootloader I selected GRUB to the partition not the MBR.  In the advanced option I selected /dev/hdb2.  I used easyBCD to add the Ubuntu entry and everything looks OK from the end.

Now when I try to boot into Ubuntu I get a GRUB> prompt.  I've tried to look through the menu.lst file, and from my very limited knowledge look fine to me.

Here are my fdisk -l and menu.lst printouts:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       12560   100888168+   7  HPFS/NTFS
/dev/hda2           12561       19929    59191492+   f  W95 Ext'd (LBA)
/dev/hda5           12561       19929    59191461    7  HPFS/NTFS

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       17751   142579552+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hdb2   *       17752       23221    43937775   83  Linux
/dev/hdb3           23222       24321     8835750   82  Linux swap / Solari


GRUB menu.lst file;

title           Ubuntu, kernel 2.6.20-15-generic

root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=8a9df627-b1a3-4be9-8f1
0-05af611972d0 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=8a9df627-b1a3-4be9-8f1
0-05af611972d0 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating system

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda5
title           Microsoft Windows XP Professional
root            (hd0,4)
savedefault
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

Hope someone out there can help, thanks for your time and let me know if you need any additional info

Scott....

---

### Post by drowner on 2007-05-25
it looks like your first drive is partitioned into 3.

And grub has an entry for that third partition....hda5.


Whats on there?

---

### Post by Thanatos10 on 2007-05-25
Well, this will sound stupid, but I'm not sure.  When using file explorer in windows it only shows Drive C: (primary windows) and E:, a trash partition where I keep failed xBase programs and code that I thought I need again (but never do).  Drive D: is my CD/DVD burner.  However, gpart clearly shows that third partition.

So, I'm not sure what that is.

Scott.

---

### Post by drowner on 2007-05-25
ok, so i had another look.

It seems like you have two entries in the fdisk for that trash partition. Weird, hey?

I'm not sure why that is.


If you are sure that you do not have windows XP installed to the hda I think the simplest solution would be to remove the entry for the hda5 from the menu.lst

make sure you back up the menu.lst first.

---

### Post by Thanatos10 on 2007-05-25
I'll try that and let you know.

---

### Post by Thanatos10 on 2007-05-25
Now I get Error 8 - Must load kerenl first.

Anyother advice is appreciated.

Scott

---

### Post by drowner on 2007-05-25
Good news: first problem solved ;)

Edit: sorry, misread your entry.

---

### Post by Thanatos10 on 2007-05-25
Oh well, thanks for your time.  It was worth a the try to give Ubuntu another shot (kinda fun in a way).  From what I could see from the live CD Ubuntu looks like it's really matured nicely in the past year or two.  Maybe I can try again next year.  Well, windows it looks like I'm back :(.

Again, thanks for your time.

Scott.

---

### Post by drowner on 2007-05-25
There's no need to get rash!

I did a quick google search, and there are numerous instances of grub error 8's.
Often it is caused when your menu.lst doesnt point to the right kernel

Google = your friend

---

### Post by Thanatos10 on 2007-05-25
OK, I'll see what I dig up from google.  I was going to try super grub, but can't find a widows iso.zip file anyplace.  From what I read it was supposed to go in there and fix everything automatically (exactly what I needed).

Scott.

---

### Post by drowner on 2007-05-25
Does the iso need to be an iso.zip?

Can't you burn an iso under windows?

---

### Post by Thanatos10 on 2007-05-25
I guess I mis-phrased that.  The iso file is usually ziped in the windows world for size.  It doesn't have to be ziped.  If can manage it from the live cd then a tar file.  It's all the same once I get onto a CD.

---

### Post by drowner on 2007-05-25
you should be able to extract the tar from the live cd somewhere where you can read it in windows.

Obviously, you wont be able to burn it ;)

---

### Post by Happy_Man on 2007-05-25
Actually, my copy of the Super Grub .iso was never zipped.... odd isn't it?

---

### Post by Thanatos10 on 2007-05-25
Where did you get it?  Googles search only finds dead links.

---

### Post by Happy_Man on 2007-05-25
I don't remember. Must have been nearly a year since I last used it... sorry.

---

### Post by Thanatos10 on 2007-05-26
Downer, thanks for your help.  The problem was in the partitions themselves.  When they were created the first time, or rather converted from the windows NFTS(?)  something went wrong.  I went back and tried to correct the problems with gpart and it couldn't do anything, but tell me there were problems. So I booted back to windows started partition magic and it was able to delete the partitions and re-create them.

After that I just reinstalled from the live CD, and I'm here in Ubuntu trying to figure out were to start, looks like a lot to learn.  But that's part of the fun.:p

Thanks for your time.

Scott

---

### Post by Computer Guru on 2007-05-26
Here's a good guide, since you're starting from scratch:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

While installing Ubuntu when presented with a screen that has a button "advanced" on it, select that to change the location of GRUB to the Ubuntu partition instead of the MBR.

---

