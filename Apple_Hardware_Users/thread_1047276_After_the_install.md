---
title: "After the install"
date: 2009-01-22
forum: Apple Hardware Users
---

### Post by SNAFU0062000 on 2009-01-22
I was able to install Ubuntu 8.10 PowerPC. i am able to boot and start the OS But Graphcs(iMac PowerPC 750@700mhz 1gRam And 60g HD) is Low and i know i need to do the sudo nano /etc/X11/xorg.conf but i just dont really know how to do that and if some one can just tell me the EZ way that would be nice and the othere thing iswhen i try to access any of the programs it open the program but rifgt after it will close. Came some one just make a list of step by step instrucions for POST INSTALL. thanks

---

### Post by avtolle on 2009-01-22
This will be somewhat a trial and error process, I fear, unless you have a copy of a working xorg.conf file from an earlier Ubuntu installation. On 8.10, ppc, for my G4 Cube, the /etc/X11/xorg.conf file was empty; there was, however, after installation, the following file: /etc/X11/xorg.conf.failsafe. What I did was open it from the terminal```
cat /etc/X11/xorg.conf.failsafe
```and review its contents. I then did```
sudo cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
``` to create the /etc/X11/xorg.conf file, which I opened for editing by```
sudo nano /etc/X11/xorg.conf
``` and made appropriate changes to it using information contained in my 8.04.1 xorg.conf file, by editing it to include the correct values for horizsync and vertrefresh, modes, etc., as well as (in my case) changing the driver from ati to fbdev. Again, I had the benefit of a hard copy of my prior file from which to work. However, as I have posted to another thread, even with this manually edited file, the system starts up in low graphics mode, but upon the completion of loading, I do get to the proper resolution, etc. 

Before going too much further, which graphics card does your iMac have? I'm ignorant about iMacs, but that would help, I think, others who would be in a position to give help to you.

---

### Post by avtolle on 2009-01-22
Since it appears that you have a G3 iMac, see [https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3) and more particularly the thread linked therein for some additional information.

---

### Post by avtolle on 2009-01-22
Take a look at [http://ubuntuforums.org/showthread.php?t=1044462](http://ubuntuforums.org/showthread.php?t=1044462) too.

---

### Post by SNAFU0062000 on 2009-01-22
The video cand is and onBored ati 128 ultra 16mB not very good i am not good at all on linux and mac base computer i got this computer along time ago didnt like it so much so i put it way but it was plugged in and the battery is still good lol. i do have i download of 8.04PowerPC but i cant get it to boot but the download is good. i dont know if this is going to make i big deal but i downloaded all this to my Hp laptop and using Infra Recorder to burn the ISO's

---

### Post by avtolle on 2009-01-22
No, burning the CD in the manner you did should not be a problem, as is evident by the fact that you were able to install the system once you got around the problem with the CD drive not being recognized. 

I would suggest doing the following from Terminal, accessed from the desktop by Applications>Accessories>Terminal, or by pressing Ctrl+Alt+F1 (or F2 through F6), and at the prompt type[cd /etc/X11 #change directory to /etc/X11
ls #to obtain a list of files[/code]and look for a file named xorg.conf and a file named xorg.conf.failsafe. If xorg.conf does not exist type```
sudo cp xorg.conf.failsafe xorg.conf
```to create it. Then open it for editing```
sudo nano xorg.conf
``` which will show you a very sparse file. You would need to add the values for the Horizsync and VertRefresh suggested in the link given above, along with some of the other changes suggested. To save, Ctrl O to write (the default name should come up as xorg.conf or /etc/X11/xorg.conf), press Enter, then Ctrl X to exit nano. Then, exit the terminal by typing exit at the prompt.

Then, do a Ctrl+Alt+Backspace to restart the display, and see if that helps. It might be you will need to do further editing of the file.

---

### Post by avtolle on 2009-01-22
Please see the file attached to post number 2 at [http://ubuntuforums.org/showthread.php?t=1036032](http://ubuntuforums.org/showthread.php?t=1036032) for a general format for the /etc/X11/xorg.conf file for one of my Cubes. Note: this is not for your computer, and you will need to insert the correct values for your particular computer, but is offered for you to see the various sections you may need to have in the file for your computer.

---

### Post by SNAFU0062000 on 2009-01-23
When i go to the terminal i type on the sudo nano /etc/X11/xorg.cong it ask me for PW i put it in and then it brings me to sudo but its empty what should i do?

---

### Post by avtolle on 2009-01-23
There is no visual password feedback at the terminal as a security measure. Type it in, press enter, and if you entered it correctly, you will go on.

I take it that you are staring at an empty file after typing ```
sudo nano /etc/X11/xorg.conf
```which is the norm for 8.10. You will need to enter certain information into the file about your video card, monitor, its refresh rates, etc.

That's why I discussed copying the /etc/X11/xorg.conf.failsafe file to /etc/X11/xorg.conf in a previous post, so there would be a framework with which you might work, using some of the information contained in the link I posted in post #7. 

Unfortunately, I must leave now to pick my daughter up from her employment. Hopefully, after you look at the file I linked, that will give you a place from which to start in creating your own /etc/X11/xorg.conf file. Good luck.

---

### Post by SNAFU0062000 on 2009-01-23
OK ill retry thanks for your time tho

---

### Post by SNAFU0062000 on 2009-01-23
So i did what you told me to (from post #7) do but it is still low should i download the drivers and where can i find them.

---

### Post by SNAFU0062000 on 2009-01-24
now i cant do anything i get to the desktop and the screen is blank but the back ground is there i dont know what to do should i reinstall

---

### Post by avtolle on 2009-01-28
See this thread, and in particular the items in red, to flesh out /etc/X11/xorg.conf file for your computer. Given all the attempts to fix, perhaps reinstalling and starting with a "clean slate" might be helpfur.

[http://ubuntuforums.org/showthread.php?t=770033](http://ubuntuforums.org/showthread.php?t=770033)

---

