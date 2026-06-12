---
title: "Can I use a Ubuntu boot disk to install drivers to Windows?"
date: 2012-09-26
forum: Any Other OS
---

### Post by Abstker on 2012-09-26
I work at a computer repair shop, and we recently received a computer  that requires network drivers, but won't let us log into the user  account until the OS has been activated online, but we can't activate the OS until we've installed the drivers. See the problem? We can't seem to find any way  to install the drivers, so I thought of booting into Ubuntu, using a USB. Is there a way to install a driver to Windows through  the Ubuntu boot?

---

### Post by uRock on 2012-09-27
Use ubuntu to back up any data, then use one of your install images and the product key, which should be on a sticker on the machine, then reimage the system. If you don't partition the system, then you can use USMT to get user data and such from the Windows.Old directory. [http://technet.microsoft.com/en-us/library/dd939980%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/dd939980%28v=ws.10%29.aspx)

Feel free to ask more about using Ubuntu to accomplish this task, but please refer all questions about USMT and such via Microsoft's forums and documentation.

Since this thread is being used to seek help with repairing Windows, I have moved it to ***Other OS/Distro Talk***.

---

### Post by Abstker on 2012-09-27
So is that a no? Because we can just clone the disk, reformat the old one, then transfer the data back on, but I'd really rather avoid that, because then we have to have a tech sit there and sort through all the data, is there just a way I can install the one driver and be done with it? Would VirtualBox let me run Windows on Ubuntu? I just really need to use Ubuntu's network drivers, to activate Windows.

---

### Post by Rexilion on 2012-09-27
Why not use a network card that Windows can handle 'out of the box' and then activate?

---

### Post by deadflowr on 2012-09-27
Phone it in.

[http://windows.microsoft.com/en-US/windows7/activate-windows-7-on-this-computer]("http://windows.microsoft.com/en-US/windows7/activate-windows-7-on-this-computer")

So long as it's a legit activation, you can always use the telephone method to activate it.

This method has been is use for all windows with activation requirements.

---

### Post by Habitual on 2012-09-27
> **Abstker said:**
> ...but won't let us log into the user  account until the OS has been activated online

Phone it in is the best advice. It's automated and very mechanical. 
Alternative, boot to command prompt and [URL="http://superuser.com/questions/420183/what-happens-after-the-trial-period-of-windows-has-expired"]run "slmgr -rearm" (no quotes)
This will extend the trial license for 1 month[/URL]. You can do this three times.
I have not tried or experienced this as I don't use Windows anymore. 

Can you login as Administrator and 
Do you have the ProductKey available?
Can you boot "safe mode" and login to install the driver(s)?
What exact Windows version are you dealing with?

[http://support.microsoft.com/kb/925582](http://support.microsoft.com/kb/925582) may help.

---

