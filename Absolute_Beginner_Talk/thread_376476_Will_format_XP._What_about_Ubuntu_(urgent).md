---
title: "Will format XP. What about Ubuntu? (urgent)"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by cyberbuff on 2007-03-04
Dear friends, I got some problems with XP (I know it's buggy): Can't work with IE (I hate it. But my ISP's portal is only on IE!) Can't downloaf any program and a lot other. So I made my mind to format it. I have ubuntu too. I don't want to harm it. Now tell what to do: If I format XP I guess there will be some problem with GRUB (beg your pardon if I am wrong). What to do? I want to Ubuntu protected and format XP. 
Regards

---

### Post by Shatrat on 2007-03-04
I'm not terribly familiar with the windows installer, but I believe that unless you repartition it shouldn't format the ext3 and swap partitions.
It will overwrite GRUB like you say, but you can reinstall grub from the ubuntu liveCD.

---

### Post by glotz on 2007-03-04
For restoring GRUB, see [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by NewWithoutClue on 2007-03-05
Depends on your plans after the format, and even the tool you're using to do so.

If your plans are to reinstall windows right after, then your current MBR (Master Boot Record aka Grub's Home) will be changed, resulting in Windows always starting up without question when you boot your PC. In order to fix this, you are going to have to reinstall grub. Do this using the live CD.

However, if you're using a different tool such as GParted, or even just the Windows Installer Format functions (without going through with the installation) then you can be assured the MBR wont be touched.

Ubuntu's Forums ROCK

---

### Post by Kuoi on 2007-03-05
I can tell you by experience that you can format your C drive (I pressume this is where XP is installed ) without any loss of Ubuntu.
Just choose the right partition for XP to format and install , but that won't be difficult.
Ubuntu isn't installed on the same partition as XP ,so you'll not loose Ubuntu .

After I did reinstall XP ,I lost my Ubuntu loader (Grub) , but I only had to follow the guide 'glotz' have mentioned above.
That replaced the Windows Boot loader  to Grub without any problem.

Good luck , Kuoi

---

### Post by cyberbuff on 2007-03-05
thanks so much for your replies. (you know why I like Ubuntu forums? It's because u guys always there!) 
well, the link glotz gave has more than one way to reinstall grub. I'd like the first one ("Using the Desktop/LiveCD while preserving Windows Bootloader") Then, what would be the root password? The one I use for the currently-installed system? or "root"?  Do reply!
Thanks and regards...
You rock!

---

### Post by glotz on 2007-03-05
I think it won't actually ask any root passwords since it's on a LiveCD. Please report back as I'm too lazy to find my LiveCD to try it. Let's rewrite that part of the article so that it'll be accurate. (You know why I like them wiki articles? Cause I can edit them 'till they're purrfect!)

---

### Post by cyberbuff on 2007-03-06
will reply a few days. Got exams ahead. Bye till then

---

