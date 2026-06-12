---
title: "Problem updating NVIDIA 5700 drivers. Envy wont install!!!"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by jlblurredvision on 2008-03-10
Hello. I am very new to Ubuntu and have a problem. I did manage to get Ubuntu to dual boot on my desktop with XP but cannot get my video card drivers to work. I am currently using it off the onboard video. Its an older computer with a P4 2.8 GHz and the above NVIDIA FX 5600 Ultra 128Mb card. Motherboad is as ASRocK 775i65gv. I have tried 2 ways of updating them but neither worked.

1. I downloaded the appropriate drivers off the NVIDA website but i dont know if I did anything after that correct. I tried ALT+F2 and typed "sh NVIDIA-Linux-x86-169.12-pkg1.run" what the website said to type. I also typed this into terminal but nothing worked.

2. I downloaded and tried to install envy. When the package installer comes up it says " Error: Dependency is not satisfiable: debhelper".

I am sure these are simple fixes. I have been searching the internet and these forums for and answer but have been unable to find anything.

Remember I am very new to Ubuntu *please don't make fun of my stupidity* :) and any help would be greatly appreciated. Thank you.

---

### Post by Dithers on 2008-03-10
Go to Add/Remove Preferences and check all the boxes in Ubuntu Software and Updates, and then try and install Envy. that should work

---

### Post by jlblurredvision on 2008-03-10
Thanks for the reply.

Now I have an even worse problem. I went to go try what you said and I started up Ubuntu, seems as if something I did while I was in there messed up my onboard video. I can hear it startup but no video. I even tried hooking my monitor up to my video card output, nothing. I cant remember what all I changed but it wasn't much. I may have turned the visual effects up to the highest level and I messed with the above mentioned things about drivers.

Can anyone help me get my video back?

P.S. Everything else is OK as I am on the same computer and video right now only running Windows.

Got video working. Changed onboard to 32Mb in the BIOS and it works now.

---

### Post by jlblurredvision on 2008-03-11
Ok. So I got my onboad video working again and after following the steps suggested above I installed all kinds of updates. After restarting I was able to "enable" the NVIDIA drivers from the restricted drivers tab. When I rebooted Ubuntu froze halfway through booting, twice. I still cannot install Envy because of the same reasons as before. 

Any more suggestions on updating the restricted drivers, installing Envy, or installing the NVIDIA drivers from there website? My onboard isn't very capable and I would really like to get my video card working. 

Thank you to anyone who can help!!!

---

### Post by Dithers on 2008-03-11
I apologize I didn't mean for you to install all of the un-supported updates. I meant for you to enable the required downloads to install envy. I should have been more clear. 

envy still won't install?

---

### Post by firestormx37 on 2008-03-11
Well I can help you out with manually installing the drivers from the Nvidia site.  In order to successfully run the driver installation, you have to shut down the gui.  So, make sure that you have the NVIDIA-Linux-x86-169.12-pkg1.run saved in a folder somewhere.  Then press CTRL+F1.  This should bring you out to a terminal.  You may have to login to the terminal so do that and then type the following:

```
sudo /etc/init.d/gdm stop
```

This will shut down the graphical system.

Next use cd to navigate to the directory where you have the file stored.

```
sh NVIDIA-Linux-x86-169.09-pkg1.run
```

This will run the installer.  Make sure that you say yes to the option at the end where it asks if you want to run nvidia-xconfig.  After that is done:

```
sudo reboot
```

This should reboot your system and have the nvidia drivers installed.  You know it is working if you see the nvidia logo flash on the screen during startup.  Good luck.

EDIT:  One last note.....I have run into problems when I try the above and have the restricted drivers enabled.  So before pressing CTRL+F1, uncheck the restricted driver and it should uninstall.

---

### Post by Kiri on 2008-03-12
I have a similar problem, and I tried to install the drivers manually, but when I try and run the NVIDIA installer, it tells me X server is still running. I typed the stop commant and it said OK but I still cant run the installer... 

How can I stop the X server and gui completely?

---

### Post by firestormx37 on 2008-03-12
Kiri, that is strange that it won't stop it. Make sure you are using the following command to stop.

```
sudo /etc/init.d/gdm stop
```

Try rebooting and then going to the terminal right from the login screen (CTRL+F1).  Then see if you can use the above to shut it down.

There is only one other way that I can think of, which I don't recommend unless you know what you are doing.  Temporarily disable gdm in ONE of the runlevels 2-5 and then telinit into that runlevel from the console.  You can even run the above command to make sure gdm is off.  Then go ahead and install the drivers.  Reenable gdm where you turned it off and reboot.  If you want to know more about turning on/off services, then take a look at this great post:
[http://ubuntuforums.org/showthread.php?t=89491&highlight=boot+speed](http://ubuntuforums.org/showthread.php?t=89491&highlight=boot+speed)

Again, be careful with turning off services and make sure you know how to turn them back on before you turn them off.

---

### Post by Riffer on 2008-03-12
[SIZE="2"]The drivers from the nVidia site won't work until you make them executable.  You also have to run it in "level 3" and stop GDM.  To do this I would first write down these instructions because you will be shutting down the GUI for a bit and I'm assuming that your package is on your desktop.  Also have written down the complete name of the package with correct syntax.

Press Ctl, Alt and F3 together, 

this will get you into your level 3 environment.

The next command shuts down your GUI.
> sudo /etc/init.d/gdm stop.

You next move to your Desktop folder.
> cd Desktop

now you make your package executable.
> chmod 777 NVIDIA-Linux-x86-169.04-pkg1.run
change the package name to fit.

You next run the package 
> sh NVIDIA-Linux-x86-169.04-pkg1.run

or

> sh ./NVIDIA-Linux-x86-169.04-pkg1.run

If you get an error mesage saying you need to be root, put "sudo" in front of the commands.

When you get the driver installed you will need to reboot so put in .

> sudo reboot

And that should do it.  Good Luck.

 [/SIZE]

---

### Post by forrestcupp on 2008-03-12
If you're having problems installing the Envy .deb, it's probably one of two reasons.  Either you're installing the wrong version of Envy, or you don't have your Universe and Multiverse repositories enabled.

The NG version of Envy is now for Hardy.  Now Gutsy is included in the legacy version of Envy.

The easy way to enable the needed repos is to open Synaptic, go to Settings->Repositories, and in that window in the 'Ubuntu Software' tab make sure all boxes are checked.  Then exit out of that and click the Reload button.  

Then you should be able to close Synaptic, and if you have the right version of Envy, it should install correctly.

---

### Post by Kiri on 2008-03-12
Thanks for the replies. 
I used >  sudo /etc/init.d/gdm stop and it says ok, but when I run the nvidia driver package it still tells me that X server is running. 

Even after following Riffer's instructions exactly, the same error.

forrestcupp, I also tried that approach, but envy gives me an error 22 when trying to install the nvidia driver.

---

### Post by waste301 on 2008-03-12
Quick question.  Ubuntu wants to update python but its unlicensed.  Is it OK?

---

