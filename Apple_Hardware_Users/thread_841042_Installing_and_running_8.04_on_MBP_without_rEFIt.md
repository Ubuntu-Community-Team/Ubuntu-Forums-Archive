---
title: "Installing and running 8.04 on MBP without rEFIt?"
date: 2008-06-26
forum: Apple Hardware Users
---

### Post by Pipen84 on 2008-06-26
Hi. 

Please help me with this, because right now i have 30 Gb I can't use.

I made a boot camp partition on 32 gb and tried everything exactly what it says on [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) about installing without rEFIt. But it doesn't work, every time i restart my computer i have to hold the "option" key and choose Macintos HD otherwise it says something about invalid boot drive. 

The reason i want to do it without refit is becase i dont like the ui of rEFIt. What can i do o solve this? i tried so many times, with and without a swap partition and alays doing that last setting in the advanced option about "On the last screen, click on the "Advanced" button and select instead /dev/sda in the drop-down list for installing GRUB", on the MacBook PRO page it doesnt say anything about installing without rEFIt, but i thought it would be the same. Please help

Best regards

---

### Post by luke.is.very.handsome on 2008-06-26
Not to be a jerk, but did you notice that your link says macbook on the end of it and not macbookpro.  the macbook pro link that they provide on the link you supplied there does have two ways of doing it, one with rEFIt and one without.  it also states that it was done with leopard on the machine and not tiger.  maybe thats what is wrong (the wrong guide)?

---

### Post by Pipen84 on 2008-06-26
As I said!

> **Pipen84 said:**
> ...on the MacBook PRO page it doesnt say anything about installing without rEFIt, but i thought it would be the same.

---

### Post by flaggh on 2008-06-26
Just to clarify, at the last step, you clicked advanced and then selected the partition to which you installed ubuntu, correct?  You say /dev/sda, but I would assume it would be /dev/sda3.

Could you clarify why you do not want to install refit.  You can disable it at bootup time if you do not like the ui.  You can also change the icons and I think maybe the background, but its appearance has never bothered me enough to not want to use it.  It has a handy tool for syncing your partitions which may explain some of the trouble you're having.

---

### Post by eddielgarcia on 2008-06-26
I have done numerous install of Ubuntu on Macs and when I have run into this problem of the Mac not seeing the Ubuntu install ( when you hold the alt key at boot-up ) I would always install refit and it took care of the partition tables.  There should be no security concerns if  there are any and nothing keeps you from un-installing it after you get the partition tables correct. When refit boots up for the first time sometimes I have noticed it may take two or three boots for it to be recognized (while holding the alt key at boot up).  When you get it to boot with refit just run the partition tool and ensure that it matches what you opted for during your install of Ubuntu.  After that you can restart go into you OS X and delete the efi folder that is created in your root directory of the Mac HD.  After that you can pretty much say refit exists no more and you should see at boot up (while holding the alt key) a windows partition which really means your Ubuntu partition.  If you select that it will take you in and successfully launch GRUB.

---

### Post by cyberdork33 on 2008-06-28
there is a bug. install rEFit, then you can uninstall it after using it's tools:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

