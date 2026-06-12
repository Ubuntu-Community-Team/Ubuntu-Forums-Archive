---
title: "First Impressions of PC-BSD 1.5 (Da Vinci)"
date: 2008-04-16
forum: BSD
---

### Post by ramjet_1953 on 2008-04-16
Hi, Guys!

I had some spare time, so I downloaded the latest version of PC-BSD and then installed it on a spare hard drive.

I must admit, the installer is one of the slickest and most professional that I have seen.

My hardware is an Acer TravelMate 4101 Laptop and everything worked straight-up, with the exception of it not recognizing my on-board WinModem. I couldn't really care about this, as I have ADSL. 

One thing that was impressive for me is that the switch for my wireless was enabled automatically. Under Ubuntu, I have to create a file in /etc/modprobe.d/ipw2200 and put the line in the file options ipw2200 led=1 to be able to turn my wireless card on.

The PBI packaging system is really great. Much like a WIndows install exe. Unfortunately, there are only a limited number of packages currently available. However, when this improves, it will be a "killer" app for PC-BSD.

One thing that I can't understand is that they do not include a GUI for ports. Neither is there one available in the ports tree, or in the PBI list. I did managed to get KPorts from the net and download it and fortunately, it worked OK. I know that downloading software with the command line is easy, but KPorts makes searching for and seeing what files are loaded and where, much easier.

Although HPLIP is included with this version, I could not get hp-setup, or hp-toolbox to work. They just refused o see my HP psc 1350 all-in-one. It may be that I needed to un-install gutenprint. However, seeing that the printer is detected and installed at installation, I would have thought that HPLIP would have been enabled. The printer worked fine, but XSane did not see the scanner. I did not have the time to persist with this, but I'm sure that googling and by posting on the forum would have secured a fix. 

The installer recognized my Intel graphics chipset and I just entered my 1280 X 800 resolution and told it to enable 3D acceleration.

When I booted up I had the option to enable Compiz. It worked straight up and placed an icon on the task bar, very much like Beryl used to. I don't know why Ubuntu don't have this. I know that you can install the GNOME Compiz taskbar icon, but this does not have anywhere near the options available with the Compiz icon.

One thing that I did find interesting is that PC-BSD cannot display the files on a iso disk. It can mount the disk, but when you have a look at it with Konqueror, nothing is listed.

Another thing that I found annoying is that as BSD uses the UFS file system, you cannot mound a UFS disk under Linux. I must admit, that I did not pursue this and there may be utilities available, or a command line procedure to mount a UFS partition.

In closing, I must admit that PC-BSD is a pretty impressive package, that in my opinion, is worth keeping an eye on.

Would I consider changing over? Not at this stage, as there are still things that need to be done to bring it up to the standard of Ubuntu. One glaring problem is with restricted codecs. There is no longer any PBI, or port listing that allows you to install a meta package for codecs.

Regards,
Roger :cool:

---

### Post by Bachstelze on 2008-04-17
> **ramjet_1953 said:**
> 
Another thing that I found annoying is that as BSD uses the UFS file system, you cannot mound a UFS disk under Linux. I must admit, that I did not pursue this and there may be utilities available, or a command line procedure to mount a UFS partition.

Linux does have (read only) support for UFS filesystems, not sure whether you're interested in that now but feel free to ask if you are.

---

