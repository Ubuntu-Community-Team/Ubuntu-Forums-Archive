---
title: "Resizing my Ext3..yes I tried stuff"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by tequilaiam on 2007-05-31
Hi, I recently installed Feisty, KDE flavor and like it so far.  So much that I'd like to start installing a bunch more software.  I'm currently dual-booting and need to keep it that way for now.

My linux partition is about 10GB and resides in the middle of the HD.   I added a few gigs of fat32 for kubuntu-XP file sharing and freed up some space direcetly after the kubuntu section successfully with QTPart off the install disk.  

I cant get QTpart to resize.  I tried the istructions here: [http://www.extremetech.com/article2/0,1697,1928205,00.asp](http://www.extremetech.com/article2/0,1697,1928205,00.asp)

and got the ext3 converted to ext2 but when I tried resizing with QTP it popped up a blank info box and nothing happened.
Here's a little more info that will hopefully be helpful to someone out there:
My swap partition is directly after the Ext3 one.  They both show up in QTP under the same extended partition tree.  The Fdisk -l output is this:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1...*............1.......6715....53938206....7..HPFS/NTFS
/dev/sda2............8567........9729.....9341797+...b..W95 FAT32
/dev/sda4............6716........8090....11044687+   5  Extended
/dev/sda5...*........6716........8026....10530576   83  Linux
/dev/sda6............8027........8090......514048+  82  Linux swap / Solaris

I imagine I can't resize the ext3 part because the swap is in the way.  But I can't move the swap either.  Any ideas?
Can I delete the swap, resize sda5 then recreate the swap?  I'm worried that will mess up my system.  I really dont want to reinstall - it took me forever to get my internet working on this lame laptop.

Any help or ideas is greatly appreciated!

---

### Post by ryanVickers on 2007-05-31
could you post a screenshot of your current hd setup (from gparted)

Just so you know, it can resize most things from the right side, but not the left.  for more details, see "Gparted > Features" menu.  some terminology:

move = resize from left/actually move
grow/shrink = resize from right

I once deleted swap and it works fine, but it's sometimes a real pain to get it to recognize the new one you've made.  It doesn't hurt anything, unless while you have no swap you fill up all your ram :p

---

### Post by tequilaiam on 2007-06-01
Ok, I grabbed a pic of QTParted on the install CD.  The first windows partition has windows on it, the last one is intended to be for a shared space.  Attached as .jpeg

Thanks!
:D

---

### Post by ryanVickers on 2007-06-01
Try this: (for slight enlargement - simple)
1. expand the extended into empty space
2. move swap
3. expand the ext3

OR

Try this: (for huge enlargement - complex)
1. expand the extended into the empty space
2. shrink your large ntfs to about half
3. make a ext3 at the start
4. copy your current ext3 into the new one (positioned at the end of the big ntfs)
5. remove the first ext3
6. shrink the extended to match swap, if not possible, remove extended then recreate swap in empty space
7. expand the new ext3 to fill the space - then your done!

It should work fine, I know gparted can do it, but if qtparted can't, I think you can just download gparted and add it on, even from the live disk!

When your done (using the complex method, if chosen) it should look like this

edit: p.s. should warn you, *sometimes* shrinking a windows partition can slow it down bad!  (~logon 3 times longer, doing stuff ~ -40% speed)

---

### Post by tequilaiam on 2007-06-01
Thanks for the tip - I think QTparted may have been the issue.  I did get it working but in a round-about way.

1st I deleted the journal per the instructions in the link in my first post
then booted to windows and used partition magic 8 to expand the extended portion of the partition and move/resize the swap.

Then booted back with the install disk and began installation using the manual partition selection and resized the ext3 (which became ext2 after removing the journal)
Then added the journal back on.

QTparted just wouldnt cooperate - Gparted may have but the utility in the install process worked.  

Everything seems to be working ok now. :)

---

### Post by ryanVickers on 2007-06-01
Glad to hear it!  I didn't know you could still get partition magic; I was under the impression everyone just used the live ubuntu cd whenever they had to change that stuff :p

---

