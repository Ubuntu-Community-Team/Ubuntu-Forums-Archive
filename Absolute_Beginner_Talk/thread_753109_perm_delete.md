---
title: "perm delete?"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by waggingwabbit on 2008-04-12
when i emptied my trash it said that the files will be permanently deleted. is that really true with ubuntu? theres no way to recover deleted files later on if you accidentally deleted something?

---

### Post by Iowan on 2008-04-12
Like the Windows trash, once emptied - gone. To get in the trash, it's already been "deleted" once.

---

### Post by tango_ninja on 2008-04-12
This peaked my interest....anyone know of any articles explaning Ubuntu's trash can process in more detail?

thanks

---

### Post by Moop on 2008-04-12
I've also wondered if there was a secure file deletion app for linux like eraser for windows. I'm still not sure how it all works but I did find this article on recovering deleted files from a ext3 file system. 
[http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html]("http://www.xs4all.nl/%7Ecarlo17/howto/undelete_ext3.html")

---

### Post by Michael.Godawski on 2008-04-12
This should help a bit:
[http://www.techthrob.com/tech/securedelete.php](http://www.techthrob.com/tech/securedelete.php)

---

### Post by tango_ninja on 2008-04-12
beauty. thanks

---

### Post by waggingwabbit on 2008-04-12
Thanks! i am wondering though. i read the instructions where it said to do "man smem" for a list of options. When i did that it gave me -f -l -l -v. it doesn't explain what they do and theres 2 "l"s. can someone explain to me what those do?

also, is there something like CCleaner for ubuntu?

EDIT: ok forget the first question. i couldn't scroll down with my mouse earlier so i didnt get to see the rest of the manual. sorry! i still need help with the second question though.

---

### Post by Inxsible on 2008-04-12
Great link Michael. Would just like to mention that its not advisable to use it for every deletion, since it would involve a lot of disk writes thereby reducing the life of your hard drive.

Having said that, its definitely useful to delete personal stuff when you are planning to give away the computer or deleting some personal records.

---

### Post by Inxsible on 2008-04-12
This quote from the link however tells you that EXT3 atleast gives a basic sense of security > **Filesystems**
Starting with ext3, Linux filesystems overwrite files with zeros when you delete them, rather than just marking the file as "free space." Previous Linux filesystems, as well as the Windows filesystems (NTFS, FAT) use the latter method, which is why it is so easy to recover deleted files with software tools freely downloadable on the Internet. This is something to consider when deciding how much time you should spend wiping your drive.Although one could argue that overwriting it with random bits and then making them all zeroes would be even better.

---

### Post by waggingwabbit on 2008-04-12
what about a CCleaner for linux? is there such a thing? x.x

---

### Post by Joe Dinmore on 2008-04-12
> **waggingwabbit said:**
> what about a CCleaner for linux? is there such a thing? x.x

That's pretty much a registry cleaner, isn't it? Linux does not use a registry, so it doesn't create the Cr*p that CCleaner is designed to remove.

---

### Post by waggingwabbit on 2008-04-13
it doesn't? does it have anything similar to a registry then?

CCleaner doesn't only get rid of registry stuff though...

---

### Post by Joe Dinmore on 2008-04-13
I'm a newbie myself, so I'm not familiar with just how *nix does its magic.
I do know that you won't have problems with fragmented files and that your computer is much less likely to attract malware, but we'll have to wait for someone cleverer that I to tell us the hows and whys of it.

---

