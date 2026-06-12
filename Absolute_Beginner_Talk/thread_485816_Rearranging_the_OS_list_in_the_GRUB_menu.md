---
title: "Rearranging the OS list in the GRUB menu?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by pwcasellini on 2007-06-27
Hi, I've recently dual booted with XP on my Thinkpad T60, and as much as I like Ubuntu, 75% of the time I still have to start up into XP.  My GRUB setup by default gives me a prompt to choose between 7.04-16, 7.04-15, the recovery modes for each of those, and memtest86+ for Ubuntu, and Windows XP Professional way down at the bottom.

I've tried editing the "default" number option at the top of the file to '7', but that didn't change anything -- 7.04-16 was still the selected option in the menu, and when left alone, would be OS to enter.

I was wondering if there would be anything wrong with simply sudoing into the menu.lst file again and dragging Windows XP to the top of the list.  Is there anything else in the menu file that relies on the Ubuntu options starting off the list?

Thanks!

---

### Post by master_kernel on 2007-06-27
> **pwcasellini said:**
> Hi, I've recently dual booted with XP on my Thinkpad T60, and as much as I like Ubuntu, 75% of the time I still have to start up into XP.  My GRUB setup by default gives me a prompt to choose between 7.04-16, 7.04-15, the recovery modes for each of those, and memtest86+ for Ubuntu, and Windows XP Professional way down at the bottom.

I've tried editing the "default" number option at the top of the file to '7', but that didn't change anything -- 7.04-16 was still the selected option in the menu, and when left alone, would be OS to enter.

I was wondering if there would be anything wrong with simply sudoing into the menu.lst file again and dragging Windows XP to the top of the list.  Is there anything else in the menu file that relies on the Ubuntu options starting off the list?

Thanks!
You can edit /boot/grub/menu.lst to change the order.

However, if you are a Ubuntu newbie, I would reccomend installing [this program]("http://web.telia.com/~u88005282/sum/archive/deb/startupmanager_1.0.7-1_all.deb") to change the default.

---

### Post by master_kernel on 2007-06-27
> **master_kernel said:**
> You can edit /boot/grub/menu.lst to change the order.

However, if you are a Ubuntu newbie, I would reccomend installing [this program]("http://web.telia.com/~u88005282/sum/archive/deb/startupmanager_1.0.7-1_all.deb") to change the default.
Sorry, the program I want you to install is called SUM (Start-up manager) found here: [http://web.telia.com/~u88005282/sum/index.html](http://web.telia.com/~u88005282/sum/index.html)

I personally have installed it, and it has a number of features and is incredibly easy to use.

To install it, open a terminal, cd to the download directory and run:
```
sudo dpkg -i startupmanager_1.0.7-1_all.deb
```

---

