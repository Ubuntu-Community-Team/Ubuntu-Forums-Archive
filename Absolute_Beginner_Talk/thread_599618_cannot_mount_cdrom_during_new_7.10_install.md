---
title: "cannot mount cdrom during new 7.10 install"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by adlerschrei on 2007-11-01
Trying a new install of ubuntu 7.10 server. After picking keyboard configuration the cdrom cannot be mounted and the installation aborts.

Also tried the regular ubuntu and xubuntu 7.10 install CD - same problem. CD drive works fine under XP and used to run Fedora on the same machine without problem. Checked that CD is configured correctly as secondary master.

The terminal window ls command from the install menu finds a /dev/scd0 .

The computer is an ancient HP Celeron that I am planning to use as file server [Model HP Pavilion 6642F]. CDRW drive is a Sony .

Any help is highly appreciated.

---

### Post by oskar2000 on 2007-11-02
If you can start the from the live/install cd - it is already mounted so the problem seems to be elsewhere. 
You can take a look in /etc/mtab to see whether or not it is still mounted:
$ cat /etc/mtab | grep cd

If it really isn't mounted anymore (no output when you typed the previous command) you can try to do it manually by going inside the Terminal (Applications - Accessories - Gnome-Terminal) and typing 
$ sudo mount /dev/scd0 /media/cdrom
If this gives you an error, I'd be suprised.

Alternatively you can use the 'alternate install' cd, which is probably a better idea to use with an old pc anyway since it doesn't boot into a live system. It's the same thing only with a minimal installer which should be less prone to errors.

---

### Post by adlerschrei on 2007-11-02
Thanks for the quick response. Still have the same problems with alternate install CD.

$ cat /etc/mtab | grep cd    returns nothing, just a new prompt.

Mounting with $ sudo mount /dev/scd0 /media/cdrom returns " .... failed: No such file or directory"

I still see /dev/scd0 though.

What I did not mention: I also receive a 
[    0.000000] no DMI bios year, ACPI=force is required to enable ACPI
My understanding is that this is for power features only and the installation kept going. I did not think this is related. Not sure now.

What I did notice today is that there is another error message [with all install CDs]:

[101.588703] ata2.00: exception Emask 0x0 SAct 0x0 SeErr 0x0 action 0x2 frozen 
[101.588802] ata.2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0  tag 0cdb 0x5a data 128 in

These two lines are repeated 3 times with different numbers in the [] until it continues with something like

Starting .... daemon: syslog...

[Sorry, I m copying from the screen. So the last line is incomplete]

I also changed the settings for the cd RW drive in the BIOS to the absolute basics - no difference.

Thanks again!

FYI: I run ubuntu 7.10 on my Dell D600 laptop and it works really well. Simply amazing!

---

### Post by adlerschrei on 2007-11-02
Also tried a Fedora live CD but get the same error messages.

---

### Post by oskar2000 on 2007-11-08
> **adlerschrei said:**
> Thanks for the quick response. Still have the same problems with alternate install CD.

$ cat /etc/mtab | grep cd    returns nothing, just a new prompt.

Mounting with $ sudo mount /dev/scd0 /media/cdrom returns " .... failed: No such file or directory"

You would need to create the directory /media/cdrom... but anyways - if the cd unmounts during installation you got a problem that probably won't be solved by just remounting it.


 - So the alternate install-cd doesn't work at all?

If no one comes up with a solution I would suggest you simply try another distro. They're all more or less the same.
Fedora is quite nice, and their new release is scheduled for tomorrow. Codename Werewolf - how cool is that!

---edit--- 
just realized you already tried fedora.
Well, there are ways of skipping the cd drive altogether. I've never done that, but you should find plenty tutorials. I think it involves some kind of boot disk/usb-drive and the iso mounted as loopback. How exactly, I can't tell you.

---

