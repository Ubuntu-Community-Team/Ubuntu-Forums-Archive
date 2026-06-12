---
title: "[SOLVED] How does mount works?"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by mice on 2007-12-11
Hi,
Whenever i double click on the ntfs partition, it will be get auto-mounted . But too bad, I can't copy files into it.  

I've tried to mount the device through command line by adding "-t ntfs-3g" arguments, but it prompts me that the option is not supported (pardon me, i forgot the details). Things are fixed after i do an update by installing the ntfs-3g package.

1. I will like to know what the ntfs-3g package does to "mount" program? 
2. how does an installation performed in Ubuntu?

Sorry for the long story.

---

### Post by Rocket2DMn on 2007-12-11
In linux, drives are mounted a little differently than in windows.  Rather than being assigned a drive letter, they get placed at a directory within your filesystem, often in the /media directory.  Here you can mount all kinds of different devices like CDs/DVDs, other hard drives or HD partitions, USB flash drives, and even remote folders.  There are many types of file systems out there, linux uses the ext3 filesystem.  Others include reiser, ext2, FAT32, and NTFS.
Linux can read many types of file systems by default, but requires the ntfs-3g package to be able to properly write to NTFS, that's why you have to download and install the package.  Once you have it, linux can mount an ntfs file system just like any other device.

---

### Post by mice on 2007-12-11
Thanks for the info.

what has happen during ntfs-3g installation process?

does it contains a new version of "mount" program and replace the one in my local system?

---

### Post by Rocket2DMn on 2007-12-11
It does't change the mount program - it is a driver (similar to what you need for all your hardware devices).  It is basically an information source that tells mount how to properly read/write an NTFS file system.

---

### Post by GeorgiaBoot on 2007-12-11
How do you go about installing that?

I am going to be getting another external HD, and would like it able to be read by Windows and Ubuntu. It will be formatted to NTFS.

Thanks

---

### Post by Rocket2DMn on 2007-12-11
ntfs-3g is available in the repositories, simply open a terminal and type/paste
```
sudo apt-get install ntfs-3g
```

---

### Post by ayenack on 2007-12-11
Hello GeorgiaBoot take a look at this.

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Should help.

---

### Post by GeorgiaBoot on 2007-12-11
Props to both of you, answered it fully.

Thanks

---

### Post by ayenack on 2007-12-11
Cool buddy. Can you mark as solved so others can gain from your experience.

Top of page **Thread Tools**  **Mark as solved**.

---

### Post by GeorgiaBoot on 2007-12-11
One Quicky, when I installed it said this,

ntfs-3g is already the newest version.


Does that mean it is already installed? Do I need to do anything else?

---

### Post by Rocket2DMn on 2007-12-11
That means you already have it installed.  You might need to enable writing by going to Applications->System Tools->NTFS Configuration Tool and checking the boxes.

---

### Post by GeorgiaBoot on 2007-12-11
I would but for the life of me I can't find a button that says answered post! :lolflag:

Where is it? Then I will need to put another answered post on how to put answered posts!!

---

### Post by GeorgiaBoot on 2007-12-11
Under applications there is No system tools?

That is why I am a little confused as the Ubuntu site said to look there as well.

---

### Post by Rocket2DMn on 2007-12-11
You didn't start this thread so you can't mark it as solved
:lolflag:
problem solved!

---

### Post by Rocket2DMn on 2007-12-11
> **GeorgiaBoot said:**
> Under applications there is No system tools?

That is why I am a little confused as the Ubuntu site said to look there as well.

try ```
sudo apt-get install ntfs-config
```
If it's already installed and you don't see it, right click the Applications menu and select Edit Menus.  There should be a System Tools menu, click and it and check NTFS Configuration Tool

---

### Post by GeorgiaBoot on 2007-12-11
Yes!!

Okay I went to System>Preferences>Main Menu

To show system tools but when I checked the box it would only stay checked for about a second and then it would go unchecked.

Does this have to do with me not in root right now?

---

### Post by Rocket2DMn on 2007-12-11
You can run ntfs-config from a terminal.
```
sudo ntfs-config
```

---

### Post by GeorgiaBoot on 2007-12-11
Okay so I installed ntfs-config and it worked perfectly. 

Thanks for being patient; all problems Solved. :)

---

### Post by mice on 2007-12-11
One last question.

After i mount a device, that is a "mount option" availabe under some kind of device properties. 

previously i key in some arguments into the "mount option" edit box, it ends up the auto-mount failed consistently. I have to delete a xml file in one of the system-config directory to make the auto-mount works again.

I will like to add the ntfs-3g as the option during auto-mount process. What should i do to it?

Thanks again

---

### Post by Rocket2DMn on 2007-12-11
> **mice said:**
> One last question.

After i mount a device, that is a "mount option" availabe under some kind of device properties. 

previously i key in some arguments into the "mount option" edit box, it ends up the auto-mount failed consistently. I have to delete a xml file in one of the system-config directory to make the auto-mount works again.

I will like to add the ntfs-3g as the option during auto-mount process. What should i do to it?

Thanks again

I'm not sure what you're using that gives you a dialog box for mount options, but are you using an internal hard drive or an external USB drive?  If you're using an internal, you should add the device to /etc/fstab
I have a windows partition with ntfs-3g and the line in my fstab file looks like this:
```
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```

---

### Post by mice on 2007-12-11
It is an internal harddisk. original installed with WinXP. Ubuntu partition it during installation.

ok. the fstab approach  is something new to me. I'll try it out tonight (my time). Thanks again.

---

### Post by Rocket2DMn on 2007-12-11
No problem, check out these links for support:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-80128df9c1c4215d74e3f016b5cd2c2352da247c](https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-80128df9c1c4215d74e3f016b5cd2c2352da247c)
Good luck!

---

