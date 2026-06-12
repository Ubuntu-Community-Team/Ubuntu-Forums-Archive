---
title: "Not sure if Wine is configured correctly"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by SleepJunkie on 2006-08-24
Yes, another Wine thread. I searched Google and the forums but I can't figure out the problem.

I'd like to install Steam ([http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)) and play CS. I was happy to see there was a guide made all ready. I'm not sure how to follow it, though. I used Synaptic to install Wine, and I think it's ready. So then I just tried wine SteamPowered.exe and got this:

```
matt@lampysys:~$ sudo wine Desktop/SteamInstall.exe
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/matt', starting in the Windows directory.
wine: cannot find 'Desktop/SteamInstall.exe'
```

I searched that error and saw that I need to run 'winecfg'. I ran that, pressed autodetect and made my cdrom drive a cdrom drive (which is irrelevant since Steam doesn't need CDs to run). I checked back at the console and recieved this:

```
err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '/'
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/media/cdrom0'
err:winecfg:apply_drive_changes   unable to define devicename of 'H:', targetpath of '/home/matt'
err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '/'
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/media/cdrom0'
err:winecfg:apply_drive_changes   unable to define devicename of 'H:', targetpath of '/home/matt'
```

If I run winecfg again, the drives are not there, so it doesn't look like it's saving right.

Am I going about this right? If it matters, I have 2 HDD's hooked up, both with XP installations.

Thanks,

Matt

---

### Post by SleepJunkie on 2006-08-24
I got it working. I just made the .wine folder and it's subdirectories. Somehow I did it as root, so it couldn't do anything with it. I just deleted those folders and ran winecfg. Everything is working great now.

---

