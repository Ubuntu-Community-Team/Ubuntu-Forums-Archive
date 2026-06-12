---
title: "sharing folders"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by drizzy on 2006-09-17
Just have to say this board is great

Have just installed Ubuntu on a dual boot with Win XP and both work fine.

When i look in files manager i cant see the other instalation but expected that.

I want to share some files between and have gone into 
system/administrators/shared folders I have installed samba and shared the folder the path showing as /home/steve

The share properties show the path and share with "smb"

i have named the folder and clicked on "allow browsing folder"


now when i book into winders where will it appear as the drive unbumto is on isnt visible on my file manager on XP?

---

### Post by kidders on 2006-10-01
Hi there,

Your files are only shared as long as the Samba server is running!! Samba is a Linux implementation of the Windows _networking_ protocols.

---

### Post by podunk on 2006-10-01
I think what you want to do is called 
“mount”
the Windows hard drive – you can get files off of it while in Linux that way.

As far as I know – windows can not read a  Linux native drive. If you want to read Linux files while in Windows you will have to make a fat 32 partition and save your Linux work there.

A how to to “mount” your windows drive is here:
[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

Welcome to Linux!

---

### Post by mjpatey on 2006-10-01
Here's what I did:  A program called GPartEd will allow you to create a new FAT32 partition on one of your drives using existing empty space.  Mount it in Ubuntu, and mount it in Windows.  You can then save to this partition, open, copy files, etc., in both OSes.

My favorite thing to use this partition for is to put my Firefox Profile folder on it, and point both copies of Firefox to it, so you have the same Extensions, Bookmarks, etc., in both OSes!  I also have all my photos and music there.

You can find tutorials for each step I mentioned.  GPartEd is an ISO that you burn to CD and can boot from (much like the Ubuntu Live CD).  There are tutorials on burning a CD from an ISO, as well.

I'm sorry I can't link you to good tutorials for all this stuff, but I'm at work right now, and can't access my bookmarks. Let me know if you'd like some links, or just do some Google searching, which is probably faster.  I may not get back to my Ubuntu machine until later tomorrow.

Good luck!

---

