---
title: "remove kernels thru Synaptic .. please assist"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by molly_001 on 2006-07-12
The information I need to show you for this question would be too messy to display in this forum post, so I have put it all onto a web page [_here_]("http://tinyurl.com/os9sw")

On that web page, you will find snapshots of the following from my machine:
1) GRUB menu.lst for now
2) Base System (in Synaptic)
3) Base Restricted
4) Base Universe


Here is my question:
My GRUB boot menu currently has three full kernels as options to boot into. (see web page).  I need to use Synaptic to uninstall the two older ones.  It's my understanding that doing this through Synaptic will also remove the undesireable entries in GRUB.

I look forward to ridding myself of these extra kernals, freeing the associated drive space, and trimming GRUB, but...

**Being new to Ubuntu, I just don't know _WHICH_ items to uninstall.**  If anyone can look at the [web page]("http://tinyurl.com/os9sw") and tell me which items to remove <via Synaptic> from (2) Base System (3) Base Restricted and (4) Base Universe, I'd be very grateful.

After I have this info, I can use the web page already created to make a small tutorial for extraneous kernal removal/extraneous GRUB menu boot options.  THANK YOU!!!

---

### Post by LKRaider on 2006-07-12
You only need to keep the latest one. You can check which is the latest by the numbering.

Right now, you have these:
[LIST]
[*]2.6.15-26
[*]2.6.15-25
[*]2.6.15-23
[/LIST]

So you just need to keep 2.6.15-26.

To remove the others, do a search by name in Synaptic for their versions. Search **2.6.15-23** and mark to _Completely Remove_ the installed ones, then search for **2.6.15-25** and again mark to _Completely Remove_ them; then press **Apply** to uninstall them.

---

### Post by Kilz on 2006-07-12
> **molly_001 said:**
> The information I need to show you for this question would be too messy to display in this forum post, so I have put it all onto a web page [_here_]("http://tinyurl.com/os9sw")

On that web page, you will find snapshots of the following from my machine:
1) GRUB menu.lst for now
2) Base System (in Synaptic)
3) Base Restricted
4) Base Universe


Here is my question:
My GRUB boot menu currently has three full kernels as options to boot into. (see web page).  I need to use Synaptic to uninstall the two older ones.  It's my understanding that doing this through Synaptic will also remove the undesireable entries in GRUB.

I look forward to ridding myself of these extra kernals, freeing the associated drive space, and trimming GRUB, but...

**Being new to Ubuntu, I just don't know _WHICH_ items to uninstall.**  If anyone can look at the [web page]("http://tinyurl.com/os9sw") and tell me which items to remove <via Synaptic> from (2) Base System (3) Base Restricted and (4) Base Universe, I'd be very grateful.

After I have this info, I can use the web page already created to make a small tutorial for extraneous kernal removal/extraneous GRUB menu boot options.  THANK YOU!!!
From what I uderstand its only the Base system ones that need to be removed. Leave the Linux-image-2.6.15-26-386 and remove the ones with a lower number. You will not have to edit the grub menu, I believe the entries will be removed when you remove the older kernels automaticly.

---

### Post by Susan.Desanco on 2006-07-12
pls disregard!!

---

### Post by molly_001 on 2006-07-12
> **LKRaider said:**
> Right now, you have these:[LIST]
[*]2.6.15-26
[*]2.6.15-25
[*]2.6.15-23[/LIST]So you just need to keep 2.6.15-26.

To LKRaider --
You've almost got me there, but I probably didn't make my question entirely clear. I could see the version numbers and could tell that 26 was the one I need to end up keeping. But, what I need to know is which items to mark ... there are a bunch of them. For instance ... which line item(s) should I mark for Completely Remove in the (2) Base ... and which line item(s) should I mark in the (3) Base Restricted ... and which line item(s) should I mark in the (4) Base Universe.

I guess what I am looking for is a specific line item(s) because there are so many to remove, and in various panes.  

Thank you!!

---

### Post by Alpha_Cluster on 2006-07-12
Just find the kernel images for those numbers that were stated to remove.  It will remove the extras as well.

---

### Post by Average_Joe on 2006-07-12
molly,

To answer your specific question about line items...
As above, remove the old kernel linux image -- it will be the line appended with the letter "-386".  As opposed to appends of "-k7" or "-server".

And as Kilz and Alpha mentioned, you need to remove this one line in the Base System area, and it will then remove some items from Restrict as well.

---

### Post by LKRaider on 2006-07-12
> **molly_001 said:**
> To LKRaider --
You've almost got me there, but I probably didn't make my question entirely clear. I could see the version numbers and could tell that 26 was the one I need to end up keeping. But, what I need to know is which items to mark ... there are a bunch of them. For instance ... which line item(s) should I mark for Completely Remove in the (2) Base ... and which line item(s) should I mark in the (3) Base Restricted ... and which line item(s) should I mark in the (4) Base Universe.

I guess what I am looking for is a specific line item(s) because there are so many to remove, and in various panes.  

Thank you!!
No need to go by categories.

Do a name search for those version numbers in Synaptic and you will find all the packages relating to that version.

Then just right-click the green ones and select Completely Remove.

---

