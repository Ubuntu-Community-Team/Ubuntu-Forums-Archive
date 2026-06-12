---
title: "Possible to transfer files from windows computer to Ubuntu?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Jhorra on 2007-06-07
I have two computers on a network, but as far as I know windows doesn't see linux drives.  Is it possible to transfer files over my network from one machine to the other?

---

### Post by Seisen on 2007-06-07
You can use Samba to share files is that what you want?

---

### Post by steeleyuk on 2007-06-07
You can use [http://www.fs-driver.org/](http://www.fs-driver.org/) to view EXT2 and EXT3 partitions in Windows if you want to go down that route. If you do decide on the networking you'll need to install Samba on the Ubuntu machine.

---

### Post by Jhorra on 2007-06-07
Well, my real goal here is that I am doing developing, and I have both computers sitting next to each other.  I want to move the files over to the ubuntu machine so I can test them locally.

---

### Post by Seeker84 on 2007-06-07
Well, if you have the wireless network set up you may be able to do it that way.  The other was is using a router.  and the last resort because it take up time is use a crossover cable.  I haven't experimented with the other two, and I've only gone one direction which is ubuntu to windows.

---

### Post by nickpaton on 2007-06-07
I use [this]("http://ubuntuforums.org/showthread.php?t=202605") excellent Samba HOWTO from Stormbringer, and have used it from Dapper days to the present.

Remember to drop your firewall though or else you will not get transfer.  Another HOWTO on configuring your firewall can be found[ here]("http://ubuntuforums.org/showthread.php?t=202605&page=30#298").

---

### Post by Jhorra on 2007-06-07
They are both on my home network.  I'll try installing that program to allow windows to read the drives.  How do I share the drive on my Ubuntu machine though?

---

### Post by mlentink on 2007-06-07
Systen>Administration>Shared Folders
You have to type in your password
select the folder to share (usually your home directory or part thereof) and you're all set

---

### Post by notwen on 2007-06-07
[Hamachi]("https://secure.logmein.com/products/hamachi/") <--- highly recommended. =]

---

### Post by Orochi on 2007-06-07
> **steeleyuk said:**
> You can use [http://www.fs-driver.org/](http://www.fs-driver.org/) to view EXT2 and EXT3 partitions in Windows if you want to go down that route. If you do decide on the networking you'll need to install Samba on the Ubuntu machine.

Does that driver also add ext3 support to Windows? The site only says ext2. If it doesn't add ext3 support, is there another driver that does?

---

### Post by Jhorra on 2007-06-07
I followed the tutorial you linked and set up Samba.  That's exactly what I wanted to do, thanks.

---

### Post by nickpaton on 2007-06-07
> **notwen said:**
> [Hamachi]("https://secure.logmein.com/products/hamachi/") <--- highly recommended. =]

Notwen - thanks for that link - I'll give it a go, but did note that the free version limits you to only 2.5Mb  of files transered on each session (you apparently need to simply reset each session), but that is a nastly little limiting factor for the free one.
Page 6 of the User manual specifies.  On the other hand it's not expensive to buy either.
(EDIT: Not on the Linux version)

@ Jhorroa - itza pleasure!

---

### Post by warcriminal on 2007-06-07
Check out these articles, they show you exactly what to do, step by step;

[http://www.goitexpert.com/entry.cfm?entry=Linux-Share-With-Windows-Vista](http://www.goitexpert.com/entry.cfm?entry=Linux-Share-With-Windows-Vista)

[http://www.goitexpert.com/entry.cfm?entry=Make-Your-Windows-Share-ReadWriteable-From-Linux](http://www.goitexpert.com/entry.cfm?entry=Make-Your-Windows-Share-ReadWriteable-From-Linux)

[http://www.goitexpert.com/entry.cfm?entry=NFS-Mount-File-Systems](http://www.goitexpert.com/entry.cfm?entry=NFS-Mount-File-Systems)

[http://www.goitexpert.com/entry.cfm?entry=Mount-a-Remote-Filesystem-Using-SSH-and-FUSE](http://www.goitexpert.com/entry.cfm?entry=Mount-a-Remote-Filesystem-Using-SSH-and-FUSE)

These explain how to transfer files and mount volumes from ubunto to windows and vice versa.

---

### Post by lazyart on 2007-06-07
I realize this is solved, but note that you never need to install a ext2, ext3 or ntfs driver when transferring files across the network.  This is taken care of by the host OS.

Quick & dirty solution would be to share the files from Windows, then from Ubuntu browse the network and grab what you need.  To share from ubuntu (again, quick and dirty)

Right click the folder, enable samba (SMB) sharing.
terminal:```
sudo smbpasswd -a *username*
sudo smbpasswd -e *username*
```

When you access from Windows side, provide username and pass from ubuntu.

---

