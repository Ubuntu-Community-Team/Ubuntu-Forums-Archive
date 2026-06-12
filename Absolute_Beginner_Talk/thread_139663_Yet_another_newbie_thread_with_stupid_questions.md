---
title: "Yet another newbie thread with stupid questions"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by Nunyah on 2006-03-04
Hey, kinda new to Linux.
I'd really appreciate to get some answers to my questions.

1. When I configured the system during install, I chose 1600x1200 resolution in X.
My screen won't view letters correct in this resolution, so I'm currently using 1280x960 which is okay, but I'd really like to use higher resolution.. Do I have to manually install Nvidia driver in order to work this out? How can I configure this again? (Like during the install where I chose what resolutions to pick from)

2. As mentioned in question #1 I managed to change resolution on desktop, but I'm still stuck with 1600x1200 before I'm able to log on Ubuntu and the letters is kinda schrewed, how can I tune down the resolution in order to fix this?

3. How can i view .avi files? Are these Windows only?

4. How can I make my USB hard drive work? Do I have to convert the file system from NTFS in order to browse and use its content?

Sorry for asking questions that probably has been told answers to a million times.

---

### Post by bluevoodoo1 on 2006-03-04
1 + 2. sudo dpkg-reconfigure xserver-xorg

3. [https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs)
Look under "the codecs"

4. Hmmm, I've never used a USB hard drive, but you probably don't have to convert it from NTFS. Ubuntu can read NTFS but not write to it.

---

### Post by stuporglue on 2006-03-04
> Do I have to manually install Nvidia driver in order to work this out? How can I configure this again? (Like during the install where I chose what resolutions to pick from)


No, you don't have to use the Nvidia drivers, but you'll get better speeds and 3d support with them. You don't have to install them manually though, search the forums or wiki, there are plenty of tutorials on how to do that. 

To reconfigure your graphics open a terminal and run "sudo dpkg-reconfigure xserver-xorg"

---

### Post by taurus on 2006-03-04
4.  If you plan to write to that external USB hd in Ubuntu and Windows, then better format it as vfat (or fat32).  If you format that as NTFS, then only your Windows can write to it and you can only read it under Ubuntu.

---

### Post by towsonu2003 on 2006-03-04
[QUOTE=Nunyah]
4. How can I make my USB hard drive work? Do I have to convert the file system from NTFS in order to browse and use its content?[/quote]
You can use gparted (search in synaptic) to repartition and format it (fat32). be **very very** careful not to format your own drive by mistake. also, if you have data in that usb thing, it will be erased for good during format. 
[QUOTE=Nunyah]
Sorry for asking questions that probably has been told answers to a million times.[/QUOTE]
I like that we don't have many people getting angry over this :)

---

### Post by Q4U on 2006-03-04
2. I do not know, I do not use an Nvidia card. However, it is possible that this is related to a font problem, rather than a video card (the graphics, the images and the larger text all look fine, right?). I suggest do some experiment with disabling antialiasing for smaller text, check this howto: [http://www.ubuntuforums.org/showthread.php?t=27665](http://www.ubuntuforums.org/showthread.php?t=27665)

4. You do not have to convert it, Ubuntu can read (though not write) NTFS. Try to plug it in, an icon should appear in the desktop. 

However, if it doesn't, check to see if it is mounted, open the terminal and type cat /etc/fstab (USB appear as /dev/sda or similar).

You might want to check out this tutorial written by an experienced user ([http://www.psychocats.net/linux/mountwindows)](http://www.psychocats.net/linux/mountwindows)). It focuses on a slightly different but related topic, it should contain information useful for you.

Also, check this thread: [http://www.ubuntuforums.org/showthread.php?p=196121#post196121](http://www.ubuntuforums.org/showthread.php?p=196121#post196121)

Hope this helps. Let us know how you're progressing. Q

---

### Post by Nunyah on 2006-03-04
Thanks for excellent answers, guys! After i reconfigured X and rebooted, the login screen showed up as it should, without schrewed letters. I attached the USB hd to my fileserver (win2003) as its my primary harddrive for unsorted downloads and it might as well stay there for now. I'm still gonna test your solution in order to know my options, Q4U.

[QUOTE=towsonu2003]I like that we don't have many people getting angry over this [/QUOTE]Hehe, found myself kinda surprised in numbers of friendly answers in really short time. Using the regular hardware/windows forums, I'd be a bit desperate and quite shamed to ask such simple questions as these! ;)

Any of you got some experience using Mono and .NET on Linux? I'ts not really a rush though, as I can remote desktop my server and use Visual Studio from there until I manage to search some answers!

Again, really appreciate the replies!

---

### Post by Nunyah on 2006-03-04
Got Mono to work with MonoDevelop as IDE thanks to Synaptic!

---

