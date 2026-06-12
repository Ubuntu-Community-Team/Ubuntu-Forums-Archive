---
title: "Install on MacBook Pro fails - wrong screen resolution etc."
date: 2007-12-17
forum: Apple Intel Users
---

### Post by john.wheeler on 2007-12-17
I've just bought a new MBP (2.2 GHz, 15 inch screen) and have tried to install Ubuntu into a Boot Camp partition. 

Unfortunately, the installation fails at almost the first step. I am following the FAQs on this forum. I did the following:

1. Burn Gutsy 7.10 image for amd64 onto a disc
2. Installed reFit.
3. Inserted Ubuntu CD and booted the Mac with the "C" key held down. It took a long time (2-3 minutes) for the Ubuntu install menu to appear.
4. Selected "install"
5. The screen resolution defaulted to 640x480 with a plug 'n play monitor. I tried changing this to "LCD panel 1440 x 900", and pressing the "test" button, but it failed to display anything and went back to the default resolution.
6. I tried selecting the monitor as  "Apple", but didn't see any option for the Mac Book Pro 15" monitor.
7. I proceeded with the install, but it got stuck on the second line of the install process (I can't remember the message exactly but it was to do with loading files in init.d/rc0.
8. I had reboot the machine.

Has anyone seen this behaviour before? What should I expect in the install process?

Should Ubuntu take so long to start up from the live CD, or could I have a bad CD?

Is it possible to boot from an Ubuntu image on an external hard disk?

Thanks for any help you can give me!

John.

---

### Post by dvdkid919 on 2008-01-19
I just got a MacBook Pro about a week ago and had some trouble installing Ubuntu 7.10
There are a few things I had to do:
1) Use the alternate (text-based installer) disc ISO from ubuntu.com - do NOT use the LiveCD
2) Once it is finished installing.. the first bootup will take a while, because it doesn't have the nvidia drivers installed, so it will go into safe/low-graphics mode after a few minutes of loading with a plain black screen. Once it finally loads, log in at the low resolution.
3) If the wifi is not working, get madwifi from madwifi.org, and compile it. You may need to reboot once more after doing this.
4) Log in at the low resolution again, and at the top of the screen, hit "System" => "Administration" => "Restricted Drivers Management", and it will have nvidia-glx-new as a choice. Click the checkbox for that and it should download, install, and enable it. Reboot after installing this and it should work fine. If when you hit the checkbox it had an error, you might need to edit /etc/apt/sources.list with gedit or nano, and put a # sign all the way at the beginning of the line that says stuff about grabbing the packages from the CD-ROM drive.  For me, it was the third line in the file. Then save and exit the file and type the command "apt-get update"... After doing this, go back into the restricted drivers manager and try the checkbox again. Reboot, and it should work fine.

---

### Post by ssnape on 2008-01-19
I also found that on the alt disk one of the options at startup is to set VGA resolution.  You can set this to 1440 x 900 before telling it to install.  This makes a nicer installation and without the waits.  Of course it loses this knowledge by reboot time but every little bit helps.

---

