---
title: "XSERVER will not work on my desktop, please help"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by Remonster on 2006-04-19
Hi, I am new to this forum as you can see and this is my first post :D anyways, I have tried Ubuntu versions 5.04, 5.10 and now 6.06 Flight 6 on my desktop but in every installation XSERVER fails to start, but this time I decided I'm not giving up and running back to WIndows lol, so I've been fighting for 2 days straight (except while at school) to get 6.06 Flight 6 to work on my desktop, in the meantime I installed it on my laptop and it runs absolutely great infact its the only OS on my laptop now and I am using it to type this at the moment :) so far I have tried installing the newest nvidia drivers (I have a 7900GTX graphics card) but for some reason my desktop isn't able to connect to the internet, so I need to install the LAN drivers as well. The trouble is I can't just burn them to a CD like I normally would because my desktop doesn't seem to want to recognize my cd rom drive!](*,) when I stick the CD with the drivers on it into my laptop I can open up the terminal and type in "cd /cdrom" and "ls" and it will show the NVIDIA driver, do the same on my desktop and nothing shows up... 

So I need help getting it to recognize my CD drive, also my XSERVER problem is really annoying me and preventing me from fixing anything else because its very hard to work only in command-line interface mode since I'm a n00b at linux :D Im sorry if I'm not being very descriptive but I've made dozens of posts on other web forums and gotten little or no help so its hard to remember everything I've tried, just ask me questions and I'll be happy to provide any info that will help you help me :D thanks in advance.

---

### Post by gondilon on 2006-04-19
I had the same problem with breezy on my laptop. What is probably happening is that breezy is trying to accelerate the graphics in a way that your video card does not support.  To stop this, you need to edit the file/etc/x11/xorg.conf. The easiest way to do this is to got to this site: [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)
and download the program that allows you to read and write your linus partition.  After you do this, open the config file in notepad. Find the part where it names your graphics card. AT the end of that section add 'option "noaccel". Save the file and restart ubuntu.

---

### Post by Mustard on 2006-04-19
I'd start with a list of hardware you have on your desktop machine and the machine specificiation.

---

### Post by Remonster on 2006-04-19
Good plan :D 

first off I found out that I needed to mount the CD manually so that worked and I got my nvidia driver installed and am rebooting now to test if the driver helped at all, my machine specs are:

Intel Pentium D 930 overclocked to 4.21GHz
2GB DDR2 667
200GB SATA drive with Ubuntu on it, 300GB SATA with Windows XP
eVGA 7900GTX graphics card

any other specs you guys need?

Also I just rebooted and the drivers didnt fix it :(

---

### Post by stuporglue on 2006-04-19
OK...

LAN -- Two possibilities: 
1) Drivers is loaded, but card not configured
2) Drivers not loaded (and possibly 1 as well). 

Try using nano or pico or vim or whatever you like to edit the file "/etc/network/interfaces".

$ sudo nano /etc/network/interfaces
Make sure it has these two lines: 
auto eth0          <------ Auto start eth0 at boot (I think...)
iface eth0 inet dhcp   <------ interface eth0 is an internet device configured with dhcp

Note: the lines with "lo" stay!

Cdrom:

Sounds like automounting isn't working. For now mount manually...it'll probably "just work" once you get the graphics up (I think some services haven't started correctly). 

mount CDs like this

sudo mount -t 6990 /cdrom 

Maybe that will only let the super user access the disk, but that's good enough for system recovery. Umount with "sudo umount /cdrom"


graphics:
Find what kind of graphics card you have by running "lspci | grep VGA". Then run "sudo dpkg-reconfigure xserver-xorg" and choose the options that fit your system. Worry about getting the official Nvidia drivers afterwards. 



Hopefully that'll get you started anyways. Once you have the network and some graphics, it'll be easier to fix/tweak the settings. BTW. Did the install seem to go right? That's a lot of stuff that didn't work out of the box.

---

### Post by Remonster on 2006-04-19
Lol the install went very smoothly, if you check my above post (looks like you were typing your response when I typed it) I 'fixed' the CD rom, also I'm not sure if my network is connected to eth0 or eth1 but I think its eth1 (my mobo is an Asus P5WD2-E Premium and as such it has dual 10/100/1000 ethernet ports).

---

### Post by Remonster on 2006-04-19
Well here's a nice little bundle of joy, after rebooting and getting an error about XSERVER as usual, I look at the error log and it says:

>  (EE) Failed to load module "glx" (a required submodule could not be loaded, 0)
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.


....that can't be good.

---

### Post by Remonster on 2006-04-19
In my xorg.conf file, under "drivers" I have "nvidia" is this correct for the Nvidia 8756 drivers? Could that be why they are not loading?

---

### Post by Mustard on 2006-04-19
I would switch back to vesa drivers while you work out what it wrong with the nvidia setup.  At least then you have a gui to work with.

Can you give more detail on where you got these drivers, why you needed to use this particular version of the drivers, and how you installed them?

---

### Post by brentoboy on 2006-04-19
sudo apt-get install nvidia-glx

that is the nvidia driver in the repo
then your existing xorg.conf should work

/etc/init.d/gdm restart
(to restart your graphical desktop)

---

### Post by Tumdian on 2006-04-19
make sure to uncomment your sources.list file 1st.

---

### Post by Remonster on 2006-04-19
I'd love to try out all of your sound suggestions but I need to seed some torrents for a few days so I won't be able to try them out until this weekend, however I can tell you guys that with the nvidia-glx drivers I still could not get XSERVER to work.

---

### Post by sorrow777 on 2006-05-23
even the latest drivers from nvidia doesn't list our (7900gtx) cards as a supported card.... check the driver docs.  I'm having the same problem.  I was able to get it to work, but then after a reboot it was hosed again. ):

---

