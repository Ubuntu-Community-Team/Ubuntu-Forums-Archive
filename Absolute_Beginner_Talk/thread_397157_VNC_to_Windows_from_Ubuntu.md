---
title: "VNC to Windows from Ubuntu"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by halohunter on 2007-03-30
Hey everyone,

I'm getting my grip on Ubuntu now. Thanks to this great community and many hours of learning and exploring.

A few unanswered goals remain though:

1. How can I remote desktop to a windows machine through the internet from Ubuntu? When I was still using Windows XP, I used hamachi and UltraVNC. 

2. Ubuntu recognises my mini external harddrive but I cannot write to it. It is a NTFS drive, so I looked through some guides on how to get write support working. Unfortunatly I did not succeed. Step by step instructions will be great!

3. Some time ago, I remember seeing this cool app for linux. It allowed for the terminal to drop down from the top of the screen like in a game using the TAB button. Does anyone still remember what this was/is?

Thanks for your time!

---

### Post by Flying George on 2007-03-30
1. I'm not entirely certain, I'm not firmilear with that software, sorry.

2. Usually you cannot write to these drives (I could be wrong) because they are recognized as Windows drives. For instance, if you partitioned a small peice of your drive as FAT32, you should be able to write to it, and Windows, and Linux alike would be able to see it. However, the NTFS is recognized as Windows, and you are not allowed to modify it as a default. And Windows knows your Linux drives are there, however it does not recognize the EXT3 format, and because Windows wants to be the only operating system, it will not access it.

3. Hmmm, Do you mean, you can use the tab button to open your menus while in a game? I'm not sure what you're trying to get at here. 

Well, hope it helps. 

-Gene

---

### Post by undertherift on 2007-03-30
As far as writing to NTFS drives, do a quick search for NTFS-3g.  I haven't tried it yet, but it was recently released write support for NTFS.  I don't know how stable it is, so careful if you have sensitive information.

Not much help, but i hope that points you in the right direction.

---

### Post by undertherift on 2007-03-30
As far as VNC goes, you can use RealVNC from a windows box. They hvae a free app which allows you to do what you  need.
Check out this guide - it'll help you with almost all your problems. 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Remote_Desktop_Sharing.2FDuplication_via_VNC](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Remote_Desktop_Sharing.2FDuplication_via_VNC)

Enjoy!

---

### Post by halohunter on 2007-03-30
> **undertherift said:**
> As far as VNC goes, you can use RealVNC from a windows box. They hvae a free app which allows you to do what you  need.
Check out this guide - it'll help you with almost all your problems. 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Remote_Desktop_Sharing.2FDuplication_via_VNC](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Remote_Desktop_Sharing.2FDuplication_via_VNC)

Enjoy!

You see, that guide does not tell me how I can access my Windows XP machine from Ubuntu. Thats what Im trying to do.

---

### Post by SendDerek on 2007-03-30
1.  The "Terminal Services" included in the install (Applications->Internet) should do the trick.  Be sure to select "VNC" protocol and type in the IP address of your windows box.  I do this all the time with my Ubuntu to Windows XP setup.  As always, just be sure the VNC Server is running on your Windows box.

2.  Have you tried NTFS the easy way?  
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

3.  The terminal drop down that you're talking about is called:

kuake:
[http://www.nemohackers.org/kuake.php](http://www.nemohackers.org/kuake.php)

yakuake
[http://yakuake.uv.ro/](http://yakuake.uv.ro/)

tilda
[http://tilda.sourceforge.net/wiki/index.php/Main_Page](http://tilda.sourceforge.net/wiki/index.php/Main_Page)

---

### Post by cfgtech on 2007-03-30
I'm able to access machines from Ubuntu to Windows thru VNC via LAN
I have not tried thru the web however...I did it before using Ubuntu's built in RDP v5
Terminal Client listed under Programs/Internet in there and I used no-ip.com to set up
the other system.I don't see why that would not work the same way using VNC

If you are not familiar you can read some good tutorials found at no-ip.com
they tell you how to set up the host and router n everything.

---

### Post by SendDerek on 2007-03-30
> **cfgtech said:**
> I'm able to access machines from Ubuntu to Windows thru VNC via LAN
I have not tried thru the web however...I did it before using Ubuntu's built in RDP v5
Terminal Client listed under Programs/Internet in there and I used no-ip.com to set up
the other system.I don't see why that would not work the same way using VNC

If you are not familiar you can read some good tutorials found at no-ip.com
they tell you how to set up the host and router n everything.

I would also like to say that there is another service called dyndns.org.  I've tried no-ip before without much luck.  dyndns.org is actually supported by most routers so there's no additional software to install on your pc like no-ip.

Just a suggestion.

---

