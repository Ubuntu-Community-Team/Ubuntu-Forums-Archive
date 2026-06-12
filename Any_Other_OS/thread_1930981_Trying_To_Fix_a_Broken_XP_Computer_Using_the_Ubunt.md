---
title: "Trying To Fix a Broken XP Computer Using the Ubuntu 10.04 Live CD"
date: 2012-02-24
forum: Any Other OS
---

### Post by StewartM on 2012-02-24
Greetings,

I'm trying to help someone fix a broken Windows XP machine which fails at bootup with the error that:

C:\Windows\System32\Config\system

Was missing or corrupted.

I am trying to do this with the Ubuntu 10.04 Live CD because the owner has lost the original Windows XP CD. The computer is a single-core 2.4 GHz machine with 768 MB of RAM.

I can successfully boot the computer with the Live CD, and it mounts the internal Windows hard drive and says I'm the owner. When I go into the specified directory, I see what I think is probably the problem--a directory with a corrupted name:

C:\Windows\System32\Config\System\Sy#temprofile

Where "#" is a gobbletybook non-recognizable character. IOW, a corrupted folder name.

But--even though I am listed as the owner and have read/write permissions over the drive, I get an "Input/Output" error whenever I try to fix it. I have tried:

a) Renaming the folder

b) Copying the files inside the corrupted-name folder to a new folder named "systemprofile" in the top-level C:\ directory, then copying that folder back to the C:\Windows\system32\config\system directory. 

c) Deleting the corrupted folder after backing it up (as per b above)

In all cases I run into the "Input/Output" error.

Any ideas? Is there some NTFS protection setting for this folder that I need to defeat first?

-StewartM

---

### Post by sidzen on 2012-02-24
It sounds like a virus you need to defeat first.  With no backup or boot disk for XP, convince 'em to go with linuX!

---

### Post by lykwydchykyn on 2012-02-24
My guess is that the filesystem is marked dirty, or that it has some corruption causing these issues.  The Linux NTFS drivers are fairly conservative in not mounting a disk with problems r/w.

I would recommend getting an XP or BartPE disc that will allow you to do chkdsk, then do:

chkdsk /r c:

That usually fixes the majority of these kinds of problems.

---

### Post by lhowaf on 2012-02-24
If you were able to copy files from within that folder, it isn't likely corrupted. The problem was probably caused by malware.

Try [this]("http://answers.microsoft.com/en-us/windows/forum/windows_xp-system/windowssystem32configsystem-file-missing-or/7e419b32-39b4-4f13-aad7-4bb34b42d587") process from MS. I would just do this part: "copy c:\windows\repair\system c:\windows\system32\config\system."

Also, be careful if you get it restarted because there's probably something nasty in there. Maybe start in safe mode and start virus hunting.

---

### Post by Doeno on 2012-02-25
I went through this and I seem to recall that any XP re-instillation CD will work because your just going to use the repair disk part to do a 'Repair-MBR' and then exit. The only time that it didn't work was when aBoot NT-file became corrupt and that was it for Windows

---

