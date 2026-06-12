---
title: "Toshiba Satellite - 1280x960 - Geforce Go 6600"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by dborgill on 2006-06-20
I have some minor Linux experience, lots of Windows experience and tons of hardware experience.  The thing that has really kept me away from Linux is managing file updates, kernels, drivers and all the other pains that come along with Linux.

A friend suggested Ubuntu.  I took his advice, installed it and of course it only displays 1024x768 as my highest resolution.  My native res is 1280x960.  So I went on the mad google search, finally got the Nvidia drivers installed.  Still no other resolutions.  I tweak a few more files mentioned in forums, now, I get white lines on startup.

Am I missing something simple or is it always going to be SUCH A PAIN to get simple tasks done/configured in Linux?

Thanks in advance :confused:

---

### Post by bruce89 on 2006-06-20
```
sudo dpkg-reconfigure xserver-xorg
``` in Applications>Accessories>Terminal should fix it.

---

### Post by dborgill on 2006-06-20
[QUOTE=bruce89]```
sudo dpkg-reconfigure xserver-xorg
``` in Applications>Accessories>Terminal should fix it.[/QUOTE]


I can't even get into X or anything -- It's just a messed up screen now.

---

### Post by Perfect Storm on 2006-06-20
Run in failsafe mode and type in the command.

---

### Post by dborgill on 2006-06-20
[QUOTE=Artificial Intelligence]Run in failsafe mode and type in the command.[/QUOTE]

Sorry to be such a bother... but recovery mode says "Execution failed" and just sits there.

---

### Post by Perfect Storm on 2006-06-20
Did you backed up your xorg.conf file?

---

### Post by dborgill on 2006-06-20
[QUOTE=Artificial Intelligence]Did you backed up your xorg.conf file?[/QUOTE]

No I did not -- I can't get into any mode of Ubuntu now.  Do you think a reinstall will be necessary now.

Also, should the addition of resolutions be fairly simple or is it pretty involved?

---

### Post by Perfect Storm on 2006-06-20
Well, you could go for a reinstall and then take the changing the resolution issue from therr or you could boot your computer up with a live CD.

---

### Post by dborgill on 2006-06-20
[QUOTE=Artificial Intelligence]Well, you could go for a reinstall and then take the changing the resolution issue from therr or you could boot your computer up with a live CD.[/QUOTE]

Ok -- Thanks, will boot off Live CD and fix issue.

Now, after that, what is the best way to go about adding a 1280x960 resolution?  O:)

---

### Post by Perfect Storm on 2006-06-20
First see if you can fix so you can boot up without live CD, next will be running the command above. Normally/with many screen Ubuntu solve the issue by itself but in some cases we've to show it :) (Due to the fact that IT industry doesn't provide drivers for linux except some few.)

---

### Post by tseliot on 2006-06-21
[QUOTE=dborgill]Am I missing something simple or is it always going to be SUCH A PAIN to get simple tasks done/configured in Linux?[/QUOTE]
Read my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

And see point 5 of the Problems Section.

If that doesn't work, try point 10.

Oh, and using the search function of the forum wouldn't hurt too ;)

---

### Post by dborgill on 2006-06-21
[QUOTE=tseliot]Read my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

And see point 5 of the Problems Section.

If that doesn't work, try point 10.

Oh, and using the search function of the forum wouldn't hurt too ;)[/QUOTE]

AWESOME!  Now that my screen looked all mess, some video modes don't work at all on my laptop any more.  Like I am trying to install Windows XP on a partition and the screen just goes black when it enters the setup.  Also, when I boot into Linux and hit the F1 or F2, the screen just goes black like it can't handle certain modes anymore. :(

---

### Post by tseliot on 2006-06-21
[QUOTE=dborgill]AWESOME!  Now that my screen looked all mess, some video modes don't work at all on my laptop any more.  Like I am trying to install Windows XP on a partition and the screen just goes black when it enters the setup.  Also, when I boot into Linux and hit the F1 or F2, the screen just goes black like it can't handle certain modes anymore. :([/QUOTE]
Are you sure that your hardware is ok?

If Windows XP has problems to detect your graphic card your hardware might be broken.

---

### Post by dborgill on 2006-06-22
sudo dpkg-reconfigure xserver-xorg

This command fixed it -- THANK YOU SO MUCH!

---

