---
title: "Can't see shared folder"
date: 2009-01-03
forum: Apple Hardware Users
---

### Post by fraterf93 on 2009-01-03
I have Xubuntu installed on my G4 iMac, and Debian on my G3 iMac.  My Debian G3 has over 2 gigs of oggs I wanna transfer to the G4 without having to burn 4-5 CDs.  I have enabled File Sharing on the Debian machine for the folder with my music, but have no idea how to find it on my Xubuntu machine.  On Mac OS X file sharing is easy, with the machines just showing up in the Finder.  Not so easy with Linux, it would seem.  So how do I find the folder to copy my oggs?

---

### Post by Cheesehead on 2009-01-03
One method...
Command line Python tool to set up an instant **temporary** FTP server:

   1. Open a terminal on the machine you want to share.
   2. cd to the directory you want to share
   3. use 'ifconfig' to get the IP address of the sharing computer
   4. 'python -m SimpleHTTPServer' starts the server on port 8000. (minimize the terminal window so you don't accidentally close it)
   5. Other computers access the server by web browser: [http://xxx.xxx.xxx.xxx:8000](http://xxx.xxx.xxx.xxx:8000), where the xxx is the server IP address.
   6. Your computer accesses the internal server by web: [http://xxx.xxx.xxx.xxx:8000](http://xxx.xxx.xxx.xxx:8000) or [http://localhost:8000](http://localhost:8000).
   7. Kill the process CTRL+C in the terminal window to stop the server

Sharing is one-way; no uploading. No security. The entire contents of the directory are shared; no blocking. No logging. Use at your own risk on an unsecured network. Leave open at your own risk on any network.

---

### Post by fraterf93 on 2009-01-03
Thanks that works and all, but is downloading and installing SAMBA a waste of time and disk space?  I mean really now.  It should not be this hard.  When booted in Mac OS X I can see the share just fine.

---

### Post by cyberdork33 on 2009-01-05
> **fraterf93 said:**
> Thanks that works and all, but is downloading and installing SAMBA a waste of time and disk space?  I mean really now.  It should not be this hard.  When booted in Mac OS X I can see the share just fine.
well, I believe you have created a samba share. I am not sure how it work in xfce, but in Gnome, you just go to Places > Network and you can browse the machines on the network.

If you want to mount the samba share as a directory, you can do that from the commandline:
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by fraterf93 on 2009-02-17
Hi guys.  The problem is with Xubuntu and the XFCE Desktop.  It seems that there is no way to see networked computers in the XFCE file browser.  I switched to Gnome on my Xubuntu machine, and was able to see the shares, and transfer files.  Thx for your help all.  Now I have to rethink whether or not I want to continue to use and promote the XFCE desktop for modern computer use if I can't easily share files....

---

### Post by gwoodruff on 2009-02-23
You can mount the shared folder at boot and browse it with thunar. you can find how to's in the forums. Search on Thunar and Network Browse. This is the only thing I could find to bitch about in XFCE

Gary

---

### Post by fraterf93 on 2009-02-24
> **gwoodruff said:**
> You can mount the shared folder at boot and browse it with thunar. you can find how to's in the forums. Search on Thunar and Network Browse. This is the only thing I could find to bitch about in XFCE

Gary

Sorry, but that's not the kind of thing I'm interested in.  And this issue is a complete deal breaker for me.  I have been using Gnome on my Debian G3, and Ubuntu on my two G4s ever since.  I have multiple computers and need an easy and automatic way to mount and browse them.  I mean what good does it do to have all of your computers networked to each other if the user cant access them easly?


That said I now have gotta say as a Mac user of 6 years and a Linux user of 4 years, the Ubuntu distro has come such a long way!  It looks great, works great!  There is the issue of the cdrom not being detected in 8.10 though...  


I have also noticed in 8.10 How much Nautilus behaves like the Finder, especially in regards to networked computers, and external volumes.  Automatic.  I can browse my computers with exactly the same ease whether booted in Mac OS X or Ubuntu.  And you can believe my shock and pleasure when I first heard that Apple was putting "Spaces" in Leopard!  You can also believe how shocked and amazed to see that in Ubuntu 8.10 the animation for switching your virtual desktops is **exactly** the same as in Leopard!

Linux should have been what Mac OS X is now **years** ago.  I think it's really important right now that the Linux community make a supreme effort towards making the desktop elegant and easy!  Ubuntu is definitely leading the way!

---

