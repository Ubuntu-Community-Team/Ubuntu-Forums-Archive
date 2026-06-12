---
title: "Another Xorg problem"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by pelicanghost on 2008-04-12
A little background: When I was using 7.04, I wanted to have some compiz effects, so I installed a program called Envy that automatically retrieved and installed the proprietary drivers.  This worked, then I wanted to update to Hardy Heron beta.  

            This required me to first upgrade to 7.10.  I figured that I would only be in it for so long.  So I updated to Gutsy.  First, it had to run in low-graphics mode, the fan was loud, and apparently the sound card was busy.  I tried to upgrade, but it said I couldn't calculate, as explained in another thread. 

           I needed to uninstall Envy.  I followed the instructions as said on the developers site (google "envy").  Heres where I probably screwed up.  It said I needed to reconfigure the a xorg file.  I know people say to be careful, but his guidelines weren't as specific as they should.  After I did this, it said input was not supported on my monitor.

        I now have no GUI.  Please help me get my GUI back, and update to 8.04 beta.   Noobish territory.  I am now in exile on my Windows partition, playing CoD4

      Thanks in advance.

---

### Post by JoshuaRL on 2008-04-12
From the Recovery Mode try:
```

dpkg-reconfigure -phigh xserver-xorg

```
That should reconfigure xorg and let you get into the desktop.  Then you can upgrade all you need.

What type of card do you have?

---

### Post by gn2 on 2008-04-12
If ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` doesn't work, then try ```
sudo dpkg-reconfigure xserver-xorg
``` and at the section to select video driver, select vesa.

If the vesa driver doesn't work chances are nothing will.

Once you get up and running with vesa you can use the GUI Restricted Driver Manager to install a better driver.

---

### Post by pelicanghost on 2008-04-12
> **JoshuaRL said:**
> From the Recovery Mode try:
```

dpkg-reconfigure -phigh xserver-xorg

```
That should reconfigure xorg and let you get into the desktop.  Then you can upgrade all you need.

What type of card do you have?

I have Nvidia Geforce 8600. Thank you.

---

### Post by JoshuaRL on 2008-04-12
Alright, no problem.  I would suggest you install the Nvidia driver directly instead of using Envy.  Envy is definitely easy, but it can have the exact problems you have had.  I'll post a 5 step howto I posted before.  It presupposes you went to the Nvidia site and downloaded the driver installer to your desktop.  Here it is:
> 
**Five Steps to Nvidia Driver Install!**

1).  Reboot the computer and choose Recovery Mode from the GRUB menu.

2).  Move into the Desktop:
```

cd /home/username/Desktop

```
The capitol "D" is important, and "username" is the name of the user that has the file in their desktop.

3).  Find the name of the installer file:
```

ls

```
That's a lowercase L, not a 1.  The file that you downloaded to the Desktop will show up here.  When you use that name in the steps below, make sure you type it exactly.  I'll be using "nvidiainstallerfile.run" as the fake name.

4).  Change permission level of the installer file so it has internet access, and change to runtime level 3:
```

chmod +x nvidiainstallerfile.run
init 3

```

5).  Run the installer file in a shell:
```

sh nvidiainstallerfile.run

```
Go through all the options, picking the defaults unless you KNOW you need something else.  After that's done, you reboot the computer and the driver should be installed.

Congratulations!


---

### Post by pelicanghost on 2008-04-12
That would be a great guide if I downloaded the driver from the site, however, I do believe I have no driver at my disposal.  I think that the dpkg is my best bet, even though the last time I went through that process, I rebooted and had a kernel panic.

---

### Post by JoshuaRL on 2008-04-12
Okay, thats fine.  If you have another computer with internet access you can download the installer and put it either on a CD-R or a thumbdrive.  Or you can use the thumbdrive and a Live CD to get the installer too.

If you do that, both the CD drive and the USB drive are located in /media.  Use the "ls" command to make sure you're moving into and using the right directory.

---

### Post by pelicanghost on 2008-04-12
It says 'x+' not valid

Try chmod --help.

---

### Post by JoshuaRL on 2008-04-12
I am so sorry, it's supposed to be:
```

chmod +x

```

---

