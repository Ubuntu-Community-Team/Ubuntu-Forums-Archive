---
title: "odd(?) mounting question"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by manicmailman on 2008-03-31
k this is my setup (for dual boot xp and ubuntu)
i have a 500g and a 250g hd
the 250 is running xp
i partitioned the 500: 150g for ubuntu and 350g for "Media"... obviously i have my media (mp3s movies etc..) on the 350 partition...

my plan is to have both xp and ubuntu be able to access "media"... can i mount the 350 partition in the ubuntu file tree and still be able to access it in xp?

or rather... whats the best way to do it? any suggestions.. im askin first so that i dont mess something up... im very afraid of that..

---

### Post by Duck2006 on 2008-03-31
This will help with mounting the media drive.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by scragar on 2008-03-31
you have a few choices(listed in my prefared method):

1: teach windows to use the ext2 format, and then format it in ext2. == ext2 has a better structure and permitions than others.

2: teach ubuntu to use ntfs, format in ntfs == ntfs avoids some of the bugs of fat

3: use fat as the partition type(called vfat for the most part on linux). == buggy, but everything can use it without problems

---

### Post by Duck2006 on 2008-03-31
For linux to write to NTFS you need to install ntfs-3g drivers with you can find in your synaptic package manager.

---

### Post by manicmailman on 2008-03-31
k new problem... my media drive is NTFS... after reading the comments i figured it was ok to get the NTFS drivers (which were already installed) and mount the drive...

when i double-clicked the drive... it mounted it onto my desktop... i figured i would put it into my home folder... i then figured this could be done in the option called 'mount point'... so i typed in /home/[user].... and proceeded to unmount then mount the drive for the settings to take effect... not so... i shoulda just dragged the damn thing... because now it wont open... giving me this message: "mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)"

unfortunately the button "do what you did before then" doesnt exist....

damnit... any suggestions? (besides the obvious "turn and walk away from linux")... but i dont want to do that... so your stuck with my dumbass problems...

---

### Post by superprash2003 on 2008-03-31
first unmount then type sudo mount /dev/hdb /home/[user]/folder 

where /dev/hdb is your ntfs drive

---

