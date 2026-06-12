---
title: "Hear me WINE"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by Quinch on 2006-01-18
Basically, I've installed WINE from a repository, ran winecfg and got...

```
quinch@Quinch:~$ winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/quinch', starting in the Windows directory.
```

Well, being ran for the first time, I expected some kind of error, what with nothing being configured yet, but once I hit autodetect in the config window and followed up with "apply", the terminal scrolled up with...

```
err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '/'
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/media/hda1'
err:winecfg:apply_drive_changes   unable to define devicename of 'E:', targetpath of '/media/hda2'
err:winecfg:apply_drive_changes   unable to define devicename of 'F:', targetpath of '/media/hdb1'
err:winecfg:apply_drive_changes   unable to define devicename of 'G:', targetpath of '/media/cdrom0'
err:winecfg:apply_drive_changes   unable to define devicename of 'H:', targetpath of '/home/quinch'
```

Any suggestions on where to go from here?

Regards,

Quinch

---

### Post by Mr. Electric Wizard on 2006-01-18
I think the one in the repositories is kind of behind the times...
If you install "Automatix" and install Wine from there, you'll get the latest and greatest.
Works well.

---

### Post by Quinch on 2006-01-18
[QUOTE=Mr. Electric Wizard]I think the one in the repositories is kind of behind the times...[/QUOTE]

Are you sure? I added the repository according to the instructions at winehq.com, [here]("http://www.winehq.com/site/download-deb")... I sort of assume that one would be up to date.

---

