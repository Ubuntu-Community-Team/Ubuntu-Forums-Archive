---
title: "Sharing files between PC and wireless laptop..."
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by diggs on 2006-01-06
So I tried following the info in this link:
[http://ubuntuguide.org/#automountnetworkfoldersall](http://ubuntuguide.org/#automountnetworkfoldersall)
But it isn't working. the IP addy of my lappy is 192.168.1.102
and of my PC is 192.168.1.100
I want to be able to share the files on my desktop partitions, 
HDA5,6,7,8,9 and the folders within. Of course  Iwant to be able to read and write to them upon startup. 

Now assuming we can get this sharing up and running, how would I view/acess these files on my laptop?
Thanks!

---

### Post by bogoliubov on 2006-01-06
Hello. How you should go about depends on what OS you're running on the laptop. I share files between an iBook running OSX and a PC running Ubuntu. 

This is what the line in fstab looks like:
//192.168.0.2/christian /mnt/samba/ibook        smbfs credentials=/root/.smbcredentials       0       0

"smbf" means that I'm using Samba, which is a protocol to share files with Windows computers. It's perhaps not the fastest protocol, but it's quite easy and works with most systems.

What I've also done is sharing the files on my PC with the laptop. This is done by starting "Shared folder" (in the Administration part of the Gnome menu). WIth this small program you can add the folders you whish tro share. You can also set some general settings for sharing with a Windozecomputer.

Hope it helps!

---

### Post by diggs on 2006-01-06
hmmm. I should have posted that I am using ubuntu on both. I donut think that your code will help, but I will try using the shared folder option, which is working on my laptop, but being gay on my desktop. I'll just keep trying :)

---

### Post by diggs on 2006-01-06
well for some reason my shared folders keeps locking up on my desktop...why ?:(

---

### Post by buckley on 2006-01-06
an hour after installing ubuntu, i had finished copying 8gigs of music wirelessly from my laptop (XP) to my ubuntu desktop - i did the following

Places -  Network - Windows Network - workgroup 

and both of my other computers are there, and i was instantly sharing/copying files.  i dont see the need for further configuration =/

---

### Post by diggs on 2006-01-06
As was I. but for some reason, this is turning out to be a real whore!

---

### Post by frodon on 2006-01-06
If you have linux on both the easiest way is to use NFS : [http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)

---

### Post by diggs on 2006-01-06
oh my that looks tricky....I'll try that in the morning...

---

