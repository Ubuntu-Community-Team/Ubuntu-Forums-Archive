---
title: "easy partition question"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by benner on 2007-07-11
just about to install a dual boot and i have a simple question regarding the automatic partition manager.  If I want to create a partition in 20% of the hard disk for ubuntu, where it says 'guided partition, partition #5 and use the freed space' do i drag the 'new partition size' slider to 20% or to 80%?

---

### Post by FleetAdmiral74 on 2007-07-11
I would think 20%, but you can always double check visually, looking at the relative size.

---

### Post by Papi-KB7VGW on 2007-07-11
Hi  Before you install Ubuntu, I would very strongly recommend that you defrag windows at least 5 times.  I always close the derag gui and then reopen it because it seems to do a better job of defraging that way.     :)

---

### Post by Espreon on 2007-07-11
I recommend creating a separate partion for Ubuntu, 1st download the GParted LiveCd"
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Burn it to a blank CD (with a real iso burner, not the one XP comes with)

Next Pop it in, boot it, and double click GParted.

Next resize the Windows Partion to give it 20% less space.

Now use the free space and create an ext3 partion give 1 GB to make a linux swap partion.

After partioning, eject the GParted CD and put the Ubuntu CD in, then when you get to the partioning part, select manual, then for the ext3 partion click the check box for format then select edit partion on the ext3 partion and make the mount point / rather than /media/whatever

then go on with installation.

I don't know why the He double hockey sticks they removed GParted from the Feisty LiveCD.

---

### Post by benner on 2007-07-11
thanks everybody.

---

