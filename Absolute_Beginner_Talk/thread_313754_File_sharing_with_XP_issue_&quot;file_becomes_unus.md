---
title: "File sharing with XP issue &quot;file becomes unusable"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by Hot Sauce World on 2006-12-06
I am using 6.10 desktop and I have a folder that is shared on an XP box.  I can access the folder that has some images on it from the XP box.   I bring the jpeg into gimp, resize it then save it as jpeg and try to put it back it the XP folder that I have opened and the file seems to lose its functionality.  I assume a jpeg is a jpeg and it should not have an issue coming from my 6.10 box into the XP folder.... am I missing something?

Thank you for your thoughts.

Bill

---

### Post by Iowan on 2006-12-06
Unless things have stabilized since last I read, writing from Linux to NTFS is still "iffy".

---

### Post by Hot Sauce World on 2006-12-06
WOW... I am shocked to read that.  How can I get the edited image back to my XP box?  Could I mount the folders or drive from my XP box or do something different to be able to share files between them?

---

### Post by meng on 2006-12-06
It's not just that NTFS writing from Linux is iffy, it may not even be available on your system, i.e. NTFS access may be read-only. I would advise you have a third partition for data, and make it either FAT, which both OSs can read, or make it ext3, and install fs-driver on Windows.
Look here:
[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

---

### Post by burek on 2006-12-06
> **Hot Sauce World said:**
> I am using 6.10 desktop and I have a folder that is shared on an XP box.  I can access the folder that has some images on it from the XP box.   I bring the jpeg into gimp, resize it then save it as jpeg and try to put it back it the XP folder that I have opened and the file seems to lose its functionality.  I assume a jpeg is a jpeg and it should not have an issue coming from my 6.10 box into the XP folder.... am I missing something?

Thank you for your thoughts.

Bill

Make a Fat32 if u have only one PC
take care with permissiosn:
[http://ubuntuforums.org/showthread.php?t=284016&highlight=permissions+fat32](http://ubuntuforums.org/showthread.php?t=284016&highlight=permissions+fat32)
[http://ubuntuforums.org/showthread.php?t=275560&highlight=permissions+fat32](http://ubuntuforums.org/showthread.php?t=275560&highlight=permissions+fat32)
[http://ubuntuforums.org/showthread.php?t=277095&highlight=permissions+fat32](http://ubuntuforums.org/showthread.php?t=277095&highlight=permissions+fat32)
and so on


PC1linux to pc2linux = NFS

PC1linux to pc2windows : you can install samba on hte pc1 linux that will share a folder of pc1

---

### Post by scc4fun on 2006-12-06
> **Iowan said:**
> Unless things have stabilized since last I read, writing from Linux to NTFS is still "iffy".
I thought that with Samba it just sent the file as SMB (smbfs) not writing directly to the NTFS filesystem.

---

### Post by Hot Sauce World on 2006-12-08
Lets say you have a company with 100 XP users but you wanted to have linux file servers.... How would you set up the hard drives and software to allow that to work?

I don't need detailed code or anything but some basic guide lines that one would use.

My plan is to get used to Linux first with desktop and then replace a WIN2k server I have with 6.10 server.  I basically use it for minimal file sharing but most importantly as a file back up machine.

---

### Post by louieb on 2006-12-08
It sounds to me like you all are talking about two different things.
[LIST]
[*]File sharing over a network between machines running XP and Linux.
[*]File sharing on a single machine that Dual boots XP and Linux.
[/LIST]
It sounds to me that the original question refers to the first. 
If so what do you mean the JPEG seemed to loose it functionality. 
[LIST]
[*]Do you mean it no longer a picture. 
[*]or is it missing some of the extra stuff JPEGS sometimes carry  with them.
[/LIST]
If it no longer a picture the you got a problem somewhere in your network Samba should work. (are you trying to use NFS if so that Linux to Linux. I don't know how good XP is with that). 
If its missing the extra stuff then check the setting in GIMP. GIMP may have striped them out before saving it back.

---

### Post by Hot Sauce World on 2006-12-08
Louieb,

I do not have a dual boot box.  I shared a folder on an XP machine with some jpeg's in it.  I then found the file using my 6.10 desktop computer by going to network file browser and locating the shared folder.  I can open the folder and drag the images onto my 6.10 desktop open them up in Gimp save them as jpeg's but when I put the jpeg back into the XP shared folder it says the file type is unknown MIME Type application/octet-stream.

My ultimate goal ofcourse is to be able to move any file back and forth between my windows and linux machines.

---

### Post by louieb on 2006-12-08
Hum that is very strange. I have XP and Ubuntu PC's on my home network and I move JPEGS between them every now and then. But you got me curious and I just copied a JPEG from XP to Ubuntu, used GIMP to scale it down to 1/4 of original size and copied it back to XP. Just checked the scaled down image on XP and it looks fine.
I now wonder if somehow the the file extension .jpg got dropped off.
On XP open My Computer and go to the folder that has the photo that got messed up.
On the menu open Tools > Folder Options > View Tab > and uncheck the box "Hide extensions of known file Types". 
I bet that photo does not have the .jpg extension. If so rename it and add the .jpg extension to it and see what that does.
And that is my wild *** guess for tonight.

---

### Post by Hot Sauce World on 2006-12-11
You were right.  So I guess the question is why would it lose its extension during the process.  I save in GIMP as jpeg, I would think it would carry through.

Thank you for your help.

---

