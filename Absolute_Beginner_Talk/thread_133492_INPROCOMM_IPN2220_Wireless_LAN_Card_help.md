---
title: "INPROCOMM IPN2220 Wireless LAN Card help"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by newlinuxuser on 2006-02-20
Hello, im new to Linux, I have the ubuntu distro installed, it works fine apart from I cant seem to connect to the internet. I have googled the internet and found some confusing stuff i am a noob running INPROCOMM IPN2220 Wireless LAN Card on a Toshiba laptop. I would be greatful for any help, at the moment I cant completely get rid of windows because I need the internet. :cry:

---

### Post by carlosqueso on 2006-02-20
Okay....it seems you need to use ndiswrapper to use this card as it has no linux driver.  First, you need to download the windows XP drivers for your card, and the ndiswrapper-utils package from here: [http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils](http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils)

Then put both of those on your Ubuntu system and install ndiswrapper-utils by going to the directory which contains the .deb file that you downloaded and typing ```
sudo dpkg -i ndiswrapper-utils_1.1-4ubuntu2_i386.deb
``` Next, unzip the file with your windows drivers in it, go to that directory and type ```
sudo ndiswrapper -i <inf file>
sudo modprobe ndiswrapper
``` where <inf file> is the name of the inf file in the windows XP driver.   Make sure you are in the directory that contains the drivers and remember that unlike dos or windows that linux is case sensitive.   

To bring the card up, you may need to type ```
sudo ifup wlan0
``` Also, to make the card work at boot, you need to type ```
sudo ndiswrapper -m
```
Let me know if you run into any problems.

EDIT: Added sudo cause of my bad memory.

---

### Post by newlinuxuser on 2006-02-20
Not much luck so far, I had a hard time finding XP drivers - did eventually find them I think, i downloaded the ndiswrapper tool. You'll have to forgive my dumbness but how and where do I go about typing these codes -  doubled clicked the *.deb file in Ubuntu and i got an error message saying "file unsupported". Thanks for your patience.

---

### Post by carlosqueso on 2006-02-20
you are doing well actually.  To type anything that I put in those code thingys you need to open up a terminal.  In the default Ubuntu, it's under Applications-> Accessories->Terminal.  Then you need to find the directory that the .deb is in (if you can see it on your desktop it's in Desktop).  and type ```
cd Desktop
``` right after you open up the terminal.   Of course replace Desktop with where you downloaded the .deb file.

---

### Post by newlinuxuser on 2006-02-20
I managed to install ndiswrapper fine, having some problems installing the driver though - this is the code i recieved. thanks again for your replies :) 



mike@ubuntu:~$ cd Desktop/WinXP
mike@ubuntu:~/Desktop/WinXP$ ndiswrapper -i NETI2120.INF
Installing neti2120
Unable to create directory /etc/ndiswrapper/neti2120. Make sure you are running as root
mike@ubuntu:~/Desktop/WinXP$

---

### Post by carlosqueso on 2006-02-20
hmmm....didn't think you needed to run that command as root.  Just put sudo before it so you get ```
sudo ndiswrapper -i NETI2120.INF
``` Sorry, it's been a few months since I installed my wireless card.   I've changed the above post to reflect the real way to do it.

---

### Post by newlinuxuser on 2006-02-20
when entering sudo ifup wlan0 i got a message along the lines of "Ignoring unknown interface" well i entered the next code sudo ndiswrapper -m and rebooted. still no connection :cry: any ideas? - oh I looked in Admin Network tools and the only interface there was for a modem. :???: thanks again.

---

### Post by carlosqueso on 2006-02-20
hmmmmm.....what does ```
ndiswrapper -l
``` give you now?

---

### Post by newlinuxuser on 2006-02-20
ndiswrapper -1 gives me options, i then entered ndiswrapper -l and it gave the filename of my driver and said it was present. :confused:

---

### Post by carlosqueso on 2006-02-20
does it also say hardware present?  Because if it doesn't that's hardware problems or you have the wrong driver for your hardware.

---

### Post by newlinuxuser on 2006-02-20
No it just said that the driver was present, ok my hardwares working fine, i guess i have the wrong driver - if i find the driver what do i have to do install it, and will or how will i have to uninstall the previous one. :neutral:

---

### Post by newlinuxuser on 2006-02-20
it just says the drivers present, not that the hardwares present - ive been surfing the net for the new driver but cant find it :???: i dont want to be stuck with windows lol... well i'll keep looking. Thanks for your help:-D  take care.

---

### Post by carlosqueso on 2006-02-20
You may have the wrong driver....type ```
lspci
``` in a terminal and it'll tell you what linux thinks your hardware is......this is much better than relying on specs that you get, as the hardware changes and they don't tell you (unforunately, I know that from experience).

---

### Post by Guy_AD on 2008-06-19
> **newlinuxuser said:**
> I managed to install ndiswrapper fine, having some problems installing the driver though - this is the code i recieved. thanks again for your replies :) 



mike@ubuntu:~$ cd Desktop/WinXP
mike@ubuntu:~/Desktop/WinXP$ ndiswrapper -i NETI2120.INF
Installing neti2120
Unable to create directory /etc/ndiswrapper/neti2120. Make sure you are running as root
mike@ubuntu:~/Desktop/WinXP$

is your account the first account that you created after installing ubuntu? if not, try

"sudo ndiswrapper -i NET12120.INF"

otherwise it will try and install it as a non-root user (doesn't work). you could also try this if your account *was* the first account, as something may have occurred to prevent you from becoming root.

hope this helps.

---

