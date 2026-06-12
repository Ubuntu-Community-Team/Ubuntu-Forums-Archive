---
title: "Ubuntu freezes when selecting partition"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Churchill on 2007-03-27
Hello Ubuntu community,

I heard these forums were excellent for beginner help so i figured i would tell you all what my problem is.

I downloaded Ubuntu for the amd 64bit processors at ubuntu's website. i insert the boot disk and select install ubuntu from that first black menu. It eventually brings me to the desktop where it has a big "install" icon at the top left of the screen. I double click it and proceed to select my languages and username. I then get a pop up window that says "starting partitioner" and it loads. I am then at step 5 of 6 and i select the smaller of my two hard drives 

"/dev/hda: master (hda) - 60.0 GB ST360020A"\

I have three other options on this screen. One is my larger hard drive that has windows partitioned on it and the other two say " use the largest continuous free space" and "manually edit partition table"

With my smaller Hard drive selected i click forward it thinks for a second and then i click forward again to "Resize IDE1 master, partition #1 (hda1) and us freed space" and my new partition size is 50%

It thinks for a second and then shows me the exact same page with nothing changed. I click forward again to resize at 50% and it just sits there and thinks for like 20 minutes and doesnt do anything. What do i do from here?

Thanks for the help guys and gals sorry for such a long newbie post.

---

### Post by chewearn on 2007-03-27
Based on what you did, I assumed you wanted to install ubuntu on the 60GB harddisk.  Further, you already back-up all you data from this harddisk and would not mind erasing the whole disk.

Then, I suggest that you select "manually edit partition", and delete everything in this harddisk.  (Be careful not to accidentally delete the wrong disk !)  After deleting the disks, it should be empty and unallocated space.

Once you return from manual partition edit, select to install ubuntu on the largest continuous free space.

---

### Post by Churchill on 2007-03-27
Thanks, i still have some files on that 60 gig HD, i'm going to back them up and clear it out when i get home from class and work today.

---

