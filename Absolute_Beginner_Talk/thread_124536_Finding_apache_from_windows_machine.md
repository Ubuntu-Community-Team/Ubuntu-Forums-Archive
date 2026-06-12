---
title: "Finding apache from windows machine"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by procogo on 2006-02-01
Hello:

I installed Ubunto Desktop, with Apache 2.0 for use as a testing web server.  Now, I need to find it from my Windows machine where I run Dream Weaver.  

I've never used linux, apache, or a local web-server so I don't really know where to start.

I've installed Ubunto, and I think I have apache installed.  The computer is attached to the network but I don't know what's next.

Details of my system:
[LIST]
Windows Small Bussiness Server 2003 set up as DHCP server.  
Linksys router (dhcp turned off)
My web development machine is a workstation on this network running Windows XP pro.
I have Ubunto installed on a separate computer connected to the network.
[/LIST]

Thanks,

Dale

---

### Post by DonQuixote on 2006-02-01
You can view your pages by pointing your browser to your Ubuntu machine, however, to create and edit files on your Ubuntu machine from your Windows machine, you would most likely need to enable it as an FTP server, as well.

---

### Post by procogo on 2006-02-01
Thanks John:

Umm.... how do I get the Ubunto machine to be seen on the Windows network?

Dale

---

### Post by DonQuixote on 2006-02-01
Can you not see the default apache page when you point your browser to it?

If you are talking about sharing files, it's my understanding that there are a few options.

1) If you are using DreamWeaver to FTP your created/edited files to your web server (Ubuntu) then enabling FTP on your web server would do the trick.
2) If you want to look at the directory through Windows Explorer, you would need to enable samba sharing.

I'm not to savvy on either account, but do know that there are at least those two ways of doing it.

---

### Post by johnswb on 2008-06-21
Did this work ?

---

