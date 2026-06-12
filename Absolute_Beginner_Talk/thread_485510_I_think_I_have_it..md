---
title: "I think I have it."
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by henthorn on 2007-06-27
I first installed XP in a 10gb partition and then installed Ubuntu on the balance of the disk.  I need to enlarge the Xp partition and used gparted to divide the Unbuntu partition in half.  Now it shows the 10 gb Xp partition,then the 70 gb Ubuntu partition, then the 70+gb unknown partition and then the swap partition.  Can I now just go to XP disk management and make the unknown partition  another nfts partition and  be home free?  I know nothing about this stuff.

---

### Post by freebird54 on 2007-06-27
That is one option.  Another might be to MOVE the Ubuntu partition to the end, and resize the XP partition as desired.  Other options include:

Formatting the new partition as ext3, installing a [driver](http://www.fs-driver.org/) to read/write ext3 from Windows, and having a dual accessible partition that way.

Formatting the new partition as VFAT32, and accessing from both OS's that way.

Or your original thought, and installing NTFS-3g in Ubuntu to access from both sides.

Hopefully this isn't confusing!  Just thought you might like to know your choices.... :)

---

### Post by ugm6hr on 2007-06-27
> **henthorn said:**
> I first installed XP in a 10gb partition and then installed Ubuntu on the balance of the disk.  I need to enlarge the Xp partition and used gparted to divide the Unbuntu partition in half.  Now it shows the 10 gb Xp partition,then the 70 gb Ubuntu partition, then the 70+gb unknown partition and then the swap partition.  Can I now just go to XP disk management and make the unknown partition  another nfts partition and  be home free?  I know nothing about this stuff.

I take it you got GParted to work then?
[http://ubuntuforums.org/showthread.php?t=484199](http://ubuntuforums.org/showthread.php?t=484199)

---

### Post by henthorn on 2007-06-27
ugm6hr:    No, I never gor Uparted to work.  I downloaded from different mirrors, I tried different versions.  That is partly wrong.  I did get version 2.5.2 to work and used that to make two partitions of the Ubuntu partition.  But 2.5.2 doesn't have the ntfs functions so it didn't help much. I don't know what the problem is and apparently neither does any one else. It seems that the computer problems I have are always unsolvable.(G) Probably due to my own ignorance.

Freebird54: Thanks for taking the time to post all my options.  I do appreciate that. I will study them and see if I can understand any of them.  I still don't understand a lot about Windows and I've been USING computers since the old Commodore 64.  I would move the partitions as you suggest in #1, but without gparted have no idea how to get that done.

The second option would require a step by step instruction manual since I don't know the terminology.

Ditto: the third option.

The fourth option is probably the one since I have already installed the ntfs-eg thing in Ubuntu but haven't a clue as to how it works.  It is terrible to be ignorant.  I am trying to remedy that but at 87 it seems I forget as fast as learn. Again thanks for your trouble.

---

### Post by aeiah on 2007-06-27
if you're planning on moving your ubuntu partition to the end of the disk and resizing your windows one, make sure stuff is backed up. moving the partitions like that can result in ubuntu not being able to find its home partition (if one exists) and other bits and pieces. backup and it doesnt really matter if this happens. you may be safer if you havent got a seperate home partition

---

### Post by freebird54 on 2007-06-27
If you have the Live CD you should have GPartEd - a version that will work well enough.  You will find it under System->Administration->Gnome Partition Editor.  When you access it that way, none of your hard drives have been mounted, so you can make changes as needed.

Remember - make your changes in ORDER.  Plan it out on paper (one piece of hi-tech that still works well!), and enter the changes to be made 1 at a time.  It takes longer that way, but you know what youhave then.

If you let us know what you end up deciding to do, I am sure someone (me if I'm back on here fast enough!) will be happy to make up a step-by-step guide for you.

Oh - and don't worry about the 87 thing... my Dad at 87 still uses MS Word 5.0 - the DOS VERSION! - now along with Word 2000.. so I am used to showing things step-by-step!

---

### Post by henthorn on 2007-06-27
Thanks,freebird54.  I found the gparted forum and was advised to choose the Force VESA Driver option.  That worked and I was able to get gparted to work finally.  However your advice to use the live disk so as not to mount the drives (although I really don't understand that) sounds like a good way to handle it.  I have the partitions shiifted  but I forgot to include the file type when I  created the new partition. I guess that is no biggie, I'll just go back and make that change. Just getting the darn gparted disk working must have taken a week.

BTW, Which of the methods you gave would be best? I had planned to go with ntfs but am open to suggestions if one is better than the others/

---

