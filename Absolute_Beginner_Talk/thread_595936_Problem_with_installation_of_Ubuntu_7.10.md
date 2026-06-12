---
title: "Problem with installation of Ubuntu 7.10"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by Bheegerji on 2007-10-29
I'm new to linux and found that Ubuntu distributions are easy to be installed.So, I downloaded a ubuntu 7.10 iso and burnt it. I checked the cd for defects and there were no problems with the burnt cd. I'm using Win XP Pro. I'm planning a dual boot installation. I've a 80GB hard disk partitioned into 4 drives( c: 19GB, d: 19GB, e: 19GB and f: 15GB). Win XP has been installed into c: drive and I like to install Ubuntu in f: drive. So, I emptied all the contents of f: drive and made available all the 15GB for Ubuntu.

I read many posts and started my installation. I inserted the cd and rebooted my system and started my installation. Here are the problems 

1) I use a 15" monitor and the "forward" and "back" buttons at the bottom of the install window were not visible. I tried to resize the window and still found no success. The window wont resize. So I realigned the top and bottom task bars to left and right and checked the autohide option. This time I could see half of the button. Will this problem persist even after the installation?

2) I proceeded with the installation and went ahead to "Manually edit partition table". The window showed it had 17092MB and others had around 20000MB. There was a free space of around 8000MB. I selected f: drive as it was the only drive with least space. I entered a value 13000MB in the box and selected fat32 formatting and clicked ok. A new box appeared showing that it was scanning the drive and later another window appeared that showed "Writing the changes to disk. You cannot undo the changes later." I clicked ok and waited for sometime. Then an error box appeared stating " Error: Root file not defined." I din know what to do and rebooted the system and removed the cd.

3) Windows started and I checked my f: drive. It was formatted as fat32 and it showed only 11GB (initially 15GB) as available free space. How can I undo this? Will I be able to restore the f: drive to its initial condition?

Please help me with the installation.

---

### Post by bumanie on 2007-10-29
I am no expert on this, but I have a dual boot system myself. 
_Answer to Q1:_ this won't persist once installed and the restricted driver for your video card is installed.
_Answer to Q2:_ Have difficulty with this part myself, although I managed do it, I can't clearly explain how to do it. Sorry!
_Answer to Q3:_ For an ubuntu install you should really be using an ext 3 file system rather than a fat 32 (although fat 32 will work). You could download a g-parted live cd, which is a partition manager and works well - [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828). It is the same as on the ubuntu live cd, but this has the option of GUI with slide bars etc and can format most file system types.
I pre partitioned the hard drive with the stand alone live cd g-parted prior to installing a dual boot system. I found the g-parted live cd easier to manage and it will change your f:/ to the size you want.
Hope this helps a bit.

---

### Post by Bheegerji on 2007-10-29
Thanks bumanie. I've read in a lot of forums that Ubuntu can safely write data in fat32 formatting. That's why I formatted in fat32. And thanks again for that GParted live cd thing.

---

### Post by ske1fr on 2007-10-29
> **Bheegerji said:**
> 1) I use a 15" monitor and the "forward" and "back" buttons at the bottom of the install window were not visible. I tried to resize the window and still found no success. The window wont resize. So I realigned the top and bottom task bars to left and right and checked the autohide option. This time I could see half of the button. Will this problem persist even after the installation?

If your 15" monitor can only display 800 by 600 pixels (also known as XGA) then you may find that this "hidden button" problem will persist.

---

