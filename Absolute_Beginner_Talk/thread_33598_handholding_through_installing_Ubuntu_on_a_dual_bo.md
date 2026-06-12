---
title: "handholding through installing Ubuntu on a dual boot system"
date: 2005-05-11
forum: Absolute Beginner Talk
---

### Post by Jace on 2005-05-11
I am looking to get away from M$ Gates.  I understand networking/ computers in a Microsoft world.
Heres where the problem lies:
I have 2 80 Gig Harddrives # 1 has Windows Xp and I have created a 10 Gig extended partition. Downloaded Ubuntu "full install, client side". 
#2 hard drive cannot be touched "data backup drive".
I have to maintain my dual boot between XP and Linux.
So I think I am ready to rock and roll. I put the disk in and reboot. Ubuntu takes off.
Dicovers hardware e.t.c. Then it gets to where it ask " where do you want to install " well in a M$ world I want it on the 2nd partition. o.k.  Ubuntu answers back saying
this is a partition that has been formatted with NTFS. Right. Right. Then it wants to know what kind of file system would you like it to be,,,,ext3. Not a problem. Then it gives me #1 and #5 which #5 is where my 10 gig partition is. Then/ also I need to create a swap file. I know what a swap file is. But do I create with in an Ubuntu install or bail on the install and let Partition Magic build it for me. Being very new to this You guys help me out. Walk me through this as technical as you can be so that I understand it and will be able to do this in my sleep. Thanks and look forward to telling Bill to get bent.

---

### Post by Zelut on 2005-05-11
If you've already created a seperate partition using partition magic I'd suggest just using that for the swap partition as well.  Partition magic is really easy & gui (which is always nice).  Using command based partition editors (ie; ubuntu install partition editor) can be confusing.  By the way, can we update that in the next version maybe?

The swap partition doesn't need to be very big.  If you're running 10G on your linux partition your swap could be 1G and you're probably ok (anyone else please pipe up if I'm wrong).

Any other questions on your installation let us know.  We're here to help.

---

### Post by az on 2005-05-11
A simple way to do it would be to use the installer to delete that ntfs partition and then tell the installer to do guided partitioning on the free space.
That will calculate the sizes, and decide the filesystems and mount points for you.  Easy.

---

### Post by Jace on 2005-05-11
No doubt this is confusing.....Never been prompted for so many file systems. A co-worker told me to use ext3 partition. O.k well what about the other options..i.e.  
no boot {yes/or no} mount point e.tc.  This is taking in the fact of how I want mine to be set up and other newbies might want to do something else like put the partition on the 2nd hard drive extended partition. Give me a break down 1,2,3,...Can I use the partition for the swap file?  List out the steps just like as if I was looking @ it.
Thanks and you guys will soon have the world. 28% of the server market by 2008.....

---

### Post by az on 2005-05-11
Well, there is no simple way to do complicated partitioning.  Deleting a partition and using guided partiotinoing on the free space is the easy way.  If you know enough about your disks and want your swap in a specific place, you are describing something an advanced user would do.

---

### Post by Jace on 2005-05-11
Thanks alot, I am looking forward to getting into this. I am @ work, so when I get home I will dive into this. Keep in mind " I want to  become an advanced user" the easy way does not teach me....#1 Boot into windows and delete the extended partition leaving it as free space. #2 reboot unit and when it prompts me for where I want to install it select " in this case"  the #5 free space. Where as Linux see's it as #5 " another question that has me going uh...  In reading over you guys statements in which I say thanks, it should just start looking like M$ . It should automaticly put the swap partition on the 10 gig partition...right?   keep in mind this is why they call us newbies......................................

---

### Post by Zelut on 2005-05-11
Use the guided partioning like azz suggested in the blank 10G space.  ubuntu will automatically assign a ext3 partition & swap using that 10G space.

So, all you'll need to do is make that 10G unpartitioned 'extra' space & the guided will set it up for you.

---

### Post by az on 2005-05-11
You can do it all at once with the ubuntu installer.

Boot.

Select the partition you want to blow away.

Tell it to delete it

You will be shown your new partition status (now with free space)

Use "guided partitionning" and you can relax after that.



Always back up anything you would not want to lose in the event you make a mistake...

---

### Post by Jace on 2005-05-11
Good deal got it to work. The only problem was the Grub and Lilo boot loaders failed ti install on me. I rebooted the unit and went through my steps and some how in the world it worked...Great job guys........................

---

