---
title: "Group/Sharing Files on 8.10 and 10.5.6"
date: 2009-04-10
forum: Apple Hardware Users
---

### Post by vsiege on 2009-04-10
I have a server running 8.10. On this system I have several users, all of which are part of the same group. In each of their home folders I have put a link to a shared folder (i believe I used a umask to make sure all files and folders copied to this directory would be fully accessible by the group).

When I transfer files from my 10.5.6 mac to the server.... 
1. How do i make sure that all files created on my mac can be transfered without having to get file permission errors (and acls)? I do not want to have to do a "get Info" and change them for all files created.

2. How do I make sure that all files copied over to my server have read and write access for my server group?

FYI: I went and created the same group that existed on my server, on my mac. But when I create new files and directories on my mac... I do not see this group listed.... all I see is staff.

---

### Post by cyberdork33 on 2009-04-10
what sharing protocol are you using?

---

### Post by vsiege on 2009-04-10
I'm using samba for sharing. I got the file permissions errors when taking an Mac OS Extended (journaled). I'd like to have it setup so i don't see them either way.

---

### Post by cyberdork33 on 2009-04-10
> **vsiege said:**
> I'm using samba for sharing. I got the file permissions errors when taking an Mac OS Extended (journaled). I'd like to have it setup so i don't see them either way.
well, with samba, it doesn't matter what the filesystem is on the server, the protocol that the remote computer is using to read/write is samba. Only the server needs to worry about being able to write to the local file system.

---

### Post by vsiege on 2009-04-10
That makes sense but I'm not always going over a LAN connection.

I just realized I forgot to write the rest of this statement:
I got the file permissions errors when taking an Mac OS Extended (journaled) external hard drive and connecting it to my ubuntu computer. When I tried to transfer some files off of the external to the ubuntu computer it gave me the errors. The files are super huge and would benefit not having to go over a network cable as they would take hours to download. What do I do to correct this problem?

---

### Post by cyberdork33 on 2009-04-10
> **vsiege said:**
> That makes sense but I'm not always going over a LAN connection.

I just realized I forgot to write the rest of this statement:
I got the file permissions errors when taking an Mac OS Extended (journaled) external hard drive and connecting it to my ubuntu computer. When I tried to transfer some files off of the external to the ubuntu computer it gave me the errors. The files are super huge and would benefit not having to go over a network cable as they would take hours to download. What do I do to correct this problem?
ubuntu respects the file permissions on the HFS+ partition, and they are a different user than the one trying to access them. open a root nautilus window and you can access the files.

---

### Post by vsiege on 2009-04-10
So after I type:```
gksudo nautilus
```
The root File Browser pops up. Next I Use the browser to open my external HDD, then transfer the files. Do I have that right?

I'm assuming that (besides being dangerous if I mess with anything) that the owner of the files will be root? Or does it give ownership to current user that is logged in (preferable)??

Thanks for your help thus far

EDIT: i just tried it..I copied over the files then changed the owner and group... thanks

---

### Post by cyberdork33 on 2009-04-10
> **vsiege said:**
> EDIT: i just tried it..I copied over the files then changed the owner and group... thanks
yep, there ya go.

---

### Post by vsiege on 2009-04-11
i think I spoke too soon.... the permissions were only changed for the directory I selected... not to all the files and folders enclosed in that directory too... I could have swore this worked in the past.... do I have to set the user and group permissions via CLI achieve recursive changes?

I thought right-clicking the directory and changing the permissions, and applying them to the enclosed files and folders didn't work.

---

### Post by cyberdork33 on 2009-04-11
> **vsiege said:**
> i thought right-clicking the directory and changing the permissions, and applying them to the enclosed files and folders didn't work.
That should work, but you can do it from the cli. Something like
```
chmod -R +r DirectoryName
``` ought to do it.

---

### Post by vsiege on 2009-04-14
```
chmod -R +r DirectoryName
```
Whats the second r do : ```
+r
```
I believe the first -R is for recursive.

---

### Post by JGreenidge on 2009-04-14
I guess this is related, though I'm using Tiger on a G3 iBook with a Tiger and Jaunty partition. I acn see and open my Tiger icons on Jaunty's desktop but can't put/change any text files in there. I hate to seem like a kid who must be led around by the hand, but no techie and just want to learn Ubuntu enough to keep up with the afterschool kids using the Ubuntu PCs at the "Y". I know fixing this involves the Terminal somehow but I'm not messing around in there without pros showing the way! So how can I get Jaunty OpenOffice Writer to fully access files on the Tiger side of the partition? Please give step-by-step directions how if you can!

One last thing; how do I make Ubuntu partitions show up on Tiger's desktop?

Thanks,
Geekless Jim

---

### Post by cyberdork33 on 2009-04-14
> **vsiege said:**
> ```
chmod -R +r DirectoryName
```Whats the second r do : ```
+r
```I believe the first -R is for recursive.
add read permission

---

