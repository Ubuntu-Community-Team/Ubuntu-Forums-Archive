---
title: "Ubuntu/XP vFat issues"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by Emceay on 2006-08-19
I'm completely new to linux, but seeing as how I've been blissfully using my system for the past month, I don't think I'm stopping anytime soon. I'm dual booting Dapper Drake and XP from separate drives with a third drive in the vFat format.

Everything works fine on the ubuntu side, however, when the rare times arise when vmware can't do the trick and I need to dual boot to XP, the vFat is never visible.

I know this is an ubuntu forum, but perhaps someone has had this problem before since ubuntu is the main OS. Does anyone know how I can have the vFat drive 'mounted' in XP?

Currently, Ubuntu sees all three drives, while XP selfishly only sees itself. Typical, and sad.

Oh, here's the funky part: In device manager, XP knows all three disks are there, but under my computer, only gives me access to it's own drive.

Any help, much appreciated.

---

### Post by anaconda on 2006-08-19
You have to map (=give the drive a letter) your vfat drive in XP.

Go to 'control panel', (select from traditional view) 'Administrative tools' and 'computer management' and from there 'disk management'
and from there right-click the partition you want to map.. ie. assign a drive letter to.

Oh. and the traditional-view, because I looked the path from windows2000,(VMWare), and it is a bit different than XP:s 'new' look.

Hmmm. Would be much easier to just give a terminal command to do the job.. but not in windows.

---

### Post by Emceay on 2006-08-19
What's it mean when I right click, and the option is greyed out.
I'm in computer management, and it sees the disk, but I can't map it at all. Is there some condition or trick to it?

---

### Post by rowanparker on 2006-08-19
Did you use Windows or Ubuntu (Installer or not) to format/create the drive/partition?

---

### Post by Emceay on 2006-08-19
> **rowanparker said:**
> Did you use Windows or Ubuntu (Installer or not) to format/create the drive/partition?

Ubuntu of course ;) this is the first time in a month I've sat down to get XP up and running.

Should I convert it to a dynamic disk? or will that ruin linux's ability to read it?

---

### Post by Emceay on 2006-08-19
So am I ***-out or what?

---

### Post by Frank Golden on 2006-08-19
> **anaconda said:**
> You have to map (=give the drive a letter) your vfat drive in XP.

Go to 'control panel', (select from traditional view) 'Administrative tools' and 'computer management' and from there 'disk management'
and from there right-click the partition you want to map.. ie. assign a drive letter to.

Oh. and the traditional-view, because I looked the path from windows2000,(VMWare), and it is a bit different than XP:s 'new' look.

Hmmm. Would be much easier to just give a terminal command to do the job.. but not in windows.
Or click Start>run and type diskmgmt.msc

---

### Post by Frank Golden on 2006-08-19
> **Emceay said:**
> So am I ***-out or what?
It acts like it is not fat32. My dual boot when I right click
my Ubuntu ext3 partition I get the same result. Try downloading

[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

and installing this tool. When installed it places control
in your Control panel. Open the control and see if your drive/partition is there. If it is and it is ext3 or ext2
it will have a dropdown from which you can assign drive letters.
Just remember to unasign the drive before removing and/or booting XP with
drive removed. Don't want to confuse XP do we. You can access
your Ubuntu drive the same way read/write. Just don't
change any system files or folders only data you've created.

Read the info on their web site especially the FAQ.

---

