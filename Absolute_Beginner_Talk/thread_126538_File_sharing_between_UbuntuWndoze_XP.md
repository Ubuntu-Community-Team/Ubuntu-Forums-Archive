---
title: "File sharing between Ubuntu/Wndoze XP"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by rivervalleyprinting on 2006-02-06
I think I need Samba but is this the only program desinged for file sharing over a network with windows? I basically am looking to share mp3's from one computer to another for now and then hopefully as I learn how it works I will be able to do more. So is it Samba or something else? Thanks



Oh also I already have a network up and running with three XP machines a JetDirect print server and wirelless access. Please dont ask why I have 3 xp's running cuz I dont have a good answer for that

---

### Post by Robgould on 2006-02-06
I use samba to mount the hard drive of the other computer on my network (winxp) directly to my linux box. I mount it with full rights so that I can use whatever files I want. Is this what you want to do?
 
install smbfs from synaptic
 
Edit your /etc/fstab file - add the line below at the end
 
//server/share = your remote computer ip/shared drive
 
/mount/point = where you want to mount the drive in linux. The folder must exist before you can mount to it
 
username and password are the windows username and password with rights to the shared drive.
 
format:
```

 //server/share      /mount/point    smbfs    rw,username=XXX,password=XXX,uid=XXX,gid=XXX 0 0

```
 
Hope this helps

---

### Post by aspangenberg on 2006-02-07
Hi,

I am having a similar problem I think.  I have a second hard drive in my Ubuntu Box that has all of my music and videos on it.  I'm having trouble accessing this drive because it says I am not the owner. Is there a way to make this drive available from startup and listed with my other drives(hda, cdrom, etc) in computer:///  

Ultimately I would like to share this drive over my home network with my iBook, but If I can get the first part configured, I'm pretty sure I know how to share the drive over network.

Thanks....i'm a noob to linux.

---

### Post by Robgould on 2006-02-07
You should find what you need here.....from a post of mine if Fedora forum, but will work the same in Ubuntu.
 
[http://forums.fedoraforum.org/showthread.php?t=63708]("http://forums.fedoraforum.org/showthread.php?t=63708")
 
make sure to read all the way to the bottom....I like to another post there.  You should read it all...You will have a much better understanding when you are done.

---

