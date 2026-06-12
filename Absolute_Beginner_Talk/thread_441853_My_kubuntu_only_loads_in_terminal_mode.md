---
title: "My kubuntu only loads in terminal mode"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by kurishiiu on 2007-05-13
This has been an ugly week in my Ubuntu experience. I formatted my hard drive by mistake losing important info, then i installed kubuntu. I setup my desktop, i installed a window decorator, when i reloaded the system, the only possible configuration was 640x400.

I found the instructions to set up my Intel G82865 card in a spanish forum [http://www.ubuntu-es.org/index.php?q=node/47127]("http://www.ubuntu-es.org/index.php?q=node/47127"), i followed them step by step, and now my system charge the bootsplash and then it gets stuck in the command mode... no kde, no desktop, no graphic enviroment, no nothing, just the terminal.

Please someone let me know how to load the graphic enviroment from that terminal screen or how to recover the desktop i will really appreciate it

I need to have my computer back to normal by monday... :(

---

### Post by taurus on 2007-05-13
What happens when you run this command from a prompt?

```
startx
```

---

### Post by kurishiiu on 2007-05-13
I will need to check tomorrow morning as soon as i get to the office, i will let you know

thanks

---

### Post by kurishiiu on 2007-05-14
when I type startx it says

(==) log file:"/var/log/Xorg.0.log" Time mon May 08:48:47 2007
(==) Using config file : "/var/x11/Xorg.conf"
(EE) Intel (0) detecting sil164
(EE) Intel (0) Unable to read from DV0I2C_E Slave 112
(EE) Intel (0) detecting ch7xxx
(EE) Intel (0) Unable to read from DV0I2C_E slave 236
(EE) Intel (0) DDC Analog 0,  00005010
(EE) Intel (0) DDC DV0 1, 0000501c

Executing (ax== 0x5f01 BIOS call at /../src/i830_driver.c:617
Fatal server error
No modes found on either pipe
XIO: fatal IO ERROR 104 (connection reset by peer) on x server ":0.0" after 0 request (0 known processed) with 0 events remaining

---

### Post by taurus on 2007-05-14
Reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by kurishiiu on 2007-05-14
thanks,

what option would you choose?

---

### Post by taurus on 2007-05-14
If you're not sure, pick the default and use vesa driver for your graphic card for now until you get X up and running again.  Then, you can install the right driver for you card.  However, you can use i810 for your Intel graphic card.

---

### Post by kurishiiu on 2007-05-14
thaks a lot man, I'll give it a try and then i'll let you know

---

### Post by kurishiiu on 2007-05-14
> **taurus said:**
> If you're not sure, pick the default and use vesa driver for your graphic card for now until you get X up and running again.  Then, you can install the right driver for you card.  However, you can use i810 for your Intel graphic card.

You are the best!! At last!! I chose I810, kept pressing *ok* 'til the end (not pretty sure what i did), then I selected the resolutions  and now the suffering is gone, my Kubuntu loads fine and i see a beautiful 1280x1024 screen. 

It seems the codes to install the drivers did not send the files where they were supposed to go, I have a couple of folders in my home folders called "mesa" and xf86-video-intel. Maybe that is why the Intel option does not find anything and sends you to the terminal hole.

Could you please let me know how to install those drivers where they are belong and tell me what MESA is?

The original code i typed is this:
> 
sudo apt-get install git-core
git-clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel
git-clone git://anongit.freedesktop.org/git/mesa/mesa
sudo apt-get install xserver-xorg-video-intel
sudo apt-get remove 915resolution
sudo dpkg-reconfigure -phigh xserver-xorg
    select intel and then the resolution


---

### Post by kurishiiu on 2007-05-15
Taurus, do you know how i can install those drivers where they belong? my kubuntu is getting frizzed  all the time

---

### Post by taurus on 2007-05-15
Well, you can try something like

```
sudo aptitude update
sudo aptitude install xserver-xorg-video-intel
```
Then reboot.  [-o<

---

