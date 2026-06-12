---
title: "Mounting NTFS"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by gutterballk7 on 2007-04-20
Sorry, this is a horrible question because I know it has been answered before... but I just can't find the appropriate topic while searching.

I am installing Feisty Fawn, and once I get past the ATI driver issues with the xserver, I'm going to need to mount my Windows NTFS volumes.

Of course, it automatically mounts when you log in as root, but not as the first user account Ubuntu installer makes for you. *Sigh* Additionally, if I mount it myself (I forgot how :( )  then it is only read-only unless I use sudo in the terminal.... which I'd rather use the file browser than the terminal.

If anyone could give me an answer or a link, that would be superb. I'll add it to my collection of links on my flash drive so I won't lose it. I just need to automount (fstab?) and make it writable by someone other than root.

Thanks a bundle!

---

### Post by taurus on 2007-04-20
NTFS driver is read-only and if you want to write to it, you need to install ntfs-3g first.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by gutterballk7 on 2007-04-20
See, I knew this was a dumb question.... if you go to Places > Computer and simply double-click the drive.... it just works. Heh.

But yes, it is read-only, so I may need to go do that.

---

