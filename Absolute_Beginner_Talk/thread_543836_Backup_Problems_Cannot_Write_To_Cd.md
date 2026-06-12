---
title: "Backup Problems Cannot Write To Cd"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by larry Gaminde on 2007-09-05
How do you back up Ubuntu files. I have tried to drag etc. and home directorys using CD/DVD Creator. I just cannot write anything, I keep getting Error " I/O error" while linking I have tried two different CD writers with no luck when the cd write screen comes up its all greyed out. Is there something I need to do to make the cd usable or is it that I can't copy etc because its root. Is there another way to do this? Im not even sure what to backup. I have postfix, apache2 and ftp servers running on this unit and will install print server someday.

---

### Post by bone2006 on 2007-09-07
here's instructions on moving home to another partition if that's what your trying to do and you didn't do it during installation.  I took this from somewhere else to help you out

How to move /home to another partition

 

Having the /home directory on it’s own partition has several advantages, the biggest perhaps being that you can reinstall the OS without losing all your data. You can do this by keeping the /home partition unchanged and reinstalling the OS which goes in the “/” (root) directory, which can be on a seperate partition.

 

If you have already installed your OS and did not create a seperate /home directory, go to gparted.sourceforge.net and download the liveCD ISO. Reboot your computer with the livecd and create another parition for your /home directory. Gparted will allow you to reize your existing partition and allow you to create a new partition without destroying your data. Create a partition of sufficient size for your “/home” directory.

 

 

Next, mount the new partition:

 

$mkdir /mnt/newhome
$sudo mount -t ext3 /dev/hda5 /mnt/newhome

 

(You have to change the “hda5&#8243; in the above to the correct partition label for the new partition.

Also, the above assumes that the new partition you created is formatted as an ext3 partition.

Change the “ext3&#8243; to whatever filesystem the drive is formatted to.) Now, Copy files over:

Since the “/home” directory will have hardlinks, softlinks, files and nested directories, a regular copy (cp) may not do the job completely.

 


$cd /home/
find . -depth -print0 | sudo cpio --null --sparse -pvd /mnt/newhome

 

 

Now we want to unmount the new partition and move it for the new home

 


$sudo umount /mnt/newhome
$sudo mv /home /old_home

 

 

Now we want to make the home directory since it's no longer there and mount it:

 

$sudo mkdir /home
$sudo mount /dev/hda5 /home

 

 (Again, you have to change “hda5&#8243; to whatever the new partition’s label is.)

Cursorily verify that everything works right.

Now, you have to tell Linux to mount your new home when you boot.

Add a line to the “/etc/fstab” file that looks like the following:

 

/dev/hda5 /home ext3 nodev,nosuid 0 2

 

(Here, change the partition label “hda5&#8243; to the label of the new partition, and you may have to change “ext3&#8243; to whatever filesystem you chose for your new “home”) Once all this is done, and everything works fine, you can delete the “/old_home” directory by using:

 

$sudo rm -r /old_home

---

