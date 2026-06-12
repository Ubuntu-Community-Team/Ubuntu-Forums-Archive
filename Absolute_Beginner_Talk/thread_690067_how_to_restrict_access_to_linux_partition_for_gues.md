---
title: "how to restrict access to linux partition for guest user in windows xp (dual boot)"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by cyneuron on 2008-02-07
hello there

i have windows xp and Linux as dual boot setup.

/dev/hda1 = windows xp

/dev/hda2 = linux swap

/dev/hda3 = linux root

/dev/hda4 = linux home

i access my linux home partition in windows xp by using ext2/3 driver installed on windows xp. but the problem is that the guest users on windows xp also have access to this drive.

i am unable to find a way to restrict access if guest user to just windows x drive.

can anybody please guide me in this regard ?

---

### Post by tact on 2008-02-07
I do not think there is any way to stop such access just by setting access rights or permissions.  Also goes for the situation where a person boots your PC using a linux (or any other OS) live CD, they will have root access and can override all permissions and access rights.

The only way to stop that happening is to use one of a variety of encryption tools to encrypt certain files or to encrypt the entire partition.  There are tools that do either and are cross platform (windows and linux).

I personally run the install time full disk encryption that is possible using the v7.10 alternate installer CD.  I believe there are (but have never looked for or used) tools to access such partitions from Windows.

I know I can access dm-crypt/LUKS partitions from other linux boxes, particularly simple from other gutsy boxes  - have done that, but never tried from a windows box.

---

### Post by fiddledd on 2008-02-07
AFAIK the only way to restrict access to Drives/folders in XP is by using NTFS, Windows doesn't handle EXT2/3 hence the Driver you are using. It may be possible to create a new NTFS Partition and use that as Home (copy over files.folders etc and change fstab), but I'm not sure about that at all so don't try it without a response from someone who knows what they are talking about. :) It may be possible to configure the Driver you are using in XP also, you'd have to read the help files about that. Sorry, not much help really.

---

### Post by fiddledd on 2008-02-07
Was thinking again and thought maybe you could do it using Group Policy. I found a longish thread that may help but I can't actually read it all ATM.

[http://www.novell.com/coolsolutions/trench/3600.html](http://www.novell.com/coolsolutions/trench/3600.html)

---

### Post by Archmage on 2008-02-07
Just ask M$, when they will release a decent ext3-driver.

---

### Post by tact on 2008-02-07
The thing is that if windows or some 3rd party releases some new way to access ext2/3 filesystems that respects permissions, as good as that may be, it still leaves the user the option to NOT use it and still gain access to portions of the file system that the owner wants to protect.

I suspect that the only way that would allow the owner reasonably complete confidence that this cannot happen, that the data CAN be accessed by him from windows but not accessed by others, would be to use a cross platform encryption scheme.

Then others cannot access what you do not want them to access under a dual boot system, or by booting by CD.

Happy to be corrected if someone has other ideas.  :)

---

### Post by cyneuron on 2008-02-08
thanks for responses....

i was also thinking on these lines...

ext3 driver still doesn't implement user permission natively. Windows xp can not implement it on third party driver.

can't use ntfs as home. i want to keep linux home partition on ext3 only. also ubuntu won't use ntfs as home.

about encryption....i am going to give true encryption a shot...

keep posting any more ideas....

---

