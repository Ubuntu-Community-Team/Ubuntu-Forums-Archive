---
title: "Can I use Ubuntu to reclaim my data?"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Randybob on 2007-06-30
OK, here's the story: I made a n00bish mistake a while ago, encrypting data in Windows XP, finding that I had to reinstall Windows XP, and not backing up the key first. I lost some 20+ gigs of data, much of it was restored from backup, but not all of it. It's now sitting dead on my hard drive, inaccessible since Windows won't let me touch it. If I dual-boot with Ubuntu, can I move that data to a FAT32 partition and get it back? Would I need ntfs3g in order to do it?

---

### Post by C.S.Cameron on 2007-06-30
Randybob:
I have installed Ubuntu on a USB stick.
When I boot It I can access every thing on the computers hard drives.
I think this is one of the main reasons for Linux boot CD's.
Good luck
Cork

---

### Post by expatCM on 2007-06-30
I do not quite understand .....

You are dual booting already or not?  Just thinking that you need to be a bit careful not to overwrite anything if you decided to set up a dual boot.

Your Windows is on an NTFS volume?  It is this same volume where the encryption key was?

Your data is on a separate FAT32 volume but encrypted or is it  on the Windows drive?

It seems to me that this should not be impossible if you can recover the encryption key.   However, in the first instance I would personally approach this as a Windows exercise using a program like PC Inspector File Recovery which is a Windows program which can recover files even after a format.
[http://www.pcinspector.de/file_recovery/uk/welcome.htm](http://www.pcinspector.de/file_recovery/uk/welcome.htm)

You may also want to consider the use of SpinRite which I understand can be very effective
[http://www.grc.com/intro.htm](http://www.grc.com/intro.htm)

No doubt there will be Ubuntu focussed responses though .....

---

### Post by Randybob on 2007-06-30
> **expatCM said:**
> I do not quite understand .....

You are dual booting already or not?  Just thinking that you need to be a bit careful not to overwrite anything if you decided to set up a dual boot.
I am planning on it. I've gotten some money and will probably be getting a new hard drive soon, and I plan to dual-boot with Ubuntu on the new drive.

> **expatCM said:**
> 
Your Windows is on an NTFS volume?  It is this same volume where the encryption key was?

Your data is on a separate FAT32 volume but encrypted or is it  on the Windows drive?
There are two NTFS volumes on my first HD. One has Windows, the other has data. The data is still encrypted, and Windows will not decrypt it, since the key was on the system partition, which I wiped when I reinstalled Windows. What I want to do is bypass Windows and move my data to a FAT32 partition, which will strip the encryption and enable me to use the data again. 

> **expatCM said:**
> 
It seems to me that this should not be impossible if you can recover the encryption key.   However, in the first instance I would personally approach this as a Windows exercise using a program like PC Inspector File Recovery which is a Windows program which can recover files even after a format.
[http://www.pcinspector.de/file_recovery/uk/welcome.htm](http://www.pcinspector.de/file_recovery/uk/welcome.htm)

You may also want to consider the use of SpinRite which I understand can be very effective
[http://www.grc.com/intro.htm](http://www.grc.com/intro.htm)
I'll see if they do anything, thanks. If there's a way I can get at it without the key (which I am hoping is possible with Linux) I'd like to know it.

---

### Post by expatCM on 2007-06-30
In all honesty I do not think moving the data is going to have any impact on the encryption.   You need to recover that encryption key, that is imho the only way forward.

How to recover the key is the most important element here since you want to minimize any write activity on the Windows drive so that recovery activities are easier.  So if you are to install any new software ....  let it be installed on the spare space on the data partition and not on the Windows partition where it could overwrite space making the key recovery more difficult.

What encryption program did you use?  Are you sure that the key is portable in that it can be used in another system and still access the data?

---

### Post by Randybob on 2007-06-30
> **expatCM said:**
> In all honesty I do not think moving the data is going to have any impact on the encryption.   You need to recover that encryption key, that is imho the only way forward.

How to recover the key is the most important element here since you want to minimize any write activity on the Windows drive so that recovery activities are easier.  So if you are to install any new software ....  let it be installed on the spare space on the data partition and not on the Windows partition where it could overwrite space making the key recovery more difficult.

What encryption program did you use?  Are you sure that the key is portable in that it can be used in another system and still access the data?
I just used the built-in Windows encryption. It stores the key in a certificate on the system partition which I retardedly did not back up. It didn't even occur to me to do so, since the darned A+ textbook didn't even mention the existence of a key, let alone the importance of backing it up. 

Moving the data to a FAT32 partition SHOULD strip the encryption. The only problem is Windows won't let me move it since the key is gone (even though I reinstalled with the same CD). If another OS will let me access an NTFS partition and move the data to a FAT32 partition, I should be golden.

---

### Post by expatCM on 2007-06-30
Think you need advice of deeper expertise than my own here.   I do not believe that moving the data will remove the encryption ....  to me that would represent a big security weakness.

However, if you want to access the data and move it to a FAT32 partition then you should be able to do so with and Ubuntu Live CD (just a normal install CD).  Boot your system from the CD (so Windows is not started at all) and you will be able to read the data on the NTFS partition and copy it to another location.  Copy is perhaps better than move in this case.

---

