---
title: "what external usb HDDs work on 12.04?"
date: 2014-01-23
forum: Any Other OS
---

### Post by darinb6-w on 2014-01-23
Hi am running LM 13 which is Ubuntu 12.04.
i have read that many external HDDs do not work on 12.04. 
ie WD passport Ultra or seagate external usb HDDs.

I want to use it to make a copy of my home folder before i do a clean install of LM 17 or 14.04...

is there a way to do a clean install and keep my home folder intact? 
Thank you so much.
D

---

### Post by Herman on 2014-01-23
Hello darinb6-w,
> i have read that many external HDDs do not work on 12.04. 
ie WD passport Ultra or seagate external usb HDDs.
As far as I know all external HDDs should work in Ubuntu.

However, if the hard drive in question happens to contain special software for doing something extra such encrypting files or syncing to a cloud service then the software part of it might or might not work. It depends on whether the manufacturer of the software in the USB disk decided make their software operating system specific, to only work in Windows or Mac. I have not found any drive that doesn't work in Ubuntu, only the special software.

In Ubuntu we already have our own free backup software, file encryption software and our own cloud syncing service, so we don't really need the proprietary stuff. 
When shopping for external drives or any other hardware, we can often  save money and get a better deal by avoiding the fancy software and  going for drives with the best hardware specs instead. Sometimes a drive with extra software happens to be the best bargain. Most of the time it will be okay to just leave it there, it can't spy on us since it doesn't support Ubuntu, so it can remain there dormant except it will be cluttering up your new drive. Personally, what I do is simply delete all the proprietary software. 
> I want to use it to make a copy of my home folder before i do a clean install of LM 17 or 14.04...
Of course, it's always wise to always make regular backups of our files, and right before re-installing I always make a special backup of the contents of my /home/user directory, inculding the hidden files, (the ones with the . in front of their names, which you can see after pressing 'ctrl'+'h' on your keyboard). I normally export things like firefox bookmarks first too, and most important my encrypted accounts and  passwords database. You might have other things you'll need to think of backing up, depending on what program you have installed.
> is there a way to do a clean install and keep my home folder intact?
Yes, you can. Some people like to install Ubuntu with a separate /home partition. If you really want to, you can delete all other folders except /home, then shrink the partition and add other partitions around it with GParted. 
At install time tell the installer the partition you have your stuff in will be your separate /home partition. Do not format it. I tried that a long time ago and it worked okay for me. But remember, you still need to have all your files backed up first anyway, just in case something goes badly wrong, (rare, but can happen).
I have tried it (having a separate /home) and I didn't like it really, I would rather back up and  restore completely, and keep my operating system flexible and easy to  use. I can't stand fences and I like my new installation to be clean. I'm a lousy housekeeper and my /home directory seems to accumulate a lof of junk over time. An interesting thing about having a separate /home partition though, is we can have more Gnu/Linux operating systems sharing the same /home. For example you can dual boot between Ubuntu 12.04 and 14.04 when the time comes if you have a little spare hard drive space.

---

### Post by monkeybrain20122 on 2014-01-24
Everything I have tried works.

---

### Post by Bucky Ball on 2014-01-24
*Thread moved to **Other OS/Distro Support**.*

---

