---
title: "Help installing Ubuntu."
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by Jimit87 on 2006-09-04
Ok so i burned Ubuntu CD and started installing.
**NOTE: i have 120 GB HD.**

First i installed windows XP some time ago.

[B][U]I installed win xp pro on partition of 110 GB
LEFT 10GB unpartitioned 
[/U][/B]

_NOW I WANT TO INSTALL UBUNTU ON THAT UNPARTITION._

So hers is what i did.

[IMG]http://img76.imageshack.us/img76/5642/picture001uq4.jpg[/IMG]
**so i clicked on manually option.**

**then i got onto this screen**
[U]
full view[/U]
[IMG]http://img65.imageshack.us/img65/1787/picture003sx8.jpg[/IMG]
[B][I][U][SIZE="4"]

I have no idea on how to use that unpartitioned space to install Linux.[/SIZE][/U][/I][/B]

**WHICH ONE DO I PICK FROM THIS OPTION?**
[IMG]http://img137.imageshack.us/img137/6510/picture007yq4.jpg[/IMG]
[IMG]http://img219.imageshack.us/img219/3968/picture008hg0.jpg[/IMG]

[B]
and which one should i pick from this option?[/B]
[IMG]http://img137.imageshack.us/img137/1387/picture009qx2.jpg[/IMG]

**after that which one should i pick from here?**
[IMG]http://img171.imageshack.us/img171/3452/picture004pi7.jpg[/IMG]
[IMG]http://img171.imageshack.us/img171/4370/picture005vq3.jpg[/IMG]

**and would i get 1 more hd option over here?**
[IMG]http://img219.imageshack.us/img219/9776/picture006gm3.jpg[/IMG]

please help me out here. i never installed linux on unpatitioned space before like this, i havn't installed linux at all.

Thank you.

---

### Post by orb9220 on 2006-09-04
Ok create 9gb with a mount point of / and there should be 1gb left over for linux-swap.

So right click unallocated create partition of 9gb.
"                                             "1gb.
on next page change mount point for 9gb to /
             "                      1gb to linux-swap and make sure there is a checkmark to reformat for those two only.

---

### Post by szf on 2006-09-04
If it sets any fears aside, the wizard asks how to use the 10041MB on the hard disk. From the earlier screenshot, we can see that the "free space" on the partition table was judged to be 9.81GB. 9.81 * 1024MB/GB = 10045.44MB, so it looks like it's acknowledged the desired area to install Ubuntu Linux...
And orb9220 is correct about the swap area - you'll get scary messages from the installer if you don't elect one at that time (although you can successfully install without one).

---

### Post by Jimit87 on 2006-09-05
> **orb9220 said:**
> Ok create 9gb with a mount point of / and there should be 1gb left over for linux-swap.

So right click unallocated create partition of 9gb.
"                                             "1gb.
on next page change mount point for 9gb to /
             "                      1gb to linux-swap and make sure there is a check mark to reformat for those two only.

ok so let me get this straight.
[B]
first i right click on unallocated.[/B]
[IMG]http://img65.imageshack.us/img65/1787/picture003sx8.jpg[/IMG]

Then i click on "New" to create new partition.

[IMG]http://img137.imageshack.us/img137/6510/picture007yq4.jpg[/IMG]

I put the following.
FREE SPACE FOLLOWING (MB) = 9000

THEN WHAT DO I PICK FROM HERE THOUGH?
[IMG]http://img219.imageshack.us/img219/3968/picture008hg0.jpg[/IMG]

do i click on **_primary partition or extended partition?_**

Then, from, 
[IMG]http://img137.imageshack.us/img137/1387/picture009qx2.jpg[/IMG]

Which file type should i choose for 9GB?

Ok then part II, 
Do i right click on unallocated again and click on new?
I put the following.
FREE SPACE FOLLOWING (MB) = 1000?
Then, do i click on **_primary partition or extended partition?_**

and for file type, am i choosing Linux-Swap for for this 1GB partition?

Ok so now i have 9GB and 1GB partition.
Now, check everything i said until now and tell me if i am suppose to change something.

Ok if everything is correct, on next page, what should i do?

---

### Post by Jimit87 on 2006-09-05
anyone?

---

### Post by aktiwers on 2006-09-05
> **Jimit87 said:**
> anyone?

You do 9gb for your / partition. It should be primary and I recoment ext2.

Then click ok.

Ok now you have 1gb unused space. Again go to the menu where you pick the partition. Just pick Linux-swap and ok.

Then you will be fine. Just remember later it will ask which ones to format. Make sure your Windows NTFS partition dont have a cross in that box. 

Format the 2 others and go!

---

### Post by gkiller on 2006-09-05
Go to unallocated space and "new", then enter 9000 in "New Size". Leave "Free Space Proceeding" and "Following" at 0. This is, if you want to have some unallocated space left between your Windows and the new Linux partition.

The 9 GB is going to be your main partition. The main partition should be created as "Primary Partition". One hard disk can have up to 4 primary partitions or extended partitions, and "lots" of logical partition inside a extended partition. But you won't need that now.

The default filesystem type for Linux is "ext3" so you should use this.

Then click "Add".

Then go again to unallocated space and create a 1000 MB partition (enter 1000 in New Size). This is the swap partitin where parts of the system memory gets swapped if there is not enough room in RAM. Again create Primary Partition and filetype is now "linux-swap".

You have now 2 new partitions, /dev/hda2 and /dev/hda3.
For /dev/hda2, set the mount point to "/", since that is the root directory where all data will be put. For the swap partition you don't need a mount point and won't be asked.

I hope I could clarify the situation a bit ;)

---

### Post by Jimit87 on 2006-09-05
omg. thanks. i installed Ubuntu finally.
now i want to install nVidia 3D driver on it.
anyone can tell me how?
i dled the 3d driver and burned on dvd and then installed linux and pasted it to /home/username folder. how do i install it now?

Thank you.

---

### Post by szf on 2006-09-05
Look a this [thread]("http://ubuntuforums.org/showthread.php?t=251020&highlight=easyubuntu")  on EasyUbuntu.

To clarify, EasyUbuntu will make installing nVidia (and ATI) drivers as easy as clicking a checkbox.

---

### Post by gkiller on 2006-09-05
> **Jimit87 said:**
> omg. thanks. i installed Ubuntu finally.
now i want to install nVidia 3D driver on it.
anyone can tell me how?
i dled the 3d driver and burned on dvd and then installed linux and pasted it to /home/username folder. how do i install it now?

Thank you.
Unfortunately I don't know that. I suggest you follow this Howto:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
This Howto only works if you have access to the Internet. If not, you might want to start a new thread so people can specifically help with that problem.

Or if you want the latest binary drivers, there is a Howto on the forum, but it might be more for experienced users:
[http://ubuntuforums.org/showthread.php?t=139264](http://ubuntuforums.org/showthread.php?t=139264)

---

