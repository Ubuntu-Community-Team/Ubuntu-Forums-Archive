---
title: "Creating new partition"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by caimex on 2006-08-27
I have 250gb sata2 hdd, where dapper is installed and I want to create a new 50gb partition. I tried GParted, and everything went fine but once I select all the options I see jumbled colored lines and my monitor says signal over range. Obviously its a monitor, video, whatever problem. In GParted I tried selecting 24bit color, 16 and 32, none worked. Tried different resolutions as well.

Then I tried using QTparted, but I dont know how to create a new partition using it.

Can anyone suggest any other partitioning programs, maybe some other ones that can boot of a cd? Or maybe I missed something in GParted?

---

### Post by anaconda on 2006-08-27
sfdisk, and fdisk work well, but they are a bit more difficult to use. (both of them are non-craphical terminal -programs, which are run from command line..

---

### Post by coffeecat on 2006-08-27
When you say you used Gparted, I assume you mean the Gparted live CD. You can also use Gparted from the Ubuntu Dapper live CD, and then you don't have to worry about setting video resolutions, etc because the Ubuntu CD should do all that for you.

Boot up Ubuntu live and then go to System > Administration > Gnome Partition Editor. That is Gparted.

---

