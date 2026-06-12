---
title: "wine and nvidia help"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by iand675@gmail.com on 2005-12-31
how do i set up wine? i tried installing it and running winecfg, but winecfg keeps locking up and stuff heres the terminal  output
```

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/ian', starting in the Windows directory.
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '/'
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/media/cdrom0'
err:winecfg:apply_drive_changes   unable to define devicename of 'E:', targetpath of '/media/windows'
err:winecfg:apply_drive_changes   unable to define devicename of 'F:', targetpath of '0'
err:winecfg:apply_drive_changes   unable to define devicename of 'G:', targetpath of '/mnt/cdrom'
err:winecfg:apply_drive_changes   unable to define devicename of 'H:', targetpath of '/home/ian'
err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '/'
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/media/cdrom0'
err:winecfg:apply_drive_changes   unable to define devicename of 'E:', targetpath of '/media/windows'
err:winecfg:apply_drive_changes   unable to define devicename of 'F:', targetpath of '0'
err:winecfg:apply_drive_changes   unable to define devicename of 'G:', targetpath of '/mnt/cdrom'
err:winecfg:apply_drive_changes   unable to define devicename of 'H:', targetpath of '/home/ian'

```

And the other problem i'm having is the nvidia drivers.
I hear that if they are working right, that a logo should be showing up somewhere. But that's not happening. I have nvidia-glx, restricted modules, nvclock-gtk, nvidia-settings, and nvtv.
The nvidia-glx and nvidia-settings packages were installed with automatix.

Anyways, if anyone could help me out, I would really appreciate it.

---

### Post by thekiller on 2005-12-31
[QUOTE=iand675@gmail.com]

And the other problem i'm having is the nvidia drivers.
I hear that if they are working right, that a logo should be showing up somewhere. But that's not happening. I have nvidia-glx, restricted modules, nvclock-gtk, nvidia-settings, and nvtv.
The nvidia-glx and nvidia-settings packages were installed with automatix.
[/QUOTE]

For this, open /etc/X11/xorg.conf and go under graphics card device section, there change driver [COLOR="Red"]nv[/COLOR] to [COLOR="Lime"]nvidia[/COLOR]. save and restart x server, you should now see the "magic" screen :D

---

