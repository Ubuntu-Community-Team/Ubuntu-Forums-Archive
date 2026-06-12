---
title: "Ubuntu to Ubuntu File Sharing"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by Max Roswell on 2006-07-11
Okay, I'm stumped.  I've searched the Wiki and the Forums, so if I missed something, apologies.

I have Ubuntu installed on my desktop machine.  I have a crapload of music there.

I just got Ubuntu installed on my sweet new laptop.  I'd like to listen to music on it.

How do I copy the files from the desktop to the laptop?  I went to System > Administration > Shared Folders, and it told me I needed Samba or NFS.  I picked NFS for no real reason.  

Now what do I do?  If Samba's easier, then I'll use it.  I couldn't find a simple how-to, but if someone wants to point me to one, then that's cool, too.

I don't plan on doing much sharing after this, and I have no need to share with any windows machines.  I just gotta get the good stuff over here on the lappy lap.

---

### Post by Kilz on 2006-07-11
> **Max Roswell said:**
> Okay, I'm stumped.  I've searched the Wiki and the Forums, so if I missed something, apologies.

I have Ubuntu installed on my desktop machine.  I have a crapload of music there.

I just got Ubuntu installed on my sweet new laptop.  I'd like to listen to music on it.

How do I copy the files from the desktop to the laptop?  I went to System > Administration > Shared Folders, and it told me I needed Samba or NFS.  I picked NFS for no real reason.  

Now what do I do?  If Samba's easier, then I'll use it.  I couldn't find a simple how-to, but if someone wants to point me to one, then that's cool, too.

I don't plan on doing much sharing after this, and I have no need to share with any windows machines.  I just gotta get the good stuff over here on the lappy lap.


Samba is much easier. You can then look in places in the network servers.  But if you want to use nfs [look here]("https://help.ubuntu.com/community/SettingUpNFSHowTo?highlight=%28nfs%29").

---

### Post by DigitalXpert on 2006-07-11
If you want maximum speed go the NFS route.  Its much better for linux <-> linux networking.  Easier to setup too, but thats just my opinion.

---

### Post by jimmygoon on 2006-07-11
Not to hijack your thread... or wait, yes I am.

Why is it nearly impossible to change back from samba to nfs or vice versa after you set it for the first time?

---

### Post by Kilz on 2006-07-11
> **jimmygoon said:**
> Not to hijack your thread... or wait, yes I am.

Why is it nearly impossible to change back from samba to nfs or vice versa after you set it for the first time?
It's not impossible, you can install both. Most people will use one or the other though. Just follow a howto [Samba]("https://help.ubuntu.com/community/SettingUpSamba") or [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo?highlight=%28nfs%29")

---

### Post by Max Roswell on 2006-07-11
This is getting frustrating.

4 hours to unsuccessfully copy some files from one computer to another.  

I can't for the life of me get the desktop set up with SAMBA to properly make the folder with my music in it available to the laptop.  I had it showing up in the network servers for a while, but all the files were read-only and I couldn't copy them over.

Now it doesn't show up at all.  I followed the Samba How-To above and it disappeared.  

This is seriously weak.

I'll try again in the a.m...this is a lot of effort to indulge my crappy taste in music.

---

### Post by Max Roswell on 2006-07-12
Okay, I got some sleep, and I'm much less pouty.  Ditto for my computers, because now, for no real apparent reason, it's ALMOST working.

I've got the proper folder shared on the desktop.
I can see that folder in "Network Servers" on the laptop.
I can copy SOME of the files over, no problem.

However, and this is my last remaining hitch here, for some reason, I'm getting a permissions error with **some** of the files.  Some I can copy over, some I get denied with a message that says I don't have permission to write them.  These are all files in the same shared folder.

I've checked the permissions as set on the desktop, and as near as I can see, all the files are the same.  The ones that I can copy have the same permissions set as the ones I can't.

Any ideas?  And thanks in advance.

---

### Post by someusernoob on 2006-07-12
Check out this link:

[http://ubuntuguide.org/wiki/Dapper#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29](http://ubuntuguide.org/wiki/Dapper#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29)

Change /home/public with the folder you actually want to share (you dont have to follow the mkdir command)

After this you can read/write to the folder without any problems. Scroll up if you want to set it up with authentication enabled (asks for user and password when you want to enter the other pc's folder)

---

