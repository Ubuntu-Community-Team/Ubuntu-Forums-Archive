---
title: "Ubuntu and Windows networking"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by sdubois92 on 2006-09-28
We have a fair amount of computers in our house (IBM PC running ubuntu, MacBook, Windows Laptop and a Windows PC). Our Windows PC is shitty. Its 7 years old, made for Win98 but running XP, so its slow as hell. We are having some problems with it and will replace it with an iMac soon, but for the time being I would like to install linux on it and have some fun. Our windows PC acts as a storage center for all of our other computers through a shared folder on our network. If I were to install ubuntu, but partition the hard drive and keep windows on it, will our other computers still have access to the shared folders when Ubuntu is running or will it only work when windows is running on it.

---

### Post by echo $USER on 2006-09-28
> **sdubois92 said:**
> We have a fair amount of computers in our house (IBM PC running ubuntu, MacBook, Windows Laptop and a Windows PC). Our Windows PC is shitty. Its 7 years old, made for Win98 but running XP, so its slow as hell. We are having some problems with it and will replace it with an iMac soon, but for the time being I would like to install linux on it and have some fun. Our windows PC acts as a storage center for all of our other computers through a shared folder on our network. If I were to install ubuntu, but partition the hard drive and keep windows on it, will our other computers still have access to the shared folders when Ubuntu is running or will it only work when windows is running on it.

Yes, you would have to mount the windows partition (ubuntu usually does this automatically, atleaset dapper does).

---

### Post by sdubois92 on 2006-09-28
so would I be able to access the windows shared folder when ubuntu is running, sorry, your answer didnt make it clear to me.

---

### Post by echo $USER on 2006-09-28
> **sdubois92 said:**
> so would I be able to access the windows shared folder when ubuntu is running, sorry, your answer didnt make it clear to me.

Yes. First thing is to mount the windows partition in ubuntu so ubuntu can access it ( this is ususally done automatically when ubuntu boots).  Then you can install Samba or NFS so you can share folders and specify which folders you would like to share.

Here is a like to samba how to...
[http://easylinux.info/wiki/Ubuntu_dapper#Samba_Server](http://easylinux.info/wiki/Ubuntu_dapper#Samba_Server)

How to mount windows partition in ubuntu (if its not automatic)
[http://easylinux.info/wiki/Ubuntu_dapper#Windows](http://easylinux.info/wiki/Ubuntu_dapper#Windows)

NFS how to...
[http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)

---

### Post by sdubois92 on 2006-09-28
Okay another problem. im logged into windows, i put the LiveCD in, i hit restart but it boots up windows, not the live CD, any help?

---

### Post by echo $USER on 2006-09-29
> **sdubois92 said:**
> Okay another problem. im logged into windows, i put the LiveCD in, i hit restart but it boots up windows, not the live CD, any help?

Check you BIOS boot options to make sure boot from CD is first on the list, and boot from hard disk is second.  Then it should work.

---

### Post by Kulgan on 2006-09-29
on some computers you have to hit a key when the boot screen from the maufacturer is around (Dell, in blue, in my case). I have to press F12, then hit "boot from CD/DVD drive" or something.

---

### Post by Iowan on 2006-09-29
I'm wondering how well (IF) the Ubuntu machine will be able to share files on the NTFS partition (Default FS for XP).

---

### Post by doobit on 2006-09-29
> **Iowan said:**
> I'm wondering how well (IF) the Ubuntu machine will be able to share files on the NTFS partition (Default FS for XP).
This is a simplified description. Please see the HowTo for more detail. I'm just writing this so you will get an idea of how it should work with Samba.
Samba is a server and the Windows file and printer sharing utility is the client. The Windows client will see the folder that you designate as shared on the Ubuntu machine. You should set a username and password in the Samba configuration file, then open your My Network Places in Windows and you will see your Ubuntu machine name there with a + that will open and show your shared folder when you click it. You will also get a dialog box that asks for your username and password (the ones you set in Samba) After you enter them you will get access to the shared folder on the Ubuntu machine. You should be able to read and write to that folder from either computer.

---

### Post by Atomic Dog on 2006-09-29
> **echo $USER said:**
> Check you BIOS boot options to make sure boot from CD is first on the list, and boot from hard disk is second.  Then it should work.

It's a good idea to make your CD the first item sought to boot from.

---

