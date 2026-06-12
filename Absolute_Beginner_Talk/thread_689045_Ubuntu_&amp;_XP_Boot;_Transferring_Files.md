---
title: "Ubuntu &amp; XP Boot; Transferring Files"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by DevgruSeal on 2008-02-06
I have an Ubuntu and XP dual-booted machine, and now I have a new custom build with XP Pro x64 on it.

My intentions are turning my dual-boot machine into a general multi-purpose server using Ubuntu, but leaving everything in tact.

Essentially what I am trying to figure out is how to be able to use XP's networked drive feature with certain folders via NTFS mounted drives on my ubuntu. I can setup/use an FTP server for my other file-transferring needs, but I need to map a few folders to a drive on my new machine.

My understanding would be to use Samba, but I don't know where to start.

Thanks in advance.

---

### Post by oedha on 2008-02-06
if you want to see xp network drive.....just go to places - connect to server choose windows shared then enter the computer name and also the shared folder.....
is that what you want.........if you want to map it....like X, Y or Z
you will need smbfs

---

### Post by DevgruSeal on 2008-02-06
It isn't that I need to *see* a networked XP drive, it's that I need to create one so I can use my new computer to see the files I choose to share (Just like in XP) on my old computer via ubuntu.

---

### Post by oedha on 2008-02-06
hehehe...sorry....my english is not too good......
question : so do you want to make a folder in ubuntu to be shared ?

---

### Post by njparton on 2008-02-06
You need to install and configure samba.  Search for how to's, there are loads here and on the wider web.

---

### Post by DevgruSeal on 2008-02-06
I want to make a folder within a mounted volume (Windows C:\ drive mounted as /media/sda1) shared.

As a rough example (Using "Documents" for now)

In WinXP:
C:\Documents
In Linux:
/media/sda1/Documents

I want my 2nd computer (Which has XP Pro) to be able to access what is in /media/sda1/Documents by mapping that shared folder to Z:\ as a Network Drive.

---

### Post by oedha on 2008-02-06
i see now.......:)
go to system - administration - shared folder
click add button
choose teh folder that i'd like to share ( /media/sda1/Documents )
pay attention on read only box

then....open terminal
type :==> sudo smbpasswd -L -a username ( make a username and password ) this username and password can be different then the username and password of linux machine

---

### Post by njparton on 2008-02-06
You may also need to manually install "samba" and "smbfs".

Then configure "/etc/samba/smb.conf" with all the necessary options you require.  Search for a how to.

---

### Post by DevgruSeal on 2008-02-06
On typing **'sudo smbpasswd -L -a username'** as well as **'sudo smbpasswd -a username'** (which I read on the Samba documentation; and substituting username for my own username, of course), I receive this:

$ sudo smbpasswd -a username
[sudo] password for devgruseal:
New SMB password:
Retype new SMB password:
Failed to modify password entry for user username

---

### Post by njparton on 2008-02-07
You are replacing "username" with your actual username aren't you?

Judging by your last post it should therefore be:

```
sudo smbpasswd -a devgruseal
```

and repeat for all usernames requiring access to the shares.

---

