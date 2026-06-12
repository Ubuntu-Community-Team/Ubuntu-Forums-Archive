---
title: "Trying to dual boot..."
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by RobotAlligator on 2007-06-22
I have XP already installed and I'm trying to dual boot...I have a ~80 gig hardrive and when I go to install Ubuntu the SMALLEST guided partition I can make is 35 gigs..Thats about 15 more gigs than what i wanted to use, so I go to manual, and I try to make my windows XP partition smaller.  It gave me an error...So I go to the Gnome partition editor and try and resize it there.  No luck

It denied me to resize the file system under details and fill the space or something

Any ideas?

---

### Post by RobotAlligator on 2007-06-22
back to page one!

---

### Post by the.phantom on 2007-06-22
just a polite suggestion, give the post time ( at least a few hours) before a bump please

now on the guided partition i think there is a slider where you can make it smaller? not sure 

and gotta ask before the partition  did you DEFRAG windows at least once?
that can do it with data scattered all over the drive, makes it hard to partition

---

### Post by ghost_ryder35 on 2007-06-22
**_[FONT="Arial Black"][SIZE="5"]WARNING: when doing this make sure the hard drive is not mounted, it may mount itself at some point during this, right click on it and unmount it if that happens, If your drive is mounted you will get errors![/SIZE][/FONT]_**

1. go into windows and defragment your hard drive 5 times. (if you dont do this you might now be able to shrink the windows partition!)

2. Now boot into the live Ubuntu CD, Use Gnome Partiton Manager and resize the windows partition to something smaller leaving you with enough room for linux (remember you can only have 4 primary partitions so if you want more than that make one of the primary a logical and go from there)

3. now click install and choose manual partition

4. then make two partitions one whatever size you want and make it mount with " / " , and the other a 1500 meg linux swap, it will mount with swap

5. then install and enjoy

---

### Post by logos34 on 2007-06-22
so I go to manual, and I try to make my windows XP partition smaller. It > gave me an error...So I go to the Gnome partition editor and try and resize it there. No luck

It denied me to resize the file system under details and fill the space or something

like phantom says defrag it (a few times).  Personally I'd also temporarily disable hibernation file in power options, as well as virtual memory--those 'unmovable' files (green bars) all over the disk.  Then choose 'manually edit partition table' and shrink/resize windows down and add 20gb ext3 root partition (mount point '/') and 1gb swap ('/swap').  Be careful not to format the windows partition (format box UNticked).  

If that doesn't work you could try downloading the GParted live cd iso and burning it to a disc--it's a stronger version of the gparted on the ubuntu live cd.  Use that to partition then run the live cd install.

---

