---
title: "failed to start the X server"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by mudcow007 on 2007-07-19
hello people 

i have just installed image-server on my freshly installed feisty machine now im getting

Failed to start X server

at the bottom of the screen i have two error messages

(EE) NVIDIA ( 0): Failed to load the NVIDIA kernel module!

(EE) NIVIDIA(0 ): ***Aborting***

(EE) Screen(s) found, but none have a usable configuration

i have tried "sudo dpkg-reconfigure xserver-xorg"

but it didnt work

:confused:

---

### Post by ubuntu.daemon on 2007-07-19
hello person!  lol what nvidia package you using?? the open sourced?  or the proprietary ones form nvidia?

---

### Post by mudcow007 on 2007-07-19
lol

to be honest i wouldnt have a clue what package im using is the a command to find out?

i tried this [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_1_-_ONLINE_INSTALLATION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_1_-_ONLINE_INSTALLATION)

but thats hasnt had any effect :(

anyone help :)

---

### Post by taurus on 2007-07-19
Which nVidia graphic card do you have?

Applications -> Accessories -> Terminal
```
lspci | grep VGA
```
Or edit /etc/X11/xorg.conf

```
sudo nano -Bw /etc/X11/xorg.conf
```
and replace the "nvidia" with "nv" as the Driver for your graphic card for now.  Save the change and exit with <Ctrl>o and <Ctrl>x.

Reboot and see if X is working now with nv.

---

### Post by notoeverything on 2007-07-28
Im having the same problem. I ran the lspci I (on a mac with no vertical line key :( ) grep VGA command and it gave me

01:00.0 VGA compatible controller: nVidia Coporation NV34 [GeForce FX 5200] (rev a1)

also tried the "sudo nano -Bw /etc/x11/xorg.conf" command but that just resulted in an editable document but with content. Any help please?

---

### Post by andyho on 2007-07-28
Hey there guys.. I JUSTgot my Nvidia 5200 to work 2 days ago, it took me about a week! For one I had to disable my onboard video. Here's how I got mine to work...

1- Enter terminal and enter:

sudo nano -w /etc/modprobe .d/blacklist

2- add the following lines to the end of the file:

blacklist agpgart
blacklist intel_agp

3- Ctrl+x to exit and save..

4- then install drivers:

sudo apt-get install nvidia-glx-new  (or whatever drivers you want to use)

sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf_backup  (just in case things go weird!)

sudo nvidia-glx-config enable

sudo nvidia-xconfig --no-composite

sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

5- reboot and switch to PCI

If you get a freeze up at the beginning just ctrl+alt+f1 it to get a command prompt and see if your settings "stuck" in xserver. Mine went back to "vesa" quite a few times. :(

I pretty much followed the installation instructions.. but like step 4 on the installation guide didn't make any sense to me because there wasn't a way to alter things until I rebooted?! I'm assuming you might have some of the same similar issues! :) There was just little things within the installation guide that I worked around to get it to work.. by the time I was finally done I had created like 5 xorg backups! :lol: But then I just went and deleted them all afterwards! HTH!!

---

### Post by notoeverything on 2007-07-28
I seem to be having a problem. When i run the "sudo nano -Bw /etc/X11/xorg.conf" or "sudo nano -w /etc/modprobe .d/blacklist" commands it comes up with what appears to be an editable document but it has no contents. Any ideas why anyone?

---

### Post by andyho on 2007-07-28
sounds like it wiped out your config file if nothing's there... I could be wrong though!? if you sudo dpkg-reconfigure -phigh xserver-xorg does it re-write it for you??

---

### Post by notoeverything on 2007-07-28
Cheers that seems to have sorted it.

---

### Post by notoeverything on 2007-07-28
The xorg config file was already set to 'nv' so I tried changing it back to nvidia but that made no difference. How would I reset the 'sudo nano -w /etc/modprobe .d/blacklist' file seeing as thats blank too.

---

### Post by andyho on 2007-07-28
oops.. sorry I just noticed something.. "sudo nano -w /etc/modprobe .d/blacklist" should be sudo nano -w/etc/modprobe.d/blacklist 

no space between the period and d! see if that'll bring up the correct file! ;)

---

### Post by notoeverything on 2007-07-29
No luck :(

---

