---
title: "Run Ubuntu without admin rights?"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by rodinia on 2007-10-03
I'm an absolute Linux beginner, so my question might probably sound rather stupid. 

At work I want to test a new scanner but for some complicated reasons it's not possible for me to get a local admin login (under Win2000) and so I cannot install the driver ](*,)
I read in a newspaper article that it's possible to run Ubunto from a CDRom. Is it still possible to install software then, and will this information be written on harddisc sectors that I am able to access? Drivers seem to be available for Linux, so that's no problem. And which version should I download anyway, the 1 year support or 3 year support version? I'm also happy for any other sollution to my problem :)

Thanks a lot,
Rod.

---

### Post by funpop on 2007-10-03
i would recommend you to use feisty fawn ("1 year support") or even the gutsy gibbon beta version.
hardware supports should be better each release. 

and yes you can install software when you use the live-cd. dont ask me where it's stored, or what the limitations are. (maybe in the ram :confused: )

just give it a try, if you encounter problems with your scanner im sure there are some people around here to help you making it work :)

---

### Post by mattmole on 2007-10-03
Hi,

When you install things on Ubuntu when running from the liveCD, the changes are stored in RAM. They are therefore lost when you restart.

The only thing you could do is to use the liveCD in persist mode, this means changes can be saved to a memory stick.

[https://help.ubuntu.com/community/LiveCDPersistence](https://help.ubuntu.com/community/LiveCDPersistence)

Note, this requires wiping your memory stick, or it does describe how to use a file on the HDD to store the persist options.

Also, only Dapper and Edgy are working in persist mode.

mattmole

---

### Post by rodinia on 2007-10-03
OK, I'm off downloading. I really hope this is a way for installing hardware on my computer. It's so annoying to work on a computer without admin rights. So lets hope drivers are stored somewhere I can access. Just one more question: Where can I store the drivers in order to access them for installation? My computer only has one CDRom drive. Can I just dump them on my C-drive  (not all of it is blocked from me) under windows and access it under Linux or use a (new) USB stick without drivers?

Rod.

---

### Post by rodinia on 2007-10-03
> **mattmole said:**
> Hi,

When you install things on Ubuntu when running from the liveCD, the changes are stored in RAM. They are therefore lost when you restart.

The only thing you could do is to use the liveCD in persist mode, this means changes can be saved to a memory stick.

[https://help.ubuntu.com/community/LiveCDPersistence](https://help.ubuntu.com/community/LiveCDPersistence)

Note, this requires wiping your memory stick, or it does describe how to use a file on the HDD to store the persist options.

Also, only Dapper and Edgy are working in persist mode.

mattmole

Ah, one more question already solved :) I should have taken an additional USB stick along then, one I can wipe without problems. Ob the other hand, storing installation data in  RAM is no problem unless I have to rebook when installing and connecting. I just want to test if the scanner is useful and then buy it, or not.

Ehm.. it's no problem to save the scans in a good resolution format and use them on Windows as well, is it? (argh, almost feeling stupid aslking all this)

Rod.

---

### Post by mattmole on 2007-10-03
Hi Rod,

Ubuntu does not use drivers in the windows sense. Most supported hardware will just work! You should not need to download drivers for the scanner. What make and model is it? CHeck it out on the following website:

[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

Just for your knowledge. As far as I remmeber the livedisk will mount your windows partitions automatically, so you could access stuff on the windows partition. NOTE, If your windows partition is NTFS then it will be mounted readonly as standard. It is possible to mount as read write, but, not automatically.

Finally, just reboot your computer while booting from the livedisk, Applications->Graphics->Xsane Image Scanner and it should recognise the scanner.

mattmole

---

### Post by rodinia on 2007-10-03
> **mattmole said:**
> Hi Rod,

Ubuntu does not use drivers in the windows sense. Most supported hardware will just work! You should not need to download drivers for the scanner. What make and model is it? CHeck it out on the following website:

[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

Just for your knowledge. As far as I remmeber the livedisk will mount your windows partitions automatically, so you could access stuff on the windows partition. NOTE, If your windows partition is NTFS then it will be mounted readonly as standard. It is possible to mount as read write, but, not automatically.

Finally, just reboot your computer while booting from the livedisk, Applications->Graphics->Xsane Image Scanner and it should recognise the scanner.

mattmole

Argh, my scanner is not on that sane list. It's an Epson Perfection 750 Pro. I guess I'm slowly going insane. Still I just try to connect it and see what happens.

Rod.

---

### Post by mattmole on 2007-10-03
Hi again,

I use an Epson Perfection 1260 and that works perfectly. This is on the list, but as you say try it anyway!

mattmole

---

### Post by rodinia on 2007-10-03
OK, quick reply: project delayed until tomorrow *sigh*
the company CD writer doesn't do images, and all others I tried either try to install files where I don't have access to, or don't recognise the CD writer.

---

