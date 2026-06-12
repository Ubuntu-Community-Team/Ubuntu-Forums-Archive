---
title: "Plan of Action, ubuntu looks promising."
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by Blakeish on 2006-11-29
Good morning, I have a short fuse when it comes to dealing with most anything realted to a problem with the Windows (xp home) OS. I can usually work around where needed to get my computer back on track, but I seemed to hit a wall when I attempted to install windows on a new HD.

Originally I suspected my stock hard drive was failing, doing it's whole "death click" deal. After some time and switches here, BIOS changes there, it no longer clicks and by all accounts, looks good to go. When I thought it was on its last leg, however, I went out and purchased a new 160GB internal drive to replace it, out of panic. 

I'm thinking of using one or both of these drives in the following way, and since I'm not savvy to exactly how the integration btwn the OS's work, I'll just toss up what I would 'like' to achieve....here goes...

80GB stock HD, running windows XP, heavily tweaked to use as an online gaming/ multimedia profile. nothing more needed, really, I just want to be able to DL my music and movies, and play my games.

160GB drive, running ubuntu. used for web browsing, emails, anything aside from gaming, really.

Also, there is a 250GB usb drive hooked up that can be used as storage, but since its NTFS formatted, I assume its usewill extend to the windows OS only, as far as i know.



any thoughts? I have heard things mentioned about GRUB, as far as booting which drive and when. And all in all, this is mainly to experiment with all options available, while still utilizing the massive amount of HD space avaialbe to me.

any enlightenment on the topic, i thank you in advance. have a good one.

---

### Post by Falcorian on 2006-11-29
Dual booting shouldn't be a problem, you'll just get a menu when you power on asking you to select an OS.

However, I've never done it across two drives, so I don't know if there are any pitfalls that may come up.


I can however recommend creating a (probably small) fat32 partition. Both OSs should see it, and both can Read/Write from it, so you can transfer files back and forth with it. (You can of course make it a large partition and store files, say music, that you want access to from both OSs.) That's how I did it when I was dual booting, 15gig windows, 20g fat32 for music, and the rest split up for Ubuntu (10g /, 10g /home, 1g /swap).


So in the end, I guess I'm not that helpful, but maybe my post is worth your while. Good luck! :)

---

### Post by Giselle on 2006-11-29
I use grub to dual boot Kubuntu edgy and XP home across two drives. It works flawlessly for me and autodetected everything fine.

If you're installing both OSs from scratch make sure you install Windows first as it has a nasty habit of overriting the MBR during install. If Windows is already installed it should detect both drives fine (if not you have have to tweak some files).

It's also possible to mount NTFS partitions as read-only within Ubuntu. I think there is also some experimental read/write support for NTFS somewhere but I haven't got around to trying it yet.

---

### Post by gigaferz on 2006-11-29
disconnect windows from master cable.
Put the hard drive for ubuntu on the master cable.
Put a live cd and install ubuntu

Remember the jumper settings!!!

Put your windows in the slave section and ubuntu on the master.
After configuring the grub and mounting your windows partition
Then edit your grub to start as default on the windows partition and give it a 20 seconds delay, so you have time to select ubuntu when desired.


The extra thir drive you should leave it on ntfs for more windows games.

and movies or anything, you will be able to access to it from ubuntu but you will not be able to write on it, get all the codecs and vlc. 


This way you are tricking windows so you dont have too much trouble.

Thats the way I did it. 

So I also can go to any computer, install my ubuntu drive as master, and run ubuntu from there, (you may need to reconfigure the xserver )

---

### Post by scc4fun on 2006-11-29
> **Blakeish said:**
> <snip>

Also, there is a 250GB usb drive hooked up that can be used as storage, but since its NTFS formatted, I assume its usewill extend to the windows OS only, as far as i know.

<snip>

Linux is able to read NTFS formatted partitions, but cannot write to them--not even to edit ID3 tags. As mentioned there is experimental NTFS read/write access, but it is likely to break your windows partition. On the other hand you could use gparted or another partition editor (other than windows) to format the usb drive to FAT32. 

See [http://support.microsoft.com/kb/184006](http://support.microsoft.com/kb/184006) which states that Windows can handle large FAT32 partitions, but cannot create them and ScanDisk cannot scan them if they are over ~127.53GB (so you may want to create two partitions on the usb drive if you want to be able to use ScanDisk on it).

---

### Post by rbprogrammer on 2006-11-29
> **Blakeish said:**
> 
Also, there is a 250GB usb drive hooked up that can be used as storage, but since its NTFS formatted, I assume its usewill extend to the windows OS only, as far as i know.


sorry, i dont have much information to help you, but i read this and i thought i could at least show you something.  you could format that drive as ext3 (obviously back everything up first), then use this: [http://www.fs-driver.org/](http://www.fs-driver.org/)

it allows windows to access a linux formated partition/drive.  sorry i didnt have much helpful input to your problem, i just figured this would save a little bit of aggravation when all you need is to edit one file when your either in windows or ubuntu.

---

### Post by sindrum_murdnis on 2006-11-29
Yeah i have my box set up similar. You just install winblows first then go back and install ubuntu, Works out really nice. As far as the usb drive goes you should (don't quote me here) be able to access it in ubuntu, but your looking to do under windows which should be now prob. good luck

---

### Post by gigaferz on 2006-12-01
so, what happened to your installation plan?

Wich way did you go?

---

