---
title: "Dual Boot Help"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by gubemton on 2007-11-21
Hello, I just received Ubuntu 7.10 in the mail today. And I was following the steps in [this link]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first").
I get to step 7 of 7 in the Ubuntu install but it does not display Vista/Longhorn on the Migration Assistant. I have 15GB of unallocated space and I clicked Manual on step 5 of 7. I do not want it to reformat my whole HDD since I have important University work on it. Any advice? Thank you!

---

### Post by Inxsible on 2007-11-21
It does not show it even in the Tutorial right ?

Don't worry, you won't lose any info on your other partitions as long as you don't format those partitions. Go ahead with the installation. Even when I installed, it didnt show any options to import anything from Vista.

---

### Post by jken146 on 2007-11-21
Presumably you have vista installed on a separate partition?  If so then all you need to do is install Ubuntu (on a different partition to vista), and it doesn't really matter if the migration assistant doesn't work, you won't lost any files.  Just be careful what you format at the partition editing stage.  If you're really worried you should back up your important files prior to installing Ubuntu.

---

### Post by gubemton on 2007-11-21
Yes Vista is already on a seperate partition. I will back up my files and try and hope for the best. Any other advice? Thank you.

---

### Post by Inxsible on 2007-11-21
> **gubemton said:**
> Yes Vista is already on a seperate partition. I will back up my files and try and hope for the best. Any other advice? Thank you.
I would suggest that you create a separate home partition, if you are not already doing so.

Saves you from a lot of grief in the future !

---

### Post by Bigbird999 on 2007-11-21
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I a good how to.  Also there are at least 3 other threads today on this subject with some help.

Just make sure you back up your data because any time you do major data reorganization or mess with partitions, you can lose your data.  It doesn't happen often, but it does happen!!!

"YOU DON'T HAVE TO BACKUP ALL YOUR DATA, JUST THE STUFF YOU DON'T WANT TO LOSE"

bb

---

### Post by gubemton on 2007-11-21
> **Inxsible said:**
> I would suggest that you create a separate home partition, if you are not already doing so.

Saves you from a lot of grief in the future !

Sorry, but what does that mean?

Wow, the community here answers things fast!

---

### Post by bluepowder7 on 2007-11-21
it means that you have Win Vista on one partition, then you have a few more partitions for linux to use (three, actually - a /home, a /root, and a swap).  you can set those up using the built-in partition editor that's on the live cd (which might crash after every operation, but it DOES do what it should), and then as you do the install, specify the newly made partitions as the appropriate mount points (obviously, keep track of which is which, so /dev/hda1 is for example a 50gig vista partition, and /dev/hda2 is your 20gig /home partition, and /dev/hda3 is your 10gig /root partition, and finally /dev/hda4 is a 2gig swap partition).

---

### Post by gubemton on 2007-11-23
Hello, I have Vista and would like to Dual Boot with Ubuntu 7.10 for University. I have the 7.10 CD and when I tried to install this happens after I make a 2GB swap.
[Click here for screenshot]("http://img510.imageshack.us/my.php?image=screenshotzn1.png")
I have Vista on 1 partition, my personal files on another, and the other is some windows stuff?
So it seems that I could only have 4 partitions for Gutsy? What should I do?

---

### Post by Dr Small on 2007-11-23
Have you read this guide on Dualbooting for Ubuntu ?
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

Dr Small

---

### Post by bluepowder7 on 2007-11-23
you can only have four PRIMARY partitions.  if you need more partitions, one of those four has to be made an EXTENDED partition, and then you can made a bunch of new LOGICAL partitions inside that extended partition space.  the extended partition is kind of like a "holder of other partitions"

---

### Post by samuel.rajesh on 2007-11-23
> **Dr Small said:**
> Have you read this guide on Dualbooting for Ubuntu ?
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

Dr Small

Read the blog in the above mentioned url and read the comments as well ,the author has described why you would need partitions and all

---

### Post by overdrank on 2007-11-23
> **gubemton said:**
> Hello, I have Vista and would like to Dual Boot with Ubuntu 7.10 for University. I have the 7.10 CD and when I tried to install this happens after I make a 2GB swap.
[Click here for screenshot]("http://img510.imageshack.us/my.php?image=screenshotzn1.png")
I have Vista on 1 partition, my personal files on another, and the other is some windows stuff?
So it seems that I could only have 4 partitions for Gutsy? What should I do?

HI you can delete the swap and make that a extended partition and then you will be able to create your partition to install ubuntu. You are limited to 4 partition to a drive unless you have a extended partition.

---

### Post by gubemton on 2007-11-23
All this partition stuff is confusing, can someone please link/explain it better?

---

### Post by samuel.rajesh on 2007-11-23
> **gubemton said:**
> All this partition stuff is confusing, can someone please link/explain it better?


dude jus read the comments on the url ,and set up the partions again ,you can delete the unknow partions and recreate them as explained ,jus dont delete the partion where windows is


[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

---

### Post by gubemton on 2007-11-23
> **samuel.rajesh said:**
> dude jus read the comments on the url ,and set up the partions again ,you can delete the unknow partions and recreate them as explained ,jus dont delete the partion where windows is


[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

I did, but it still did not help much.

BTW, web browsers have spell checkers now.

---

### Post by overdrank on 2007-11-23
> **gubemton said:**
> I did, but it still did not help much.

BTW, web browsers have spell checkers now.

HI and please let not get started on the English again. If you read my post and bluepowder7 post you can only have four primary partition to a drive. So you will  have to delete your swap partition that you created and then take that space and create a extended partition and then within that partition you can create the partitions needed for Ubuntu installation.

---

### Post by gubemton on 2007-11-23
How would you go about creating an extended partition? If lets say I create one, then within that I can create the swap file and install Ubuntu on the rest of the free space?

---

### Post by overdrank on 2007-11-23
> **gubemton said:**
> How would you go about creating an extended partition? If lets say I create one, then within that I can create the swap file and install Ubuntu on the rest of the free space?

Correct when you select the unused space and choose create a partition there you can choose to make the extended partition. Then apply the changes then you can create the other partition for Ubuntu.

---

### Post by bluepowder7 on 2007-11-23
you'd need to remove that swap partition (delete it completely), and make sure that the space that's available is the full 1990+16253.  basically, you'd need one giant block in place of "sda4" and "unusable".  then, set up that ENTIRE block as an EXTENDED partition.  once you've done that, subdivice that extended partition into two LOGICAL partitions - make one of them 16253 and the other 1990 (or some combination that gets you approximately those numbers).  then, mark the 16253 as an ext2 partition and let ubuntu mount / there, and mark the 1990 as a linux-swap and ubuntu will handle the rest.

makes sense?

---

### Post by gubemton on 2007-11-23
I think I understand, I am going to back up my school files and try this, I hope I don't mess anything up \\:D/

---

### Post by merlinDwizzard on 2007-11-23
Just my 2 cents but,depending on what you are trying to keep. Step one: make a backup of your important stuff. Then use partition magic ( this is what I did so I'm not just theorizing)
My setup is an acer 5601 awlmi with 100gb hard drive.windows media center was allocated about 30 gb then allocated about the same for ubuntu.(so i had some extra room just in case) when i installed ubuntu, it just went (not prompting me for swap space allocation at all. It just did it). the main thing is it does not like too many partitons. Enlist the K.I.S.S. rule...(keep it simple stupid! lol).IMO partion magic is a little easier because with gpart you first have to unmount the drive.(you cannot partiton a mounted driive). you can get partition magic pretty easy with a little research, definitely the easiest way in my opinion. Good Luck!
let us know how it worked out.

---

### Post by gubemton on 2007-11-24
I tried using search and even google. But, how do you go about creating an extended partition?

---

### Post by bluepowder7 on 2007-11-24
if you're using GParted or the partition editor that's part of the Live Ubuntu CD, then it's the same as any other partition.  if you have the GUI, the bottom-right corner of the dialog box that pops up when you create a new partition should have a selection box - default is primary, but if you click it you can change to extended.

---

### Post by gubemton on 2007-11-24
Thanks to everyone that helped me. The dual-boot is working. But there is a problem:

When I select to load Ubuntu, I get some errors of unallocated something and then the screen goes black for about 2 minutes, then the Ubuntu loads. Any one can help with that?

---

