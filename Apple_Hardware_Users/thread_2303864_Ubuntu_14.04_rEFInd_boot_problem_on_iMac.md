---
title: "Ubuntu 14.04 rEFInd boot problem on iMac"
date: 2015-11-22
forum: Apple Hardware Users
---

### Post by JSmith1234 on 2015-11-22
Hi all

I have an iMac (purchased in April 2010) on which I run Mac OSX 1.6.8

Last year I installed Ubuntu 14.04 and also the rEFInd boot loader

For some time now I haven't been able to boot into my Ubuntu partition - I don't recall how exactly it happened, it may have been due to an accidental termination during a package update

Anyway, I set out to recover the problem (and all my files stored on the Ubuntu partition) and found various websites that provide solutions.

First, I burned the Boot Disk Repair tool (32 bit) to a DVD and tried to boot from it. It actually worked, but when trying to run the actua; repair tool, I get this:

"The current session is in Legacy mode. Please reboot the computer, and use this software in an EFI session. This will enable this feature. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd](www.sourceforge.net/p/boot-repair-cd)), after making sure your BIOS is set up to boot USB in EFI mode. "

Then, I created a 64 bit USB device with the tool, but this USB device does not show up in my rEFInd boot loader.

Right now, I have been able to load a Ubuntu live session using my 14.04 installation DVD, and I can also see my Ubuntu partition in the file manager. I can even see my folders, but when clicking through to some of my files I get the error: 

"This location could not be displayed. You do not have the permissions necessary to view the contents of “2013”."

It is very strange, because I am able to browse and see some of the files, but some folders throw this error.

The question is: how can make my boot USB (created using the approach documented @ [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) show up in rEFInd and use the repair tool? Or, how can I change permissions to access my files?

Thanks for any help or ideas

J

---

### Post by luciano.x on 2015-11-25
I'm not sure if boot repair is the right tool for the job.
Anyways, check the folders permissions to be sure it is a permission error and open nautilus as root using the live installation dvd to backup your files or whatever.
```

sudo nautilus

```

Now still in the live session search for your boot log /var/log/dmesg 
If your problem is there, it should give us a clue. Paste its contents at [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

