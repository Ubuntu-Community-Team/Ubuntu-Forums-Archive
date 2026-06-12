---
title: "Ubuntu won't load on startup"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by s2h131985 on 2007-03-28
Ubuntu has been working fine on my laptop for a month now. I have it set up so that when the computer starts, I have the option of starting Ubuntu or Windows. Last night I was helping my sister over the phone do a full system recovery on the computer at home. I went into the program on my computer to tell her the steps. I must have went to far, because it asked me to restart now or later. When I restarted the computer today, windows automatically loaded, not giving me an option for Ubuntu. I've already tried a system restore point in Windows to a week ago, and it doesn't work. I also looked to see if my C drive in windows was still 40 GB like when I had Ubuntu running, and it is. Based on this, I think that he partition is still working, but I have no idea how to load it. Any help would be great. Thanks.

---

### Post by compmodder26 on 2007-03-28
Sounds like, your restore from windows overwrote the MBR.  You should just need to reinstall GRUB.  A quick search on google turned up this thread from the Ubuntu archives.  Follow the post by remmelt: [http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by s2h131985 on 2007-03-28
I tried to do the second thing on the link you posted and it couldn't find the drive. I know the drive that I had linux on was /dev/hda5. Does anyone know how that translates for GRUB. Thanks.

---

### Post by al7kz on 2007-03-28
deleted

---

### Post by Doug11 on 2007-03-29
Here's another if that didn't work

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

the only thing,,in step 6 type >>> setup (hd0)  <<<instead of using the comma and the number if you want the grub to display the boot menu,,I wracked my brains trying to figure out why I couldn't get a boot menu and then tried it without the comma and number and worked like a charm.

---

