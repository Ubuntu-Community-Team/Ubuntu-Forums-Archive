---
title: "2 Tux icons on rEFIt screen"
date: 2012-12-04
forum: Apple Hardware Users
---

### Post by sumethc on 2012-12-04
I have been using Mac for over 30 years but just started to play around with Kubuntu a couple of weeks ago. I have installed Precise [64-bit] on my MacBook 3,1 without any problem and found that it uses a lot less resource than my Leopard system. 

The problem is I installed Linux Mint on my Kubuntu partition permitting the installer to replace Kubuntu with Linux Mint. After a couple of days of trying out I decided Kubuntu was more to my liking, so I reverted back to Kubuntu. This was when I made the mistake, I believe I used the Installer's partition manager to just format the partition before installing Kubuntu on it.

Now I know what I should have done but I don't want to start it all over again. Kubuntu Precise is working fine. The only fly in the oinment is that when I boot up my Mac and rEFIt kicks in, there appears one Apple logo and TWO Tuxes, the middle one of which will lead me nowhere. Is there some traces of the old installation left somewhere that I can remove and get everything back to normal? Any advice would be truly appreciated.

---

### Post by trogdor1138 on 2012-12-05
I'm not entirely sure of how rEFIt looks for bootable partitions and operating systems. The problem is that the project was abandoned some time ago, as the last update was in 2010.

If you insist on using a boot manager replacement, I would highly recommend updating to the rEFInd fork of the code. Rod Smith has made quite a few improvements and it works much better (the last update was just a month ago). rEFInd will also handle removing rEFIt for you: [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

Alternatively, and this is my preference, you can simply remove rEFIt all together. rEFIt and rEFInd are not boot loaders; you don't need them to boot Linux. I think most people just set them up because they found instructions saying they need to. Personally, I've found them to be more trouble than they're worth, so I just use Apple's firmware boot manager. It's not as featured, but it's reliable and gets the job done.

---

### Post by sumethc on 2012-12-05
Thanks, [trogdor1138]("http://ubuntuforums.org/member.php?u=806935"). Actually I was contemplating removal of rEFIt a couple of weeks ago when I found out that once the Linux partiton had been installed it could then be safely removed. The only reason I kept it was just in case syncing of partition tables is required. That might have been a false presumption on my part; and, as you suggested, it's a lot faster to use Apple's firmware boot manager. I just plain forgot to try that out in spite of the fact that before the problem occured I occasionally just pressed Option key and selected the Windows badge on starting up. As for rEFInd I have read the documents from its developer but found it to be a bit of an overkill as far as my need was concerned. Thanks for the suggestion, though. I really love running Kubuntu, it makes my MacBook twice as fast than running on Leopard.

---

### Post by trogdor1138 on 2012-12-05
Yeah, I'm actually running Kubuntu myself; some of us are just KDE guys ;)

By the way, you can actually sync up your MBR tables again when necessary from within OS X. If you check out Rod's site, which I linked earlier, he's also released a utility he calls GPT fdisk. Among its many features is the ability to create a hybrid MBR of the type used on Intel Macs for Boot Camp. I use this myself, and it's worked reliably through all kinds of partition meddling thus far.

---

### Post by sumethc on 2012-12-05
Thank you once again, I have just made a quick reboot and found that it was much faster forgoing rEFIt on boot up, I will check out GPT fdisk as you suggest. For the record, though, I found Linux Mint UI to be quite aesthetically pleasing but rather limited. It took me only a couple of hours to decide I need something that is much more configurable like KDE. Thank you kindly indeed!

---

