---
title: "[SOLVED] Questions."
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by Powerman2442 on 2007-09-18
I have been looking into Linux more and more as I read information about it. I am still wondering about a few questions I have. What version of Linux should I try. Ubuntu seems like the overall favorite of many people. Maybe just because of it GUI?

My Laptop Specs
AMD Turion 64 X2 1.6 GHz
1024 MB DDR2 Dual-Channel Ram
120 GB HDD 61.1 GB Free, but I can make another 5 GB by removeing an unused partition.
ATI Radeon Xpress 1150 256MB GPU

All of my RAM is not avalible to use because some is used to make the GPU run from 128 MB to 256 MB. I still have 896 MB RAM free.

Another question is, is this computer good enough to run any version of Linux, Ubuntu for that matter? And can I run all the fancy settings, or not?

My next quesiton comes to installation. I would not have a problem adding a 15 - 20 GB partition on my HDD dedicated to Linux. But I would like to try it before I "buy it". In a sense anyways. I've seen a few videos of people useing a program called Wubi. You download it onto your desktop and it downloads the Linux Ubuntu ISO image and install it on your computer in Windows itself. I'm told it never touches Windows files, and you can uninstall it by selecting Windows in the boot options instead of Ubuntu and removeing it in Add/Remove Programs.

Also, should I use the 64 bit version of Linux since I have a 64 bit processor?

Also, another question if you have any clue. Do any games work with Linux, or no? I havn't heard of much support for Linux, but I also havn't heard much about support for Vista, yet many programs that arn't made for Vista run on it.

If anyone can help me sort some of my quesitons out I would be gratefull.

Thanks, Powerman

---

### Post by RomeReactor on 2007-09-18
Hi. Regarding some of your questions:
> What version of Linux should I try.
I would definitely suggest Ubuntu, but you can certainly try other distros. If you have the bandwidth to spare, you can check out other distributions that have Live CDs [here]("http://www.frozentech.com/content/livecd.php"). Or you can check [DistroWatch]("http://distrowatch.com/") to see which are the most popular distros at the moment. If you decide to try others maybe Fedora or Mandriva will be to your liking.

Then again, I still recommend Ubuntu. It's your choice, though.

> is this computer good enough to run any version of Linux, Ubuntu for that matter? And can I run all the fancy settings, or not?
I would say yes on both counts.

> My next quesiton comes to installation. I would not have a problem adding a 15 - 20 GB partition on my HDD dedicated to Linux. But I would like to try it before I "buy it". In a sense anyways. I've seen a few videos of people useing a program called Wubi. You download it onto your desktop and it downloads the Linux Ubuntu ISO image and install it on your computer in Windows itself. I'm told it never touches Windows files, and you can uninstall it by selecting Windows in the boot options instead of Ubuntu and removeing it in Add/Remove Programs.
I haven't used Wubi, so I can't really comment on it; however, Ubuntu comes as a Live CD, so you can check it out without installing it: it will run entirely on RAM (which will make it run slower than if it were installed, but reasonably fast)

> Also, should I use the 64 bit version of Linux since I have a 64 bit processor?
Considering your processor you can use either version. But if you plan on doing processor-intensive tasks such as transcoding video, then Ubuntu 64 bit will be faster; for more ordinary applications, you may not see a significant increase in speed, though. Again, your choice. Just note that enabling Flash and Java for the 64 bit version of Firefox is a little different than on the 32 bit version, and will require a few extra steps. Nothing extraordinary, though.

> Also, another question if you have any clue. Do any games work with Linux, or no? I havn't heard of much support for Linux, but I also havn't heard much about support for Vista, yet many programs that arn't made for Vista run on it.
There are many windows games--which I imagine you're referring to--that can run under Ubuntu using compatibility layers like Wine or Cedega. Just don't expect *every* windows game to run. You can search for games to see if they run on Linux in [Wine's database]("http://appdb.winehq.org/") or the [Gaming & Leisure]("http://ubuntuforums.org/forumdisplay.php?f=93") section of these forums.

Having said that, there are **a lot of very good games that run natively in Linux**; check out [this thread]("http://ubuntuforums.org/showthread.php?t=427205") to get to know some of them.

Hope this helps. And welcome to the forums!

---

### Post by Powerman2442 on 2007-09-19
Yeah, Ubuntu, although not Windows appears more like Windows the some of the other Linux versions I have seen. I'd like to try other versions of Linux as well, but Wubi only supports Ubuntu. At this point I am planning on trying Linux with Wubi first, but since it only supports Ubuntu I'll have to go that route.

Also, will have have any problem with drivers and such?

---

### Post by Steveway on 2007-09-19
Most distributions have LiveCD's.
That means, you download them, burn them, boot from them and try it out before you install it.
Try before you buy, like you said.

---

### Post by sailor2001 on 2007-09-19
> **Powerman2442 said:**
> Yeah, Ubuntu, although not Windows appears more like Windows the some of the other Linux versions I have seen. I'd like to try other versions of Linux as well, but Wubi only supports Ubuntu. At this point I am planning on trying Linux with Wubi first, but since it only supports Ubuntu I'll have to go that route.

Also, will have have any problem with drivers and such?

that's why it is always recommended to download the iso image and run as a live disk so you can check to see if all the residuals are working.......

---

### Post by Powerman2442 on 2007-09-19
Oh I didn't know you could download it and make your own LiveCD. I thought you had to buy LiveCDs. Is there a good site that has LiveCD download files? Or can I get them from anywhere that you can download the OS from?

Nevermind.  I found a guide on this site on how to make a LiveCD. :)

Thanks for the info.

---

### Post by Mr.Beast on 2007-09-19
Good luck with the live CD. Burn slow for more chance of it working.
One thing to watch out for or read up on at least is the ATI Graphics chipset.  Do search and confirm that this will work, you may save yourself a great deal of pain doing it now.

---

### Post by kteagan84 on 2007-09-19
> **Mr.Beast said:**
> Good luck with the live CD. Burn slow for more chance of it working.
One thing to watch out for or read up on at least is the ATI Graphics chipset.  Do search and confirm that this will work, you may save yourself a great deal of pain doing it now.

Yes, read up on the ATI Graphics chipset stuff. Other than that, your hardware looks fine :)

---

### Post by mysticmatrix on 2007-09-19
> **Powerman2442 said:**
> Yeah, Ubuntu, although not Windows appears more like Windows the some of the other Linux versions I have seen. I'd like to try other versions of Linux as well, but Wubi only supports Ubuntu. At this point I am planning on trying Linux with Wubi first, but since it only supports Ubuntu I'll have to go that route.

Also, will have have any problem with drivers and such?

Only ATI may make you cry, because ATI believes that Linux user need not experience good graphics.
There is no support for Desktop Effects(Although works with a simple workaround), and frame rates for most games would be half to 3/4 of what you get on Windows.

Apart from that, Wubi is great, specially if you have a fast hard drive.

Almost all Linux are free, both as in they cost no money, as well as you own the software you buy.
You can find more informations about distros, where to download(or to order) from this website

[www.distrowatch.com](www.distrowatch.com)

---

### Post by Arkasai on 2007-09-19
You may run into some issues with drivers, particularly with video.  I say this because I'm using an ATI X1100 (almost the same as yours, with slower clock rate and no dedicated memory) which is basically an Xpress200M.  ATI hasn't been very supportive of Linux in the past, but it's looking like that will change (eventually.)  So for now, if you want the fancy desktop effects and such, you'll have to use the unofficial drivers that enable 3D acceleration.

---

### Post by Powerman2442 on 2007-09-19
Well my whole reason for trying Linux is because I am bored of Windows. I really don't want a fancy GUI. Vista is goo and all but it hogs way to much power. I figured Linux would be less power consumeing. I have even been looking at used Imac G3's to test MAC OS. But that is another story. 

Oh yes I am pretty sure my chipset is 0x5975. I looked it up in DxDiag. Not sure if that is right. Says the same thing in Everest Home Edition. Not sure if I am looking at the right thing. Going to check out Device Manager and see what happens.

And yeah 1150 is basically a faster version of 300m. I can run Aero at full settings. But Vista just sucks my RAM.

---

### Post by Powerman2442 on 2007-09-20
I downloaded the ISO image but I have two in the folder I saved it in. I have an ubuntu-7.04-desktop-i386.iso and the same thing only ending with ".iso.part". Once file is 414 MB big and the other is 0 KB big. Used winMD5sum to check the integrity of the download, on each file above and neither match the lines on UbuntuHashes on help.ubuntu.com. Lost as to what to do. Any help would be great. The file last night said it was going to be 600+ MB big, but the ony file is only 414 MB. Did the download not finish or what? According to the download window it finished.

Hmm, I assume the .part file is an unfished download file. I tried to redownload from the same place with no luck. I downloaded the file from /http://releases.ubuntu.com/7.04/ and it said it was done according to FireFox. Could I try to download it from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and burn the image?

---

### Post by RomeReactor on 2007-09-20
That means it didn't finish downloading; if you're using FlashGet or a similar download manager, resume the download until it finishes. Or, as you said, download it from [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download"). You can install a Firefox add-on called [DownThemAll]("https://addons.mozilla.org/en-US/firefox/addon/201"); it will let you resume downloads. You could also download it via BitTorrent from [here]("http://mirrors.xmission.com/ubuntu-cd/7.04/ubuntu-7.04-desktop-i386.iso.torrent").

---

### Post by Powerman2442 on 2007-09-21
I redownloaded it and not I have one file that is the correct size. I will look into them two programs though. That would have saved me last night. No problem though. Going to check the file integrity then burn the LiveCD, I will tell you all how it goes.

---

