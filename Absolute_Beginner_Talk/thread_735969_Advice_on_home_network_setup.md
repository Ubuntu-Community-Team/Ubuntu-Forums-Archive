---
title: "Advice on home network setup"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Kallekula77 on 2008-03-26
Hello everyone!

I'm really new to Ubuntu and Linux so I would like some advice on my plans for my home network.

My current setup is like this.
[LIST]
[*]File and webserver running Win2003 (Also used for torrents)
[*]HTPC Running vista ultimate (No TV signal connected since I've not found a sloution for IPTV)
[*]Workstation/Gaming PC running VISTA
[*]Laptop running UBUNTU 7.10
[/LIST]

**In general;**
Is there a way to check if your hardware is supported by Ubuntu?

**For the server;**
Is it easy/possible to setup filesharing and "Remote desktop" that can be accessed from both Vista and Ubuntu?
At this time the server has one HD with two partitions (NTFS), is it possible to install Ubuntu on one and then access the files on the other? 
I think I got the webserver part covered.


**For the HTPC;**
Streaming video/music and watching photos stored on the server. 
Do you know if there are any solutions for HTPC/IPTV in progress? 
I've read about MythTV but are there any alternatives since I (for the time being) won't be using it to watch TV?. 

**For the workstation;**
I might set it up with dual boot later but for now I'll leave it.

I fear that this might be a bit much as a "beginner project" but what the hell, this seems to be a helpful forum :)

Any advice or input is greatly appreciated!

Regards
Kallekula77

---

### Post by pedro_orange on 2008-03-26
> In general;
Is there a way to check if your hardware is supported by Ubuntu?

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

> For the server;
Is it easy/possible to setup filesharing and "Remote desktop" that can be accessed from both Vista and Ubuntu?
At this time the server has one HD with two partitions (NTFS), is it possible to install Ubuntu on one and then access the files on the other? 
I think I got the webserver part covered.

Yes you can setup a home fileserver with Linux that can be accessed from both machines. Yes you can install Ubuntu on NTFS, and it can read NTFS.

Heres a small guide to the home server setup, but there are loads out there if you google it.

[http://howtoforge.com/ubuntu-home-fileserver](http://howtoforge.com/ubuntu-home-fileserver)

> For the workstation;
I might set it up with dual boot later but for now I'll leave it.

Dual booting is a piece of cake if you already have Windows on there. There are a million and one guides out there on how to Dual Boot.

Good luck sir

---

### Post by Kallekula77 on 2008-03-26
> **pedro_orange said:**
> 
Yes you can setup a home fileserver with Linux that can be accessed from both machines. Yes you can install Ubuntu on NTFS, and it can read NTFS.

Heres a small guide to the home server setup, but there are loads out there if you google it.

[http://howtoforge.com/ubuntu-home-fileserver](http://howtoforge.com/ubuntu-home-fileserver)


Thanks for your reply!

I read the guide and it seemed easy enough. 
It does however suggest using 2 HDs, one for the system and one for the shared media. 
Will the Server setup recognize the partitions made by windows and let me install everything on "C:\" leaving "D:\" intact?

Regards
Kallekula

---

### Post by hyper_ch on 2008-03-26
for checking hardware compatibility: Download the DesktopCD and run it... if it runs without problems then you should be fine. If you encounter problems you may need to inquire more.

---

### Post by hyper_ch on 2008-03-26
> **Kallekula77 said:**
> Will the Server setup recognize the partitions made by windows and let me install everything on "C:\" leaving "D:\" intact?

You can install to other partitions. I don't really see why there should be two harddisks invovled in that howto.... I wouldn't used windows ntfs harddisks... they can be supported but it's not a native linux filesystem format...

---

### Post by Kallekula77 on 2008-03-26
> **hyper_ch said:**
> for checking hardware compatibility: Download the DesktopCD and run it... if it runs without problems then you should be fine. If you encounter problems you may need to inquire more.

Thanks, that sounds like a good start!

> **hyper_ch said:**
> 
You can install to other partitions. I don't really see why there should be two harddisks invovled in that howto.... I wouldn't used windows ntfs harddisks... they can be supported but it's not a native linux filesystem format... 

With the risk of making myself look even more stupid than necessary :) does this mean that I can install Ubuntu on c:\ and the media library on d:\ will not be affected?

/Kallekula77

---

### Post by pedro_orange on 2008-03-26
> With the risk of making myself look even more stupid than necessary  does this mean that I can install Ubuntu on c:\ and the media library on d:\ will not be affected?

Disk names like C: & D: are Windows conventions.

You can certainly have Linux on one partiton and have files on the other partition on the same physical disk. All you need to do is mount the partition & you're laughing. 

If the files are already on "D" and are partitioned away from the OS, then formatting the "C" Partition will not affect the files on "D"

---

### Post by hyper_ch on 2008-03-26
here a quick read on partitions and stuff:  [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Kallekula77 on 2008-03-26
Thanks alot, I will read up some before asking more stupid questions :) 

/Kallekula77

---

### Post by Kallekula77 on 2008-03-27
Good morning people!

I got started with my project yesterday and istalled the 7.10 server. I did however chicken out and installed it as a dual boot keeping win2003 as well :) I also kept my Media library as NTFS

The webserver is up and running and I hope that I will be able to set up Squeezecenter for my Squeezebox.

I ran into some problems with the installation since my user was "not in the Sudoers file", I have no clue why this happened...

This was missing in the etc/sudoers file:
```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

And this was missing in the etc/group file:
```
admin:x:106:Username
```

I found the solution on [http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/") that has so far been able to answer all my questions :)

This I hope to set up tonight:
[LIST]
[*]File sharing, failing that mean no "Bob the builder" for my son and then there will be hell to pay :mad:
[*]lNTS3G, any options here?
[*]Remote Desktop, so that I can put the computer back into the closet :)
[*][http://www.no-ip.com/]("http://www.no-ip.com/") any opinions on using it with Ubuntu?
[/LIST]

I'm sure most of you would set this up in your sleep, but it's hard for me ok! :)

/Kallekula77

---

### Post by hyper_ch on 2008-03-27
no-ip is simple, install the noip2 client, enter your credentials, set the update interval... that's it... :)

not sure what you mean by file sharing or INTS3G

---

### Post by Kallekula77 on 2008-03-27
> **hyper_ch said:**
> 
not sure what you mean by file sharing or INTS3G


It was supposed to say "NTFS-3G", for read and write access to my media library on NTFS.
The file sharing part is simply giving access to the Media library to the other computers on my network.

/Kallekula77

---

### Post by Kallekula77 on 2008-03-28
Hello again!

Made some progress yesterday, so far this has been easier than I thought it would be... but then again I've followed guides mostly :)

**So far this is now done:**
[LIST]
[*]Dual boot installation
[*]Gnome desktop installation, how do I get back to console mode, i.e shut down the GUI?
[*]Mounted the media library and set up NTFS-3G for write access.
[*]Installed NO-IP
[*]Enabled Remote Desktop
[*]Enabled SSH
[*]File sharing using SAMBA, in smb.conf, what does "Force group", is that a windows group? I've disabled it for now and it works fine.
[*]SqueezeCenter installed for my Squeezebox.

Today I will try to move my webpages to this machine, so tonight I suppose it's time to look closer at Apache, MySQL and PHP settings.

Regards 
Kallekula77



[/LIST]

---

