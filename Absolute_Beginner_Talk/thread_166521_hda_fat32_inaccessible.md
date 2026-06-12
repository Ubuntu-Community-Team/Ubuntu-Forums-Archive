---
title: "hda fat32 inaccessible"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-04-26
I have hda1 for windows and 30 GB empty drive hda5 ... my linux is on hda6.

hda5 format was ntfs, but as I have learnt, ntfs on ubuntu is read only. so I formatted hda5 and converted it into fat32. now as I am trying to mount it it gave me this output in terminal:

```

mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Somebody please tell me what's happening :(  ...

---

### Post by aysiu on 2006-04-26
How did you try to mount it?

---

### Post by Ensnared on 2006-04-26
How did you try to mount it?

EDIT
Erm, yea, what he (she?) said 8)

---

### Post by Isoss on 2006-04-26
```
sudo mount /ISOS
```
OR
```
sudo mount /dev/hda5
```

---

### Post by aysiu on 2006-04-26
You need parameters if you're mounting manually, and if you're not mounting manually, you need the appropriate parameters in your /etc/fstab entry.

[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by Ensnared on 2006-04-26
Is the entry listed in /etc/fstab?

Try this:```
sudo mount -t vfat /dev/hda5 /ISOS
```

---

### Post by aysiu on 2006-04-26
Or ```
sudo mount -t vfat /dev/hda5 /ISOS -o iocharset=utf8,umask=000
```

---

### Post by Isoss on 2006-04-26
Oh .. sorry for that ... it's working ... I thought after formatting the drive it would be still at the mount point .. but thanks very much ... I am new to linux, I still need more time to understand how it works.

---

### Post by Isoss on 2006-04-26
Ok ... shouldn't FAT32 be writable and executable in ubuntu?

I can't do any copy-files to it ... what can I do?

---

### Post by Ensnared on 2006-04-26
It's probably just mounted with owner/group root, which means only root can write to it.

To fix that, mount it with this:```
sudo mount -t vfat /dev/hda5 /ISOS -o uid=1000,gid=1000
```...which will make the user with UID/GID 1000 the owner instead (which should be you on a default Ubuntu installation with only one user other than root).

Alternatively, you can use the mount-line aysiu posted (with the umask=000) which will make everything readable and writeable by everyone.
I've never used the iocharset-option, but chances are that's why I've had some issues with filenames becoming funky 8)

To make this default in /etc/fstab, modify the appropriate line so it looks something like this:```
/dev/hda5    /ISOS    vfat    iocharset=utf8,umask=000    0    0
```

---

### Post by Isoss on 2006-04-26
Thanks guys ... it's working now ... thanks a lot. Now of course I need more explaination on these commands ... I don't really understand the way they work and what does UID/GID stand for ... I don't wanna learn these commands by heart without understanding .. can u please explian what these mean? and why we choose utf8 for the iocharset? and what are those numbers ... 

hope the explaination won't be tiring for you ... but at least can u direct me to some link that explain everything?

Thanks again.

---

### Post by aysiu on 2006-04-26
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by Ensnared on 2006-04-26
UID = User ID, GID = Group ID. It's a number identifying a user or a group within the system, and the mapping of these to the actual usernames and groupnames can be found in the files /etc/passwd and /etc/group.
When you add a new user to Ubuntu, he/she will be assigned an UID and a GID - usually they're the same. The first user added to a fresh installation is 1000, the second will be 1001, etc.
The UID/GID's below 1000 are usually used for system-accounts - that is, user-accounts only used internally by programs and daemons (or services, as some now call them). These accounts never actually log in to the system, but are used to make certain programs and daemons run with the privileges of these specified user-accounts.
The exception is the user "root" (UID/GID 0) which is the system administrator account and is often used for logging in (except in Ubuntu, where we're encouraged to use sudo/gksudo/kdesu to perform administrative tasks instead of actually logging in as the root user).

Specifying UID and GID when mounting a filesystem will make that user and group the owners of the mounted drive and it's contents, unless the filesystem itself specifies it's own owners, which is the case with native Linux filesystems. Windows filesystems do not have these owners defined like this, which is why it's often specified who will be made to own the files when mounting the drive instead.

As for UTF-8, there's a pretty good expanation on Wikipedia - [here](http://en.wikipedia.org/wiki/UTF-8). Basically, it's a system for mapping numbers (which computers use) to characters and letters (which humans use). Hence, it's a "character encoding", just like US-ASCII, ISO-8859-1, Codepage 437, Codepage 850, etc. I typed out a very very long explanation for it, and then realized I'd probably just confuse more than explain, so I leave that to Wikipedia instead ;)

The reasons you specify it is - to put it simple - so that the filenames given to the files and directories in Windows will have the same names when the drive is mounted in Linux. Without it, some characters might look completely different than they should.

---

### Post by Isoss on 2006-04-27
Thank you Ensnared. Really, God bless you for this efficient explaination.
I understand now the way these stuff work now.

---

### Post by Ensnared on 2006-04-27
My pleasure :)

I have however discovered something that seems to contradict the instructions as far as charsets go. When I booted after adding the iocharset=utf8 to my fstab-file, I noticed the kernel telling me that...```
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
```

So - while UTF-8 is the correct character set for NTFS, this indicates - actually it states outright - that it's not the proper one for FAT32. I'm not really sure what is the correct one though...

---

### Post by Isoss on 2006-04-27
Alright, in my linux I am using Arabic. I usually use win-1256 for arabic encoding in websites, do u think that would help?

---

### Post by Isoss on 2006-04-27
Helloooooooooooooo ... can somebody help on this?

---

### Post by bailout on 2006-04-27
[QUOTE=Ensnared]My pleasure :)

I have however discovered something that seems to contradict the instructions as far as charsets go. When I booted after adding the iocharset=utf8 to my fstab-file, I noticed the kernel telling me that...```
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
```

So - while UTF-8 is the correct character set for NTFS, this indicates - actually it states outright - that it's not the proper one for FAT32. I'm not really sure what is the correct one though...[/QUOTE]

OEM apparantly, though I don't know what this means in terms of the fstab line.

[http://msdn.microsoft.com/library/default.asp?url=/library/en-us/intl/unicode_42ib.asp](http://msdn.microsoft.com/library/default.asp?url=/library/en-us/intl/unicode_42ib.asp)

I noticed the same line after adding a drive using the recomended utf8 bit.

---

### Post by Ensnared on 2006-04-27
Ah... looks like it uses codepages. Try specifying "cpXXX" instead of "utf8", where XXX is the appropriate number for your language - see [here](http://msdn.microsoft.com/library/default.asp?url=/library/en-us/intl/unicode_81rn.asp) for a complete reference.

There are several possibilities there though, but I remember from the MS-DOS days (and currently DosBox) that I use cp865 there for nordic, e.g. Norway (yay!), Sweden, Denmark, Iceland, etc. For arabic, it looks like cp864 is the correct one.

---

### Post by Isoss on 2006-04-27
yes .. for arabic we use cp1256 ... I guess this shall work ... but can u tell me how can I figure out whether it's working or now?

---

### Post by Ensnared on 2006-04-27
[QUOTE=Isoss]yes .. for arabic we use cp1256 ... I guess this shall work ... but can u tell me how can I figure out whether it's working or now?[/QUOTE]
Mount the drive and check the name of a directory or file on it which you know contains other characters than just a-z or 0-9. If they look right, it's working ;)

---

### Post by manicka on 2006-04-27
I use something like this in my fstab without any problems 

```
/dev/hda5    /ISOS    vfat    defaults,rw,umask=000        0       0 
```

---

### Post by Ensnared on 2006-04-27
That's pretty much what I've had as well, using the default character-set rather than specifying anything. For someone using only the letters a-z (upper or lower case doesn't matter) this won't be a problem, but for everyone else it is likely to have unwanted effects.

I just did some actual testing on this to make absolutely sure what I should do to get it right. If you don't want to bother with details, the short conclusion is: use iocharset=utf8.

What I did was boot into Windows XP and made sure there were some files on one of my FAT32 partitions with the special characters "æ", "ø" and "å" of my language (Norwegian). I then rebooted into Linux and tried mounting the partition with different character-sets.

cp850 (Western Europe), cp865 (Northern Europe, default for FAT on my kernel) and iso8859-1 (Western Europe) all made the characters show up wrong. In console-mode they all simply showed a "?", and if I tried to enter the filename with command-line completion, the character would be removed completely (though I could access the file this way with no problem)

charset=utf8  made the characters show up as they should, both in console-mode and in the GUI.

I also tried various combination of specifying codepage=850 and codepage=865 as well, and I also tried mounting it as type "msdos" to make it ignore the vfat-portion, but none of the options would give the correct result. Using "-t msdos" even refused to work with iocharset regardless of the setting, and none of the codepage-settings made any difference for the filenames.

I also realised I compiled my kernel with cp865 as the default for FAT filesystems, but that didn't help if mounting them with no options.

I'm not really sure what's going on, but I did read several places, in tables comparing various DOS/Windows filesystems, that the character set for FAT32 was the system character set, although this seems to contradict the documentation from Microsoft. Still, VFAT (Virtual File Allocation Table) is the system Windows 95 started with to be able to use filenames longer than the MS-DOS 8.3 limitation (8 characters, a dot, 3 characters). This is a layer on top of the regular FAT, and so what may be happening is that the filenames in the actual FAT is stored in whatever character set, while the information in the VFAT is stored in the system default character set. If that was the case though, I'd expect my filenames to show up correctly when mounting the drive as msdos specifying the proper codepage, but that didn't happen.

But this is all irelevant anyway - the main thing is using a character set when mounting that will make sure your filenames show up correctly. And I have now reached the conclusion that you should not listen to the kernel when it tells you to not use UTF-8 ;) Atleast that's what I'm going to do from now on - I'm used to my FAT32 partitions acting as if they're case-sensitive anyway, cause that's how Linux has always treated them when entering the names of files and directories.

---

