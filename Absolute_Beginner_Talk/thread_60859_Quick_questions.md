---
title: "Quick questions"
date: 2005-08-29
forum: Absolute Beginner Talk
---

### Post by saB on 2005-08-29
I am going to reinstall Windows XP soon on my PC. I figured that, for the moments I'm not going to play games, I might as well install and use a Linux OS instead (for webbrowsing, emulators, etc). So my questions are:

- Is it possible that after you install WinXP, you install Ubuntu in such a way that you can choose which OS to use when you boot up the computer? If not, how do I do install a dual OS?

- Is Ubuntu well supported in terms of drivers (I have an ATI videocard)?

- How is the security for Ubuntu? Is it easily infected by spyware/viruses/malware/etc? Or is it immune to all these things?

- Can I view, and edit MS Office documents (Word, Excel, etc) in Ubuntu?

I really want to try something besides XP, which I've been using for years. I hope you all can help me!

---

### Post by KingBahamut on 2005-08-29
1. Yes, grub install detects windows part and puts it in the boot menu
2. Yes it is. 
3. Very secure. 
4. Of course, OpenOffice will become your friend.

---

### Post by weekend warrior on 2005-08-29
Yes, just make sure when you install XP to leave plenty of empty space on your drive for ubuntu, minimum around 2.5 GB preferably plenty more (at least twice) for all your personal files.

This depends entirely on the manufacturer, not linux per se. You can first try the LiveCD (no install required) or you can google for "your video card + linux" to see what success others have had or if there are any problems.

Immune, zero problems with that here  :) 

Yes, OpenOffice is very much like Word.


HTH

---

### Post by weekend warrior on 2005-08-29
Oh drat! beaten by a minute   :razz:

---

### Post by DJ_Max on 2005-08-29
To add to what KingBahamut said.

2.) The question really isn't wheither Ubuntu supports your hardware, but rather the Kernel it's using does. Which is yes, it has very good support for most hardware.

3.) Long story short, it's immune. Now, I could go on a paragraph or two on why you won't hear anyone posting about a virus or spyware problem (which is mainly due to the permissions system Linux has, as well as nothing as horrible as ActiveX), but I'll leave it at that.

4.) OpenOffice or Abiword. (Note OpenOffice is the equivalent of MS Office, while Abiword is just a nice word processor.

---

### Post by saB on 2005-08-30
Thanks for the answers! However, one thing left:

If I use the LiveCD to try Ubuntu, and I like it, can I use the LiveCD to install it as well? Seems a bit useless to download nearly 700 MB twice. And I don't have a DVD burner for the Install / Live combo.

Edit: And maybe I'm not paying attention, but the GRUB site says it's not publically available. How do I obtain this program then?

---

### Post by cnayak on 2005-08-30
[QUOTE=saB]I am going to reinstall Windows XP soon on my PC. I figured that, for the moments I'm not going to play games, I might as well install and use a Linux OS instead (for webbrowsing, emulators, etc). So my questions are:

- Is it possible that after you install WinXP, you install Ubuntu in such a way that you can choose which OS to use when you boot up the computer? If not, how do I do install a dual OS?

- Is Ubuntu well supported in terms of drivers (I have an ATI videocard)?

- How is the security for Ubuntu? Is it easily infected by spyware/viruses/malware/etc? Or is it immune to all these things?

- Can I view, and edit MS Office documents (Word, Excel, etc) in Ubuntu?

I really want to try something besides XP, which I've been using for years. I hope you all can help me![/QUOTE]

  If you're a complete green horn, then better try Xandros , Suse or Mepis. Ubuntu needs a fair knowledge of Linux. Btw, don't EVER try Linspire.

---

### Post by Lord Illidan on 2005-08-30
> If you're a complete green horn, then better try Xandros , Suse or Mepis. Ubuntu needs a fair knowledge of Linux. Btw, don't EVER try Linspire. 

I don't call this helping at all...give reasons why not to use Linspire.. and just directing towards another distro is not going to help.

For your information:

GRUB is not publically available, because it is installed with the distro you install. For example, if you install Ubuntu, you will also install GRUB automatically.

You can dual-boot painlessly, and if you follow the Ubuntu Guide, you can find out how to access NTFS files from the Windows XP partition..

Open Office can open and save files in Word, Excel, Power Point, etc, formats.. However VBA macros are out..

ATI cards are a bit of a pain under Linux, though their support is better than before. I recommend getting an NVIDIA card, any NVIDIA card works with Linux..

---

### Post by weekend warrior on 2005-08-30
Right, the idea of using the Live CD is simply if you're worried about compatibility. If you have a fairly standard computer, no exotic things - you should be fine. Goto [http://www.ubuntulinux.org/download/](http://www.ubuntulinux.org/download/) choose the download site nearest you and then click on one of the three install CDs, probably "Intel x86 install CD"

Then go [here](http://www.mrbass.org/linux/ubuntu/install/)  and have a read through on how the install process goes. 

After that you should be ready to start or ask more questions if needed. If for example you want o keep a previous OS, chime in for help. So long as you're ready to learn new things ubuntu should fit your needs. Give it a go.

---

### Post by cnayak on 2005-08-30
[QUOTE=Lord Illidan]I don't call this helping at all...give reasons why not to use Linspire.. and just directing towards another distro is not going to help.

.[/QUOTE]

    Sure, you can use Linspire if you don't mind shelling out the extra dollars. Btw, any rookie will prefer a system that will do all the configuration itself. AFAIK, Suse , Xandros and Linspire detected every piece of hardware and did the auto-mounting itself. Sure, you may say it's no big deal, but don't expect a rookie to download the latest alsa package to get the sound fixed and tinker with the fstab file - he'll simply revert back to windows. end of story.

---

### Post by weekend warrior on 2005-08-30
For the dual boot XP/ubuntu process have a look in the wiki  

[https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)

---

### Post by cnayak on 2005-08-30
[QUOTE=saB]I am going to reinstall Windows XP soon on my PC. I figured that, for the moments I'm not going to play games, I might as well install and use a Linux OS instead (for webbrowsing, emulators, etc). So my questions are:
I[/QUOTE]

  Regarding the gaming part, you can also game on linux :) I play Q3a on my ubuntu system. The best part is that you just download a small point release and link to the installed files on your Windows partition. My friend ( he uses Fedora Core 4) also plays Doom3 and UT2k3 on his linux machine. The downside is that , I noticed the framerates are a bit lower ( upto 10% in Doom3)  in Linux.

---

### Post by Lord Illidan on 2005-08-30
[QUOTE=cnayak]Sure, you can use Linspire if you don't mind shelling out the extra dollars. Btw, any rookie will prefer a system that will do all the configuration itself. AFAIK, Suse , Xandros and Linspire detected every piece of hardware and did the auto-mounting itself. Sure, you may say it's no big deal, but don't expect a rookie to download the latest alsa package to get the sound fixed and tinker with the fstab file - he'll simply revert back to windows. end of story.[/QUOTE]

Most soundcards are automatically detected.. mine was autodetected instantly. And the fstab file isn't that difficult to configure..

---

### Post by saB on 2005-08-30
So let me get this right: when I reformat the whole HDD, I'll make 2 partitions. A 4GB one for Ubuntu, the rest for Windows. I install WinXP first. After that, I put in the Ubuntu CD, reboot, and I'm able to choose to install on the 4GB partition. After successfully installing it, and rebooting the PC without any CD in it, I'll get the choice to boot either Linux or WinXP every time I boot up the PC.

Did I get that all right?

Edit: Also, I've been playing around with the LiveCD. It works perfectly fine. I like Ubuntu, it's pretty simple for me really. I just needed an installing guide that simple people can understand as well. Weekend Warrior's link is very helpful, but it doesn't show anything about Grub. How come?

---

### Post by weekend warrior on 2005-08-30
Essentially yes, that's how it should work. Perhaps more generous with the linux partition size (if possible), remember - *personal files*. As for GRUB examples, it's worth remembering that many of us don't dual boot and probably started with an older "junk" computer for linux. It's really the ideal situation for any OS, 1 per machine. That's how I do it, just linux for me. :) 

Check [this link](http://www3.telus.net/linux4u/ubuntu.html), last page you'll see GRUB.


HTH

---

### Post by Lord Illidan on 2005-08-30
[QUOTE=saB]So let me get this right: when I reformat the whole HDD, I'll make 2 partitions. A 4GB one for Ubuntu, the rest for Windows. I install WinXP first. After that, I put in the Ubuntu CD, reboot, and I'm able to choose to install on the 4GB partition. After successfully installing it, and rebooting the PC without any CD in it, I'll get the choice to boot either Linux or WinXP every time I boot up the PC.

Did I get that all right?

Edit: Also, I've been playing around with the LiveCD. It works perfectly fine. I like Ubuntu, it's pretty simple for me really. I just needed an installing guide that simple people can understand as well. Weekend Warrior's link is very helpful, but it doesn't show anything about Grub. How come?[/QUOTE]

Yes, you got that right. However you don't have to know anything about GRUB for that matter. It should install painlessly.

I also second what weekend warrior said. 4 gigs is a bit too little, especially if you are planning Ubuntu as a main OS. How large is your hard disk?

---

### Post by xmastree on 2005-08-30
[QUOTE=saB]So let me get this right: when I reformat the whole HDD, I'll make 2 partitions. A 4GB one for Ubuntu, the rest for Windows. I [/QUOTE]That's not what I would do.
I recently set up a dual boot from scratch on a friend's computer. 40GB drive. I made a 10GB primary partition for Windows, a 20GB secondary partition, containing one virtual drive, formatted as FAT32, and left the remaining 10GB untouched.

Install windows on the first partition ntfs, then install ubuntu in the remaining space and give it access to the 20GB shared partition.

That way you can share files between the two. Photographs, music, etc.

---

