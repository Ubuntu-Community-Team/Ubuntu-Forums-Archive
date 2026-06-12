---
title: "Nvidia Help Please"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by davesbrain on 2008-01-26
Well, my Ubuntu is running sweeeet....except for a couple of annoyances with my Nvidia.
My hardware is an MX440 card, a 19"Micron crt(Panasonic) and a 17"Mag Innovision crt.
The Micron is my main monitor and the Mag is to the right of it.   I would like to use 'twin view' with both monitors set at 1024x768 75.  When I set it up in the nvidia settings and hit apply, everything(wallpaper, and both top, bottom panels) goes white. Driver version is 96.43.01.


Also,  my nvidia settings dont stay after reboot.  I usually bump up the brightness and digital vibrance a tad and set it at 1024x768 75.   Then after reboot, it's set at 1600x and my other settings back.

---

### Post by swoll1980 on 2008-01-27
My first advice to you would be to instaal the newest update from nvidia.com I've got version 169.09 released on the 20th very nice. To install it down load it to your desktop
in a terminal ```
cd ~/Desktop
``` ```
sudo chmod a+x name_of_nvidia.run_file
``` in order to install it you will have to restart and boot into recovery mode in the terminal there ```
cd ~/Desktop
``````
ls
``` The ls command will give you a list of files in the directory find the nvidia file and do ```
./name_of_nvidia_file
``` this will bring you to the installer it's self explanatory at this point

---

### Post by brokenhachi on 2008-01-27
im not having this same problem but i would like to install the driver for my nvidia go5200 card so i tried this way and....

it went to listing a bunch of crap for about an hour with nothing happening... so i thought it shouldnt take an hour to install a driver so i halted the system and rebooted.... 


does it really take longer than an hour to install it?

---

### Post by swoll1980 on 2008-01-27
no how did you go about doing it

---

### Post by brokenhachi on 2008-01-27
i did everything you posted in order... it gave me some error about kernel something.... i cant remember exactly what it gave me but its ok, i used envy and it installed my driver just fine. although now i am having problems with compiz... (i made a tread about it)


for the creator of this thread, here is the link to envy: [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

just downoad the one that applies to your copy of ubuntu and follow the faq. its real easy.

maybe that will work for ya.

---

### Post by swoll1980 on 2008-01-27
envy gives you a out dated driver. During the nvidia install you have use compile kernel option

---

### Post by davesbrain on 2008-01-27
Well,  I did try and install the new(169) drivers with Envy.  If you choose the 'manual' option a list pops up at the bottom, with the new 169.09 drivers at the top of the choices.  I chose that and continued,  the Envy terminal window pops up and I watch it remove my old drivers, download new ones, and installs it.   It then said something about configuring X server automatically( I chose yes) then it said to reboot. Did so.  Got a black screen with plain grey dialog wanting me to identify monitor.  I think I just went with a default at 1024 just to continue booting to the desktop.  I then tried to open the nvidia settings control panel and it gave me some error about failing to load x server(I think thats what it said).  So I opened Envy again, chose automatic(so it would identify my hardware), it removed the 169 drivers and reinstalled the version 96 drivers.  I'm back up running except for the same  annoyances that I first mentioned.

---

### Post by AmericanXer0 on 2008-01-27
> **bloor75 said:**
> My first advice to you would be to instaal the newest update from nvidia.com I've got version 169.09 released on the 20th very nice. To install it down load it to your desktop
in a terminal ```
cd ~/Desktop
``` ```
sudo chmod a+x name_of_nvidia.run_file
``` in order to install it you will have to restart and boot into recovery mode in the terminal there ```
cd ~/Desktop
``````
ls
``` The ls command will give you a list of files in the directory find the nvidia file and do ```
./name_of_nvidia_file
``` this will bring you to the installer it's self explanatory at this point

I went through this step by step and I received an error stating that I'm running an X server and need to exit it before installing. I just installed Ubuntu today, so I don't know how to go about this yet. Detailed steps on how to exit X server and get these 169.09 drivers installed would be greatly appreciated!

---

### Post by AmericanXer0 on 2008-01-27
> **AmericanXer0 said:**
> I went through this step by step and I received an error stating that I'm running an X server and need to exit it before installing. I just installed Ubuntu today, so I don't know how to go about this yet. Detailed steps on how to exit X server and get these 169.09 drivers installed would be greatly appreciated!

I downloaded and ran Envy and it installed the nvidia 169.09 drivers for me. So if anyone is still having trouble, give Envy a try.

Still, it'd be helpful to know how to exit X server to manually install nvidia drivers.

---

### Post by brokenhachi on 2008-01-28
i think ctrl+alt+bksp and then boot into recovery mode.

edit: dave, now that i think about it... i think i remember reading somewhere that envy was for geforce cards.... but maybe not. you might want to check into that.

---

### Post by bumanie on 2008-01-28
I think crtl+alt+f1 stops x server and takes you to console mode.
Someone will correct me if I am wrong.

---

