---
title: "xorg.conf second look"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Tommy James on 2007-04-25
Hello Everyone!

Wondering if I can get some second eyes on my xorg.conf?  

Just installed Feisty and set up my nVidia for dual monitor by using "nvidia-settings".  I use separate X servers with Xinerama enable so I can share windows between monitors and not have to deal with the "cross bar problem" of TwinView.

When nvidia-settings saves to xorg.conf it looks a bunch of sections from the original file are missing or some of the options from sections are missing.

My Current xorg.conf is attached as xorg.txt
My original xorg.conf is attached as OLDxorg.txt

Do I need the missing sections?  Everything seems to run fine now.
Pros/Cons of the missing sections?
Future Challenges I might run into with them missing?

Thx Everyone!

---

### Post by PartisanEntity on 2007-04-25
I recently used the xorg.conf output of nvidia-settings (which contained less than my original xorg.conf) without problems.

I would recommend that you back up your old xorg.conf and then use the data from nvidia-settings in your 'new' xorg.conf. Then see if anything stops working.

---

### Post by Nythain on 2007-04-25
i basically back up the original working conf with all MY edits... then save the changes in nvidia-settings, compare the two files... and manually add what nvidia-settings wanted to without jeopardizing or losing my edits

---

