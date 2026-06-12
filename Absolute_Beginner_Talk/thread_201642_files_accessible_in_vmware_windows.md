---
title: "files accessible in vmware windows"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by sbguy on 2006-06-22
I took a backup of windows media files before deleting windows and installing Kubuntu. Now they're in my home folder. How do I see 'em and play 'em in vmware windows xp? Can anyone help?

---

### Post by x64Jimbo on 2006-06-22
You should create a samba share on the network and map that share as a network drive in your virtual machine. For more info, visit the wiki:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by keith whitehouse on 2006-06-22
hi sbguy,

I had a similar problem with vmware in as much as I had (have) a very large relational database in windowsxp pro. Because of the fragile nature of Windows I made it a practice to have the program files and the data generated from the program in seperate places. In vmware I could install my database from the original 3 floppies, but I could not find a way to get the data files into vmware. I overcome the problem by burning the data files to a cd and then from within vmware you can access the cd drive and drag the files into windows as you usually do

best regards keith

---

