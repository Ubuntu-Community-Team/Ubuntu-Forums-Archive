---
title: "How to tv-out"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by vussvillem on 2008-01-24
After hours of searching and frustration. I only ask for everyday simple things that are sure as hell simple in Windows.

1) Is there a simple how-to for watching video or pictures on TV screen?!

The only things I found were for Kubuntu - [http://www.uluga.ubuntuforums.org/showthread.php?t=641998](http://www.uluga.ubuntuforums.org/showthread.php?t=641998)
and this 
[http://radagast.bglug.ca/laptop/ubuntu_on_latitude_c600.html](http://radagast.bglug.ca/laptop/ubuntu_on_latitude_c600.html)
and some other pages

2)Why is there need for 5-100 steps of changing setting files, making/installing new scripts, need   to be connected to TV before running codes or other complicated voodoo?

3) Why most of the posts don't say what to do after changing xorg.conf and ten other files and settings, how can I taste the fruits of my hours of configurating?

4) Is there little GUI that enables to click - use TV screen, click - use TV and laptop screen, click - use laptop screen only? In windows, there is, for a REASON.

PS I have a dell D600 with ATI radeon 9000

---

### Post by DrMega on 2008-01-24
> **vussvillem said:**
> After hours of searching and frustration. I only ask for everyday simple things that are sure as hell simple in Windows.

1) Is there a simple how-to for watching video or pictures on TV screen?!

The only things I found were for Kubuntu - [http://www.uluga.ubuntuforums.org/showthread.php?t=641998](http://www.uluga.ubuntuforums.org/showthread.php?t=641998)
and this 
[http://radagast.bglug.ca/laptop/ubuntu_on_latitude_c600.html](http://radagast.bglug.ca/laptop/ubuntu_on_latitude_c600.html)
and some other pages

2)Why is there need for 5-100 steps of changing setting files, making/installing new scripts, need   to be connected to TV before running codes or other complicated voodoo?

3) Why most of the posts don't say what to do after changing xorg.conf and ten other files and settings, how can I taste the fruits of my hours of configurating?

4) Is there little GUI that enables to click - use TV screen, click - use TV and laptop screen, click - use laptop screen only? In windows, there is, for a REASON.

PS I have a dell D600 with ATI radeon 9000


Install the proprietary drivers from the Restricted Drivers Manager, run ati-config, and away you go.

---

### Post by vussvillem on 2008-01-24
Thanks for answer. Sorry, I'm very new to Ubuntu.

I opened up Restricted drivers manager. It shows two drivers that I have enabled already, namely Atheros Hardware Access Layer (HAL) and Software modem driver. And thats it. So what next? What drivers do I need?

How one does run ati-config?

---

### Post by kvizz on 2008-01-24
[http://wiki.cchtml.com/index.php/Tvout](http://wiki.cchtml.com/index.php/Tvout)
worked nice for feisty and gutsy on radeon 9000 and 9200

---

### Post by vussvillem on 2008-01-24
Kvizz, your refernced link's content looks really promising! I haven't got my installation CD right now with me, so I'll try it out later. Thank you very much! Really great community!

Mean time I found out about ati config as well:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Configure_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Configure_the_Driver)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-123c48c83c49553bdd4260ff972ffacdff04580e](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-123c48c83c49553bdd4260ff972ffacdff04580e)

Last refernce says that Ati Radeon below 9500 is not supported by 'fglrx' driver.

Thanks again to Kvizz!

---

