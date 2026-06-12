---
title: "Best OS for a server?"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by jamieh on 2007-09-11
I have a computer that I want to use as a file and print server, should I use Windows Server or Ubuntu Server? I know the people on the forums say that Ubuntu is better for a server, but I recently came across Microsoft's "Get The Facts" page, is all that stuff true about Windows Server being more stable, or is Microsoft just trying to embarrass themselves?

This is what I want to be able to do:

- Access files stored on several  HDDs from two Windows PCs on the same network
- Be able to print to a Canon PIXMA iP8500 and an HP LaserJet 1020 from the two Windows PCs
- Be able to scan stuff from a Canon CanoScan Lide 70 from the two Windows PCs

Thanks for any help.

---

### Post by BrendanM on 2007-09-11
Ubuntu server is free. Windows server costs $$$. If you're just setting up the home network, I'd try Ubuntu and see how you like it.

---

### Post by sumguy231 on 2007-09-11
An Ubuntu system generally makes a really great server, especially given the flexibility you get. As for "Get the facts", I wouldn't say that everything Microsoft says is a lie, but most of it is. Microsoft is hardly an unbiased source. I'm not a very unbiased source either. It's free, the best thing to do is try it out and see if it fits your needs.

You should be able to do the first two things, it's just the third thing that I'm not so sure about. Your actual experience may vary, you might want to use Google to find out what experiences other people have had with that specific hardware.

---

### Post by BrendanM on 2007-09-11
Also, don't just install Ubuntu server edition. It's command line only, and will be tricky to learn. You should install Ubuntu desktop and then add the server components. That will be much easier.

---

### Post by stmiller on 2007-09-11
Well, a server is nothing more than a dedicated computer running all the time. You can do what you want with an old Windows XP machine. No need to purchase microsoft server, which costs quite a bit.

Or if you are comfortable with Ubuntu, then use Ubuntu as a server. Any Linux distro will work. First check the support status of your scanner and printer in Linux. If they connect USB, chances are you can just plug them in and they will work.

You can configure the server to run samba, and it will show up as a network drive for OS X, Windows, or Linux users. Samba can get confusing, but there are interfaces like samba SWAT and so forth to make it easier to set up.

For just a file and print server, Linux is perfect for the job. (And free of course!)

---

### Post by Lee Davies on 2007-09-12
*Ubuntu Server* would be the easiest server distro to get to grips with, be that a normal install of *Ubuntu Server* or a normal install of *ubuntu* with the server packages added later.

FreeBSD would be more of a challenge, but why else would they have the "power to server" motto? ;)

---

### Post by hyper_ch on 2007-09-12
as a server I would give my vote to Debian Etch or maybe FreeBSD

---

### Post by Marc Hoffman on 2007-09-12
I read a write up in Micromart that used NASLite to create a small office server. It is small enough to run from a usb key or a flash card. Is not a full OS but has all the functionality to run a range of protocols.

quoted from [http://www.serverelements.com/](http://www.serverelements.com/)
- transforms a basic computer into a dedicated SMB/CIFS, NFS, AFP, FTP, HTTP and RSYNC file server. NASLite-2 USB supports IDE, SATA, SCSI, USB and FireWire connected fixed disk drives as well as hardware RAID.

---

### Post by AndyCooll on 2007-09-12
Since all you want to do is set up a print and file server then a normal Ubuntu setup will do that nicely. You'd just need to add a couple of such as nfs (for sharing with Linux), Samba (for sharing with Windows) machines, and maybe ssh. You can then add other elements later as you learn or try extra things. 

This is exactly what I've always used my server for, it's fairly straightforward to setup, and works a treat.  
Anything else is overkill.

As already mentioned above the Microsoft "Get The Facts" campaign was pure FUD, and indeed has been withdrawn by Microsoft as they couldn't prove most of it. So I would treat what they say with a strong dose of salt!

:cool:

---

### Post by atria on 2007-09-12
- Access files stored on several HDDs from two Windows PCs on the same network

Samba works fine in this case. Though you'll need to spend some time configuring it if you haven't done it before.

- Be able to print to a Canon PIXMA iP8500 and an HP LaserJet 1020 from the two Windows PCs

I'm not sure if the camera is supported but the printer should work fine. Samba will need to be installed and configured to share the printers.

- Be able to scan stuff from a Canon CanoScan Lide 70 from the two Windows PCs

Again i'm not sure if the scanner works, but to my experience there should be plenty of support for scanners (even my obscure plustek is supported). You should really check it out through google though.


In all honesty, if you already have a copy of windows server then just use it. For a server of such a small scale, performance should be the least of your concerns. I'm pretty sure you will be able to get everything running in a far shorter time than you would with ubuntu.

---

### Post by jamieh on 2007-09-13
> if you already have a copy of windows server

I have a really old copy of Windows NT Server 4.0 that I don't think I ever used, and becuase of its age, it is most likely useless. And I have a copy of Windows Vista Ultimate that is already activated on another computer, so would also be useless, but I do have Ubuntu 7.04 desktop edition and Fedora 7, which I never really warmed up to.

---

