---
title: "It destroyed it!!"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by HKeller on 2006-01-16
After having flipped through these forum pages for a while + seeing an installation on somebody else's computer, I yesterday decided to install 5.10 on my system, too. Wanting to keep the risk low and somewhat proud of my well running Windows-setup (as far as that is possible), it was to be a dual-boot configuration with Windows and Ubuntu physically sitting on two different harddrives ...

I read the manual entries regarding that topic, followed the steps through the installation, hit the 'ok' button to partition the second drive for Ubuntu, and - the Windows partition is gone. FDisk now only sees 8.4GB out of 40 on this drive, and by the way: Ubuntu doesn't boot either.

=> Does anybody know a way to restore my Windows partitioning information WITHOUThaving to re-format and re-install everything??

This was a _bad_ experience...:mad: 

Thanks for every bit of help I can get from you guys!

---

### Post by Stealth on 2006-01-16
Hmmm, what options did you pick for the partitions? You seem to mention 2 drives, are you installing Ubuntu on one of em? And what is GRUB saying? You can try the checking [here](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows) (the second part since you already have a Ubuntu disc) to restore GRUB. If GRUB just isn't working there is a way to rstore the NTDLR (Windows boot program) by using its CD and entering recovery mode. Then you can type FIXMBR...

---

### Post by L Campbell on 2006-01-16
[QUOTE=HKeller]After having flipped through these forum pages for a while + seeing an installation on somebody else's computer, I yesterday decided to install 5.10 on my system, too. Wanting to keep the risk low and somewhat proud of my well running Windows-setup (as far as that is possible), it was to be a dual-boot configuration with Windows and Ubuntu physically sitting on two different harddrives ...

I read the manual entries regarding that topic, followed the steps through the installation, hit the 'ok' button to partition the second drive for Ubuntu, and - the Windows partition is gone. FDisk now only sees 8.4GB out of 40 on this drive, and by the way: Ubuntu doesn't boot either.

=> Does anybody know a way to restore my Windows partitioning information WITHOUThaving to re-format and re-install everything??

This was a _bad_ experience...:mad: 

Thanks for every bit of help I can get from you guys![/QUOTE]

Hi, I'm sorry that you didn't have a better experience, here.

I, too, set my machine up as a dual boot, having windows and 2 hard drives.

Since I'm not a computer whiz, I elected to mount Ubuntu 5.10 on the second hard drive and just let it 'take the whole drive', theorizing that 'it' would know what to do as regards reformatting, or making any partitions that it needed.

This worked perfectly for me, so maybe you could give this method a try?

Hope this helps you.

---

### Post by HKeller on 2006-01-16
Sounds very similar to my hardware configuration, and I firmly thought that that was what I did.
Honestly, at the moment I'm not so concerned about getting Ubuntu to work -this right now would be only to play around with and I'm pretty sure the installation routine will get it up somehow.
=> I want to get my Windows back up, since this was a working configuration!

Thanks

---

### Post by Stealth on 2006-01-16
Do you have a live CD? If not, you can try geting Knoppix or something (cuz I'm not sure if Ubuntu does it or not) because then you should try booting that LiveCD to see if your Windows partition is infact intact. If you don't see any harddrives on the desktop or you don't see a standard looking "C:" structure in one of em (like hda2 has a Program Files and Windows folder) then there may be no way to recover it :( Hopefully though, seeing as how you weren't trying to mess with the first drive, this is a boot only problem with GRUB. BTW is Grub loading for you at all? Have you tried manually booting XP from the GRUB command line?

---

### Post by Sef on 2006-01-16
> Do you have a live CD?[QUOTE]

To get to GParted with Ubuntu's  Live CD:  Applications ----> System Tools -----> GParted.

[QUOTE]If you don't see any harddrives on the desktop or you don't see a standard looking "C:" structure in one of em (like hda2 has a Program Files and Windows folder) then there may be no way to recover it

You usually can have all or most of your data recovered, but you would have to take to a place that specializes in that type of work.

---

### Post by tim15856 on 2006-01-16
You may be able to recover the Windows partition using software. There may be free utilities out there that will work, you might have to Google for them. Here is an example of what you need, but it's not free. [http://www.runtime.org/gdb.htm](http://www.runtime.org/gdb.htm)

---

### Post by psyguy92 on 2006-01-16
I'm not an expert, but my general reccomendation is twofold.

1. Get a Live CD (knop. or Ubuntu) to poke around your drives.  This is probably the best way to see what actually is there.  I've recovered badly crashed systems using this type of CD.

2. If you find your windows files, it's best to try and backup any important data you see first, then I'd try booting with the Windows install CD and using the recovery option or fdisk mbr.  If for some reason you don't have your Windows install disk, there are good tools at bootdisk.com, but some require a small donation ($5?).

If fdisk is showing some space it recognizes, your files *may* still be intact.  If, however, you didn't carefully choose the partition options during the Ubuntu install and direct it to the appropriate disk, it may have repartitioned your Windows installation.  In that case, as another mentioned, you'd need a specialized recovery person to try to get your stuff.  Hopefully, it won't come to that.

If you get a Live CD and have trouble finding/mounting windows and think it's still there, post back and with any luck a Live CD guru will chime in at that point.  

Best of luck and sorry for your troubles.

---

### Post by Qrk on 2006-01-16
Did you defragment your Windows drive before resizing it? I had the same problem when I installed Gentoo without defragmenting Windows.

---

### Post by newuser111 on 2006-01-16
[QUOTE=HKeller]After having flipped through these forum pages for a while + seeing an installation on somebody else's computer, I yesterday decided to install 5.10 on my system, too. Wanting to keep the risk low and somewhat proud of my well running Windows-setup (as far as that is possible), it was to be a dual-boot configuration with Windows and Ubuntu physically sitting on two different harddrives ...

I read the manual entries regarding that topic, followed the steps through the installation, hit the 'ok' button to partition the second drive for Ubuntu, and - the Windows partition is gone. FDisk now only sees 8.4GB out of 40 on this drive, and by the way: Ubuntu doesn't boot either.

=> Does anybody know a way to restore my Windows partitioning information WITHOUThaving to re-format and re-install everything??

This was a _bad_ experience...:mad: 

Thanks for every bit of help I can get from you guys![/QUOTE]


sounds like either you didnt set the mount points properly, all you should have done is selected manual partition, and mounted the partition you wanted ubuntu on as / 

or you didn't install grub, do you even get a grub menu?

if you can boot with a windows boot disk get this program

[http://www.ambience.sk/experiments/MbrFix.exe](http://www.ambience.sk/experiments/MbrFix.exe)

this will restore a windows mbr, use like MBRFix /drive 0 fixmbr , 0 being your drive number, see [http://www.sysint.no/Nedlasting/MbrFix.htm](http://www.sysint.no/Nedlasting/MbrFix.htm)

---

### Post by Garyu on 2006-01-17
oh man... this experience has to suck big time... but... let me tell you something refreshing as an opposite...

I don't remember how, but a couple of years ago I totally screwed up my hard drive. I had LOTS of really important stuff on it, but it totally crashed one day. As I remember it was some windows instability problem resulting in a blue-screen and then nothing would work. 

So at that time I decided to give Linux a try. The distro was Red Hat. I installed it on top of the partition where my precious windows-drive used to be located, thus overwriting a lot of data. Once Linux was installed I started browsing around and suddenly found a folder containing all of my lost documents. Even when I thought I had installed Linux on top of them, it managed to save them somehow. I still don't understand how it happen, it was like witnessing a miracle. And now Linux is the only god I acknowledge in this world. :twisted: 

So, even though this might have been a bad experience for you... I also experience frustrations at times since I don't know much about the OS, I only use the software... But once in a while a miracle happens, and when it happens you can be darn sure that it isn't windows who is responsible for that miracle. :cool:

This will probably not help you in any way. I'm just saying, don't give up because you happened to encounter ONE bad thing...

---

