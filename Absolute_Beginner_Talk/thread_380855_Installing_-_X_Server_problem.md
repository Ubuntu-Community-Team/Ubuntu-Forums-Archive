---
title: "Installing - X Server problem"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Lunaris on 2007-03-10
Thank you for taking the time to read this post. I am a complete (let's see... what's lower than a newb....) poptart when it comes to technical aspects of computers, but always wanted to get into the Linux world (hoping to raise from the poptart ranks). Ubuntu seems to me like a great way to introduce oneself into the ranks of non-windows people... though I have been wrong before...
I've been surfing the forums for about 7 hours now, trying to find a solution to my problem that I can understand. I apologize in advance if the following post provides too much irrelevant information, but I felt the more I give, the easier it would be for people to give advice.

I am trying to install Ubuntu on a separate 10Gb partition that I created with PartitionMagic 8.0. I pop in the freshly downloaded/burned disc (6.10), restart, boot from it, and see the pretty graphical interface. Select "Start or Install Ubuntu" from the neat, little menu, and wait for it to crash. *cry*

A few seconds after the process starts, I get the following error message:
> Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
Selecting "Yes" leads to the following:
> X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux ubuntu 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Build Date: 07 July 2006
Module Loader present
Markers: (==) Default setting, (EE) error
(==) Log file: /var/log/Xorg.0.log". Time: Sat mar 10 11:40:19 2007
(==) Using config file: "/etc/X11/xorg.conf"
(EE) No devices detected.

Fatal server error:
no screens found.

It also states that I should visit wiki.x.org for a new version, if one is available. There is, but, being a poptart, I have NO CLUE how to install it (there are like 14 files and they all look the same)... if that's what you are supposed to do.

My question (finally, after all that) is: What exactly do I need to do (besides going back to my cave)? ANY advice would be Greatly appreciated!

Once again, thank you for taking the time to read/respond to this poptart.

Edit:
System:
Nvidia nForce 680i - Intel Core2 Duo 6600 @ 2400MHz - Nvidia GeForce8800GTX - Ageia PhysX - 2Gb RAM

I am booting from ubuntu-6.10-desktop-i386.iso disk that I downloaded/burned yesterday. The graphical Ubuntu menu comes up (as per the first screen of [https://help.ubuntu.com/community/GraphicalInstall)](https://help.ubuntu.com/community/GraphicalInstall)). I can do the check CD and memory test commands, but after I select "Start or Install Ubuntu" or "Start Ubuntu in safe graphics mode" that X server error message pops up.

---

### Post by overdrank on 2007-03-10
> **Lunaris said:**
> Thank you for taking the time to read this post. I am a complete (let's see... what's lower than a newb....) poptart when it comes to technical aspects of computers, but always wanted to get into the Linux world (hoping to raise from the poptart ranks). Ubuntu seems to me like a great way to introduce oneself into the ranks of non-windows people... though I have been wrong before...
I've been surfing the forums for about 7 hours now, trying to find a solution to my problem that I can understand. I apologize in advance if the following post provides too much irrelevant information, but I felt the more I give, the easier it would be for people to give advice.

I am trying to install Ubuntu on a separate 10Gb partition that I created with PartitionMagic 8.0. I pop in the freshly downloaded/burned disc (6.10), restart, boot from it, and see the pretty graphical interface. Select "Start or Install Ubuntu" from the neat, little menu, and wait for it to crash. *cry*

A few seconds after the process starts, I get the following error message:

Selecting "Yes" leads to the following:


It also states that I should visit wiki.x.org for a new version, if one is available. There is, but, being a poptart, I have NO CLUE how to install it (there are like 14 files and they all look the same)... if that's what you are supposed to do.

My question (finally, after all that) is: What exactly do I need to do (besides going back to my cave)? ANY advice would be Greatly appreciated!

Once again, thank you for taking the time to read/respond to this poptart.

Hi you can reconfigure the x with this command in the terminal under applications, accessories, teminal *sudo dpkg-reconfigure xserver-xorg* and just follow the instructions.
Now for the updates  you need to find witch your system needs like are you running amd 64 or something else. Hope this helps. Good luck!

---

### Post by pveith on 2007-03-10
Did i understand you correctly: The 6.10 install cd doesn't even come up with a graphical interface on your system? Can you please write what graphic card you are trying to use? And more details on your setup would be very usefull (e.g. which install cd you are using (AMD64, i386, PwerPC), your processor, etc.)...

---

### Post by Lunaris on 2007-03-10
System:
Nvidia nForce 680i - Intel Core2 Duo 6600 @ 2400MHz - Nvidia GeForce8800GTX - Ageia PhysX - 2Gb RAM

I am booting from ubuntu-6.10-desktop-i386.iso disk that I downloaded/burned yesterday. The graphical Ubuntu menu comes up (as per the first screen of [https://help.ubuntu.com/community/GraphicalInstall)](https://help.ubuntu.com/community/GraphicalInstall)). I can do the check CD and memory test commands, but after I select "Start or Install Ubuntu" or "Start Ubuntu in safe graphics mode" that X server error message pops up.

If I press 'Esc' at that screen, the graphical menu goes away and I get a text interface (just a command line). I tried tying in the sudo thing, but it didin't recognize the command.

*First post edited.*

---

### Post by pveith on 2007-03-10
Hm, did a little searching and i seems that the graphical installer has some problems with the geforce 8800gtx card, which means the open-source nv driver does not support it.

For installation you could use the "alternate cd", which doesn't use the graphical environment for installation. Later on you could switch to closed source nvidia drivers, which should get you X up an running.

---

### Post by Lunaris on 2007-03-10
Thank you! I am going to download the Alternate CD right now =]

---

### Post by pveith on 2007-03-10
Good to hear. You will probably be left with a console only system after installation. So here are the commands to install the nvidia driver binaries:

```
 
sudo invoke-rc.d gdm stop
sudo apt-get install linux-restricted-modules
sudo dpkg-reconfigure xserver-xorg

```

Then select the nvidia driver in the menu, which apears in the last step..

After that is done just

```
 
sudo invoke-rc.d gdm start

```

To test if erverything worked out.

Alternatively you could use "sudo nvidia-xconfig" instead of "dpkg-reconfigure xserver-xorg"...

Hope that helps..

---

### Post by Lunaris on 2007-03-11
Ok, the alternate CD worked, and I was able to install.

You were correct, and the system started in console only mode. There was much rejoicing (on my part =P)

However, when I typed in the commands, the console told me:
E: Couldn't find package linux-restricted-modules

I can still do the next line, but no matter what options I pick in the menues that follow, I still get an X server error message I got in the very beginning.
I tried doing the "sudo nvidia-xconfig" and "sudo dpkg--reconfigure nvidia-xconfig" and "sudo nv-xconfig" and ... ... pretty much all possible premutations of that, and it's just not working.

I bow my head in shame, as all poptarts should, and quietly await any advice on this matter.

---

