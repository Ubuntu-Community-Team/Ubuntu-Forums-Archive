---
title: "How do I access my wireless network from my laptop?"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by chuckcamp on 2007-02-01
OK.  I'm reaching my breaking point.  I want ubuntu to work VERY badly (I've fallen in love with it).  I've got an HP Pavilion ze4500 laptop with a built-in wireless card.  I just want to get on to the internet wirelessly.  Is that too much to ask?



I downloaded and installed ndiswrapper because I thought my card may not be compatible with linux.

I've downloaded and installed Network-Manager.

I've downloaded and installed Wifi Radar.



I know I'm missing something else.  I open up Wifi Radar and no networks are available.  I'm doing this as my laptop is sitting right next to my router.  Can someone please fill me in?  I know there's something basic I need to figure out.

---

### Post by aberry5555 on 2007-02-01
OK now you need to get the windows WIFI drivers for your card and install them if you havn't already. Ndiswrapper is a tool that "wraps" windows drivers so they can be used in Linux. In order to do this you have to use the terminal and, once you've downloaded the drivers, go to the driver folder and then type in "sudo ndiswrapper -i ***FILENAME***.inf (FILENAME being the name of your particular driver. Once this is done type in "sudo modprobe ndiswrapper" and see what happens.

---

### Post by chuckcamp on 2007-02-01
> **aberry5555 said:**
> OK now you need to get the windows WIFI drivers for your card and install them if you havn't already. Ndiswrapper is a tool that "wraps" windows drivers so they can be used in Linux. In order to do this you have to use the terminal and, once you've [COLOR="Red"]downloaded [/COLOR]the drivers, go to the driver folder and then type in "sudo ndiswrapper -i ***FILENAME***.inf (FILENAME being the name of your particular driver. Once this is done type in "sudo modprobe ndiswrapper" and see what happens.

when you say "downloaded", do you mean actually taking the windows disc with the driver and putting the file from the CD onto my hard drive where ubuntu is located?

also, where the hell are these drivers located?  on the XP CD? what folder?  HELP.

---

### Post by linux_kid on 2007-02-01
My windows driver's for my Compaq PC (Similar to HP) are located in /media/sda1/SWSETUP/WLAN/bcmwl5.inf
That translates to C://SWSETUP/WLAN/bcmwl5.inf in Windows

Make sure you copy that file to somewhere on your linux partition such as your home folder before you ndiswrap them

Note the filename may be somewhat different.

---

### Post by aberry5555 on 2007-02-02
You can download your drivers here, but you will need to unpack them from the .exe file:

[ftp://ftp.hp.com/pub/softpaq/sp28501-29000/sp28537.exe](ftp://ftp.hp.com/pub/softpaq/sp28501-29000/sp28537.exe)

save this file on your desktop or somewhere you can get to easily (maybe create a folder in / called "drivers" so the path would be "/drivers". Then open a terminal and type in 

sudo apt-get install unzip

this will install a program that will let you unzip the file and get the .inf file out of it (the driver). Once this is installed do the following command to unzip it:

cd /drivers (if this is where the drivers are saved)
sudo unzip sp28537.exe

This should unzip the contents of the .exe file in to a folder in the "drivers" folder, if it gives you error messages then this .exe file might not be the right type, hopefully it is though. If this doesn't work then the drivers might be available as .inf files, rather than .exe files, somewhere on the net.

Now, once you have the inf files, follow the commands I told you before (making sure you run the commands in the folder that the .inf file is in).

---

### Post by surferkid993 on 2007-12-24
Hello I own the same laptop and want wireless internet for Ubuntu 7.10

I have done all that is said here and I got the two .inf files, though the .exe could not be extracted I used a windows computer to extract them. they were bcmwl5.inf and bcmwl5a.inf.
ndiswrapper -l says they are both are installed and the device is present but the wireless internet still wont work.
It can pick up my wireless network but can't connect.

---

