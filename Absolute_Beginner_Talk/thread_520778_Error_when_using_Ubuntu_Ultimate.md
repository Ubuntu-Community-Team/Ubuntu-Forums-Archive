---
title: "Error when using Ubuntu Ultimate"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by 0verdose on 2007-08-08
Before I start telling you what the error exactly is I think it may be useful to know that I am a beginner to the complete linux scene including ubuntu and used to previously have windows installed.

Today I downloaded and burned onto a disc Ubuntu Ultimate. I then ran the disc and installed it. I started to install of the required updates and the graphic card drivers etc, when I got an error.

Ubuntu asked me to restart to I did and when it loaded back up insteaded of going into the operating system it came up with a high contrast window saying;

> Failed to start the X server(your graphical interface.) It is likely that it is not set up correctly. Would you like to diagnose the problem.

Yes                                       No

When you click yes it comes up with another full screen window with the error, this is a snippet taken from it;

> Error: API mismatch: this NVIDIA kernah mkdule's vErsion does not match. Please make sure that all the kern%h module and all NVIDIA drive components have the same versi/j

Failed to initialize the NVIDIA kernel module!

Then I was prompted with another window which read:

>  The X server is now disabled. Restart GDM when it is configured correctly.

After pressing 'OK' on this window also another fully black screen appeared with more text on it, which read at the bottom:

> Enable Alsa quequeneer first by editing /etc/'efault/timidity.

I have tried reinstalling ubuntu 4 times and I keep getting the same error after multiple restarts (2-4) especially after installing updates. Furthermore I have restarted after the error and still get presented with the same screens.

Any help will be appreciated, as I said I am new to linux all together, so could you try to be very explanatory.

---

### Post by overdrank on 2007-08-08
> **0verdose said:**
> Before I start telling you what the error exactly is I think it may be useful to know that I am a beginner to the complete linux scene including ubuntu and used to previously have windows installed.

Today I downloaded and burned onto a disc Ubuntu Ultimate. I then ran the disc and installed it. I started to install of the required updates and the graphic card drivers etc, when I got an error.

Ubuntu asked me to restart to I did and when it loaded back up insteaded of going into the operating system it came up with a high contrast window saying;



When you click yes it comes up with another full screen window with the error, this is a snippet taken from it;



Then I was prompted with another window which read:



After pressing 'OK' on this window also another fully black screen appeared with more text on it, which read at the bottom:



I have tried reinstalling ubuntu 4 times and I keep getting the same error after multiple restarts (2-4) especially after installing updates. Furthermore I have restarted after the error and still get presented with the same screens.

Any help will be appreciated, as I said I am new to linux all together, so could you try to be very explanatory.

Hi, what is your graphics card? When you get the xorg error click ok and then it should bring you to the command prompt, If not use the keys ctrl,alt,F1 all at the same time and this will enter the terminal ( command Pormpt) there you can use the command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Answer a few question and if you dont know the answer then leave the default answer given. This should bring you back to the desktop after reboot. Good lcuk!

---

### Post by 0verdose on 2007-08-09
Thanks alot for the help, I now need to wait for the error to come up again to try it. My graphic card is a NVIDIA 7900 Gs 256.0MB. 

I am now also having problems about using the correct resolution, when I go to change it, it does not have 1024x1280 which is what I normally use. This isn't a big issue for now though.

Thanks for the help once again.

---

### Post by Nexus... on 2007-08-09
There is a 'recovery mode' for Ubuntu where you would enter
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` 

Also when you are reconfiguring the xorg.conf you will be able to add pretty much any of the resolutions to the file, the resolutions will then be avalible when you goto System>Preferences>Resolution.

I'm pretty new to Linux but getting there :)

---

### Post by 0verdose on 2007-08-09
Ok thanks nexus, I will give it a go. I am just re-installing Ubuntu now and when that's done I will play about with the configuration.

---

### Post by 0verdose on 2007-08-09
Hmm I tried typing it and nothing came up.

Also now another problem:

When I turn on the computer after the Dell screen it comes up with what operating system I would like to go onto, one being windows xp and the other 4 being ubuntu, 2 of which are being recovery modes for the ubuntu installations. Shouldn't I only have one recovery mode and one normal mode? If so how do I get rid of the older version, or the one I am not using, without reformatting the whole hard drive...

---

### Post by splintercellguy on 2007-08-09
Simple, you can either remove the older kernel versions or edit the GRUB menu.lst using a tool like GrubED: [http://ubuntuforums.org/showthread.php?t=228104](http://ubuntuforums.org/showthread.php?t=228104) And try executing the aforementioned command in recovery mode, then rebooting by typing shutdown -r now, and performing a normal start.

---

