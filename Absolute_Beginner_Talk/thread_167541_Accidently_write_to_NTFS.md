---
title: "Accidently write to NTFS"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by cliff0108 on 2006-04-28
I don't know if I should be posting this on this forum or a windows counterpart (there ain't one)
but my questions :
I know you cannot write from Linex file system to Windows NTFS - and to work around that I have a usb drive formatted to Fat32 - and it works as an intermediary for file transfer.
I do wonder though - if I make a mistake and actually copy Linex file syatem files to my NTFS drive what will happen ? Will it completely screw up my Windows XP operating system ?
My research just says DON'T - does say what is likely to happen if you accidently do.
Does anyone know?

---

### Post by tburns on 2006-04-28
I don't think you can. I believe it is readonly mount so even root won't be able to write to it.

---

### Post by tburns on 2006-04-28
you could always try to edit a file on windows, and then report back to us...

---

### Post by mscman on 2006-04-28
While it IS possible to write to NTFS from Linux, the process is still very unstable and not reccommended.  Furthermore, to even write to NTFS, you have to create an "empty space" (blank file) to allow for the insertion (copying) of a file into the file system.  It's not very likely that you will accidentally do this, since it requires the installation of other programs.

---

### Post by patrick295767 on 2006-04-30
Only installing captive or paragon ntfs for linux can write in ntfs  ...
but not sure at all

---

### Post by Rinzwind on 2006-04-30
[QUOTE=cliff0108]I don't know if I should be posting this on this forum or a windows counterpart (there ain't one)
but my questions :
I know you cannot write from Linex file system to Windows NTFS - and to work around that I have a usb drive formatted to Fat32 - and it works as an intermediary for file transfer.
I do wonder though - if I make a mistake and actually copy Linex file syatem files to my NTFS drive what will happen ? Will it completely screw up my Windows XP operating system ?
My research just says DON'T - does say what is likely to happen if you accidently do.
Does anyone know?[/QUOTE]
You can not write to NTFS if you mounted it read-only. So you can't accidently do that ;)

If you do open your NTFS mount with write access you are only allowed to do things that do NOT change the filesize of a file or directory. If you then still like to live dangerously and would change a file a complete corruption of your NTFS partition is more than likely. 

So if it goes wrong it's totally screwed.

---

