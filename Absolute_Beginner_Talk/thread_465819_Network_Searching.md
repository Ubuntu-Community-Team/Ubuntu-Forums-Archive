---
title: "Network Searching"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Me! on 2007-06-06
How can I searching for some files on the intranet ?
I have many WinXP PCs on the network , I want to search on it !

---

### Post by ajmorris on 2007-06-06
> **Me! said:**
> How can I searching for some files on the intranet ?
I have many WinXP PCs on the network , I want to search on it !

I'm not sure i completely understand your question......
You want to do a search for files that searches the PCs on your network, is that correct?

---

### Post by jiminycricket on 2007-06-06
Look into [http://help.ubuntu.com/community/SettingUpSamba](http://help.ubuntu.com/community/SettingUpSamba) (in case you don't know where else to look or don't get more replies)

---

### Post by ukripper on 2007-06-06
You need to setup Samba before you can browse/ find other Windows XP PCs on your network.

---

### Post by Me! on 2007-06-06
I want to searching for files from PCs on the network

---

### Post by mlentink on 2007-06-06
Go to Locations>Network
This will show you available networks. Most likely you will then select 'Windows Network', which then will show you the computers in the network, if they have shared folders.  Click on a computer and then on the shared folder to look for files

---

### Post by ukripper on 2007-06-06
> **Me! said:**
> I want to searching for files from PCs on the network

There are three options for you :

1. Setup Samba to create LAN with other PCs and then do your Search on files.

2. Setup FTP server to upload/download files from one machine to another

3. Setup Webserver and upload/download from there.

In any of the above case you still need some kind of hardware connection. 

If you have router then best thing is you connect all your several PCs using option1 as above !

Goodluck.

---

### Post by Me! on 2007-06-09
I used SAMBA but How can I searching with it

---

### Post by ukripper on 2007-06-09
> **Me! said:**
> I used SAMBA but How can I searching with it

you have to set it up to use it.

In terminal type following to install:

```
sudo apt-get install samba
```

Once samba is installed then see if you can see other machines on network otherwise you have to change smb.conf

Follow this guide to setup peer to peer with samba:

[http://ubuntuforums.org/showthread.php?t=202605&highlight=HowTo+samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=HowTo+samba)

---

### Post by Me! on 2007-12-04
Thanks all

I found what I want here
[http://blogs.ittoolbox.com/linux/locutus/archives/how-to-find-files-in-a-remote-windows-network-from-linux-15454](http://blogs.ittoolbox.com/linux/locutus/archives/how-to-find-files-in-a-remote-windows-network-from-linux-15454)

so I wish to learning bash . it is powerful language .

:)

---

