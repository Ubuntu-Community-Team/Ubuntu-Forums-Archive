---
title: "Problem with attaining NVIDEA driver"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by darkdeek on 2007-04-15
I recently purchased a new graphics card the GeForce 8800 GTS,
I have a dual boot system 80% Ubuntu (Dapper Drake) 20% Windows XP (For games),
After installing when i boot up Ubuntu I get the X server error, meaning i need a different driver,

I've perused the forums for a day now and have run across several solutions,
One being switching to Versa drivers,
Another updating my driver via the wget command, *this was most appealling to me*

So I attempted wget [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run) (copied right from the properties tab)
I got the dread 404 error, 
I tried wget [ftp://us.download](ftp://us.download). ...
I get wrong login (anonymous)
I typed it in a hundred times, I know this file exists ive located it on my other desktop,
I know i have the path right, but i continue to get these 404 errors although other pages work

Is there something fundamental that I am missing?
Might it be because of my firewall / hub settings even tho other pages seem to download fine (such as [http://www.google.com/index.html)?](http://www.google.com/index.html)?)

Any help would be appreciated.

---

### Post by jem7v on 2007-04-15
If you change your driver in /etc/X11/xorg.conf to "nv" can you get a graphic login at all?  If so, rather than try to download the file with wget, why not just download it from your web browser and save it to your home directory?  It'll be the same result.  The very link in your post works if you just click on it (I tried it).

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper) is probably the overall best set of instructions I've seen for installing NVidia drivers.

---

### Post by darkdeek on 2007-04-15
> **jem7v said:**
> If you change your driver in /etc/X11/xorg.conf to "nv" can you get a graphic login at all?  If so, rather than try to download the file with wget, why not just download it from your web browser and save it to your home directory?  It'll be the same result.  The very link in your post works if you just click on it (I tried it).

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper) is probably the overall best set of instructions I've seen for installing NVidia drivers.

I wish it were that simple >_< ... the reason i use the wget command is because all i have access to is the command line. On start up it automatically goes into an error message saying "X11 encountered a fatal error, do you wish to disable?" or somthin along those lines and so this whole process must be done from the command line.

Ive gone as far as to download the .run file on another desktop put it onto a USB card and attempt to run it from the command line on my linux machine but then i ran into ANOTHER problem >_< my USB drive hasnt been working to good in the past taking maybe 5-10 mins for it to actually write something to it whereas it would show it on the disk as if it were done instantly, anyway aparently im not able to find the USB drive and ive checked all the usual locations /media, /etc, /dev. Couldnt find it my next attempt will be to put the same file onto a CD and then attempt to copy it off the cd into my home directory and then run it like that. I assume access cdrom via /media/cdrom , is this correct? any who ill give it a wirl.

thank you for your input tho

---

### Post by jem7v on 2007-04-16
Okay, but from the command line you can edit your xorg.conf file to change to the nv or vesa driver and hopefully get a working (though slow) X server.  A slow X server is still more useful than no X server at all.
```
sudo nano /etc/X11/xorg.conf
```
Scroll down until you get to "Section "Device"" and change the Driver to "nv" or "vesa", then exit and save.

Hopefully this will be a temporary solution to let you get to a working X server, from which you can access a web browser and download that NVidia installer or Envy to get a Proper driver.  (The problem with the NVidia installer is that it sometimes requires a bunch of headers and kernel packages and stuff so it can compile things specifically for your system, and if they aren't already installed you'll have to do that too.  Envy takes care of those dependencies really well.)

Have you tried the nv or vesa drivers as a temporary solution until you can get the proprietary nvidia driver to work?

---

### Post by darkdeek on 2007-04-16
I tried the config changes and both nv and vesa still had an error, 
here is the output:
(==)  Using config file: "/etc/X11/xorg.conf"
(WW) VESA: No matching Device section for instance (BusID PCI:2:0:0)
found
(EE) No devices detected.

So apparently its not able to locate the card = /

I tried putting the driver (the new one) onto a CD, but when i go to access it using cd /media/cdrom then ls
i see nothing. its not there i also tried the /media/cdrom0 directory ... i just assumed this is how you access cdrom via command line. Was this method correct?

The last thing i want to do is reformat and install all three of my OS once more >_<.

Edit: I am currently openning up my computer to take out the graphics card as my temporary solution >_<.

---

### Post by darkdeek on 2007-04-16
Wow that was in there TIGHT. Anyway,
I took it out started it up on the integrated graphics,
Luckily no problems so its not like i messed up my whole OS.
And i got the .run file i need in my home directory now so should have no problem attaining it from command line.

So ill let you know how it turned out after i write my compilers program, while i have a working linux environment infront of me. :D

---

### Post by jem7v on 2007-04-17
Might as well install "envy" too while you've got a working GUI, just so you have as many tools as possible when you go back to your NVidia card!

---

