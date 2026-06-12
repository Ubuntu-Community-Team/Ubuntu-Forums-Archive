---
title: "A sym link in Linux is a ? in Windows?"
date: 2012-09-07
forum: Any Other OS
---

### Post by sunfromhere on 2012-09-07
Some time ago I asked how to have the same folder for Thunderbird and multiple accounts (it was answered in this [thread]("http://ubuntuforums.org/showthread.php?t=1914537")). After that I managed to share all the folders I ever needed in Linux.

But, where I work - there's Windows. LAN, 2 computers on XP, 1 on win7. I want to make the Thunderbird folder shared across the computers in order to have all of the 3 the ability to reply to e-mails, and for the e-mails to be downloaded to a single folder. I failed. Any ideas?

(if anyone's worrying about the privacy, security etc. - it's a small firm, 2 of us on the computers, private mails are not handled here.)

---

### Post by drmrgd on 2012-09-07
In DOS it's called 'mklink'.  

```
Microsoft Windows [Version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

U:\>help mklink
Creates a symbolic link.

MKLINK [[/D] | [/H] | [/J]] Link Target

        /D      Creates a directory symbolic link.  Default is a file
                symbolic link.
        /H      Creates a hard link instead of a symbolic link.
        /J      Creates a Directory Junction.
        Link    specifies the new symbolic link name.
        Target  specifies the path (relative or absolute) that the new link
                refers to.

U:\>
```

---

### Post by sunfromhere on 2012-09-07
So it should go like this:

MKLINK [/path to the thunderbird profile on main computer] some name Path to the thunderbird profile on the dependant computer

Or?

---

### Post by drmrgd on 2012-09-07
> **sunfromhere said:**
> So it should go like this:

MKLINK [/path to the thunderbird profile on main computer] some name Path to the thunderbird profile on the dependant computer

Or?

It's been a little while since I've done, that, but I think it's correct.  I'm not sure if you need to use the /D switch or not, since I think the Thunderbird stuff you want is in a directory.  I'd try something like:

```
mklink /D thunderbird_share \path\to\your\share
```

---

### Post by papibe on 2012-09-07
Hi sunfromhere.

In Windows you would create a '**Shorcut**'. Typically icons on your Windows Desktop are shortcuts, that is, links to where the actual program is.

AFAIR, you can create shortcuts in the 'File Explorer' using the right click options.

Regards.

---

### Post by sunfromhere on 2012-09-07
Papibe, shortcuts just give me the "Thunderbird is already running. Please close bla bla" on the dependant computer even when Thunderbird is not running on the main one.

I need to have one folder on computer A, and 2-3 clients on computers A, B, C. It's a POP mail so I can't have randomly mail downloading to 3 computers.

I shall try the other suggestions tomorrow and let you know how it works.

---

### Post by drmrgd on 2012-09-07
I might be wrong here, but I think a symbolic link in this case is better than a shortcut since the OP needs a program to write to a folder.  I sort of remember Windows' shortcuts not being suitable for that kind of thing since shortcuts are actually files rather than inode links.

---

### Post by oldfred on 2012-09-07
I do not know if it works for networks shares or not.

But I just edit my profile.ini to the path that the partition is mounted. I have a shared NTFS (on one computer), but the path in profile.ini is just the path I use to mount the folder that my Firefox and Thunderbird profiles are in.

Windows:

IsRelative=0
Path=F:\mozilla\thunderbird\profiles\lyu25irb.default

Ubuntu
IsRelative=0
Path=/home/fred/shared/mozilla/thunderbird/profiles/lyu25irb.default

Both use the same lyu25irb.default. in the data folder the path is mozilla/thunderbird/profiles which I wanted. Windows just sees it as F: and Ubuntu I mount as /shared in my /home.
network share in Windows are usually just a drive letter so I do not see why the same would not work.

[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

The main issue may be that two users cannot both open it at once. One would have to close it first before the other could open?

---

