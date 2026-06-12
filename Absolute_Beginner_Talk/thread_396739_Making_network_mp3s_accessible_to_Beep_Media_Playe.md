---
title: "Making network mp3s accessible to Beep Media Player?"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by Wartooth on 2007-03-29
I somehow managed to stumble correctly through getting Samba up and running, which was awesome.  However, while Rhythmbox will play mp3s from my XP machine, BMP can't find them, and I'd really prefer to use Beep. 

 I've read over a couple of threads about this issue, but they pretty much went right over my head (I'm especially worn out this week, decreasing my already low brain power).

Is this what I need to do?  [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) Under: Mounting a Samba share

If so, there's quite a bit I don't understand and seems to be more than just copying and pasting everything that I see there. I don't want to copy/paste blindly and screw something up after having had a relatively easy time of getting Samba going in the first place. 

I'm looking for a bit of extra guidance, or perhaps a how-to with a bit more explanation than in that link, if that's what I'm needing to do.  

For example, 
> To allow non root accounts to mount shares,

Does that mean so long as there's only one account on my machine, it doesn't need to be done?  Or since I'm not logging on as root anyway, I'll have to do it for the one account on this machine..or..?

And why or when would I need to umount?

> In order to have a share mounted automatically every time you reboot,

I assume that without doing that, I'll have to fiddle with something each time one of the machines is rebooted?

> Create a file containing your Windows/Samba user account details: 

Does that need to be in a different folder than what I have already created for Samba since I got this up and working the other day?

Same with this one:

> Now create a directory where you want to mount your share (e.g. /mnt/data):

> Now edit the file system table (/etc/fstab) and add a line as follows:

I have no idea how I'd go about editing a file system table.  Sounds like something more complex than opening up a text editor, or is that just the terminology sounding scary?

I know this must sound like I am exceptionally thick in the head, but again, I'm not currently at my best, but would like very much to get this overwith so I can listen to music via BMP (I'm one of those last.fm dorks and like having the whole scrobbling plug-in thing).

Thanks.

---

### Post by cowlip on 2007-03-29
I'd recommend installing [fusesmb]("http://ubuntuforums.org/showthread.php?t=304131&highlight=fusesmb").  This allows you to browse your SMB network by 'mounting' it from your '/' directory, so you can access it from a terminal, from OpenOffice, or any program.  I found out about this when I began using hte XFCE file explorer called "thunar" which lacked smb support, but this fixed that and many other issues I had :)

The gnomevfs (*especialy* the gnomevfs) and konqueror kioslaves that support SMB browsing are not the best solutions in my mind, and even the Gnome coders agree and are looking at ways to replace gnomevfs.

---

