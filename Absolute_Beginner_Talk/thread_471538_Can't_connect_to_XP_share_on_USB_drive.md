---
title: "Can't connect to XP share on USB drive"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Imsdal on 2007-06-12
I just installed Ubuntu on one computer. Another computer on my home network runs XP Home. On the XP machine, I created two shares with full rights to everyone. One share was created on the internal HD, and the other on an external USB HD.

Without doing anything on the Ubuntu machine, boths shares were immediately recognized. However, only the share on the internal HD works, so that I can access files etc. I have created several other shares as a test, and it is repeatable that the shares on the USB HD can't be accessed properly, whereas all of the shares on the internal HD can.

When I open the "USB share", I get the following error message:
  The folder contents could not be displayed.
  Sorry, couldn't display all the contants of "myshare"

Googling that error message, I get serveral hits that (as far as I can tell) concerns dual boots, and nothing about shares. What can I do to find and correct this?

---

### Post by gerscht on 2007-06-12
Can you access this USB share from a different windows machine?
I doubt this has anything to do with ubuntu, as samba (which is used to access windows shares) seems to be working, otherwise you wouldn't be able to access the other share.
It looks like as if Win is treating the USB drive differently... But who expected consistancy ;)

---

### Post by Big_Croc7 on 2007-06-12
hmm... I haven't used windows for a while, but here's a possible workaround until you find a real solution.  If you're using NTFS for the hard disk partitions you can mount the USB drive to a folder on the hard disk - I think the command is start, run, 'diskmgmt.msc' and somewhere there there should be an option to mount it.  If you mount to a folder inside the hard drive shared folder, you should be able to access the contents through the other share.  Maybe. ;)

---

### Post by Imsdal on 2007-06-12
Unfortunately, I don't have another machine to test. I used to have a laptop, and that could access all drives, but that was some time ago, and I may well have inadvertently changed something since then.

---

### Post by Imsdal on 2007-06-12
> **Big_Croc7 said:**
> hmm... I haven't used windows for a while, but here's a possible workaround until you find a real solution.  If you're using NTFS for the hard disk partitions you can mount the USB drive to a folder on the hard disk - I think the command is start, run, 'diskmgmt.msc' and somewhere there there should be an option to mount it.  If you mount to a folder inside the hard drive shared folder, you should be able to access the contents through the other share.  Maybe. ;)

Thanks, that was great to know. It was exactly like you said, and I could mount the USB drive as a folder in my internal HD. Sharing the internal HD folder works, but trying to browse down to the folder that is actually the USB drive still gives the exact same error message as before.

Any new ideas?

---

### Post by djchandler on 2007-06-12
> **Imsdal said:**
> Thanks, that was great to know. It was exactly like you said, and I could mount the USB drive as a folder in my internal HD. Sharing the internal HD folder works, but trying to browse down to the folder that is actually the USB drive still gives the exact same error message as before.

Any new ideas?

The first thing that comes to mind is that you may be re-using a folder name, and samba is getting confused which folder contents to retrieve. My second guess is that the root directory of the removable media must be shared also to get at the shared folder, not just the folder within that root directory of the removable device. Otherwise, give me a bit of time and I'll see if I can duplicate your problem. :o

---

### Post by Imsdal on 2007-06-12
> **djchandler said:**
> The first thing that comes to mind is that you may be re-using a folder name, and samba is getting confused which folder contents to retrieve. My second guess is that the root directory of the removable media must be shared also to get at the shared folder, not just the folder within that root directory of the removable device. Otherwise, give me a bit of time and I'll see if I can duplicate your problem. :o

The share names are unique and don't conflict with anything on either machine, except that I have tried naming the shares both the same as the actual directory and something else. And I have also tried sharing both the top level of the drive and a sub directory. No difference there, as far as I can tell.

---

### Post by djchandler on 2007-06-14
> **Imsdal said:**
> The share names are unique and don't conflict with anything on either machine, except that I have tried naming the shares both the same as the actual directory and something else. And I have also tried sharing both the top level of the drive and a sub directory. No difference there, as far as I can tell.

I duplicated your problem by creating an unrestricted shared folder on a USB drive in XP Pro. It has Samba flummoxed. Could be a bug in Samba, because I can't see a third computer in the workgroup at all either. Trying to connect to the XP Pro box gives the same error message you have been getting, and I can't access any of the shared resources on it at all.

---

### Post by djchandler on 2007-06-18
It wasn't easy to get my old shares on the XP box to remount either. I had to delete all references to it in XP before I could get to the other shares in XP from Ubuntu. This has to be a bug somewhere, maybe in XP's sharing routines rather than Samba. It even interfered with another XP box, my wife's computer, seeing my XP shares until I removed all reference to it on my XP. It was one of those things that should work, but doesn't and leaves you wondering what's going on in Redmond.
:o

---

### Post by circuitsurfer on 2007-11-17
Hello all;

I am having the same problem accessing a usb drive. It mounts fine and is shown on the desktop, but when accessing the share on MAc OSX I get alias is broken. I get this with my other drives if they are not already mounted on my linux system. This is another problem I have is that my internal drives no longer automount  since upgrading to gutsy.

Any help is greatly appreciated.

Linux and the community that supports it Rocks, and is laying foundations for the future of commerce.

---

