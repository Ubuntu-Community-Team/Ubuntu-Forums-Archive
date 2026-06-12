---
title: "Screen Flickering, Mouse configuration, screen refresh rate and other problems"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by johnation33 on 2007-10-30
Hey everyone,

So I'm a new convert from windows vista to ubuntu 7.10, but I'm having lots of problems that's not letting me enjoy this as much, can someone help me?

First, I have a really annoying screen flickering, I checked another thread and someone mentioned that it might have to do with incorrect vsync and hsync settings and that I should probably look for my monitor's settings? The problem is, I don't know where to find this, I have a vaio sz with an LED screen at res 1280x800 but that's all I know. I tried to click "detect" on the screen settings under system, but it creates a new item called "plug n play" and has no values for resolution or refresh rate so I'm guessing its a broken feature. Does anyone have answer for this? It's very annoying and makes this unusable.

Second, does anyone know how to set the screen resolution and the refresh rate correctly? It seems everytime I use "Screen & Graphics" setting in the administration panel, It won't let me select a refresh rate higher than 53. I'll post my config file here:

```
Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8400M GS]"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 2560x1600"
	Horizsync	31.5-99.0
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
  modeline  "2560x1600@60" 348.16 2560 2752 3032 3504 1600 1601 1604 1656 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8400M GS]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	2560	1600
		Modes		"1280x800@60"	"1440x900@60"	"1280x720@60"	"1600x1024@60"	"1280x768@60"	"1680x1050@60"	"800x600@60"	"1920x1200@60"	"800x600@56"	"2560x1600@60"
	EndSubSection
EndSection
```

Is the section for the monitor configurations supposed to be this long?

Third, I'm having problems with my mouse. I can't set any of the programming buttons on my razer copperhead mouse. I remember downloading some emulated driver for the mouse from sourceforge, but I don't know how to open that up. Can anyone help me in setting the programming for each of its buttons?

Fourth, how do I have the desktop cube from compiz fusion? (I am correct in assuming that beryl is merged with compiz fusion so beryl is no longer updated right?) I enabled the config manager but I only get a two-sided cube after I do ctrl-alt-lclick

Fifth, how do I get/install the themes for compiz fusion? I really like the glass theme that looks very much like vista but I don't know where to get a list of themes etc.

Sixth, what is the most popular/dominant music manager for ubuntu? I really miss itunes but I'm perfectly willing to find a replacement.

Seventh, how do I unmount a hard drive partition from my desktop? It mounts one of my partitions that is a recovery partition, and when i try to unmount it, it says I don't have permissions. However, for other administrative tasks, it pops up a password prompt, so why doesn't it happen for this?


Sorry I am such a newbie at this, but I think I'll grow to learn to love linux very much. I'm already very impressed.

-John

---

### Post by juantovarm on 2007-10-31
As for questions 1 and 2 regarding your monitor, you could run this in the terminal, it will reconfigure your screen, mouse, keyboard, just follow the steps:

sudo dpkg-reconfigure -phigh xserver-xorg

for question 4, you have to install "ccsm" aka "advanced desktop effect settings" in add/remove, there you can add whatever effects you like. Under "general" there is a tab where you have to set the number of desktops to 4  in order to have the four sides of the cube

Question #5 i think you are referring to emmerald, that is the theme manager

Question # 6, i use amarok for sound and kaffeine or vlc for video, i find they are the best

Question # 7 you have to be root or have root priviledges to unmount a filesystem that is owned by root. The easiest way is to do it by the command line: 

sudo umount nameofpartition (usually /dev/nameof partition) you need to know what is the name of your partition, so you could type these commands in the terminal and post their outputs

pico /etc/fstab

and 

sudo lshw -C disk

as for q#3 i have no idea what kind of mouse that is, sorry, but if you have the source tar ball, it's pretty easy to install IF you have all the dependencies met, In the terminal: 
1- simply untar your files: tar -xvf nameofpackage (you have to be in the directory where the package is to do it, you can go there by typyng cd /nameofdirectory)
2- go to the folder just created by typing cd /nameoffolder
3- type : sudo ./configure
4- type: make
5- type: sudo make install

the first dependency is always build-essential in the terminal:
 sudo apt-get install build-essential

if you find a .deb package is a lot easier, just double click on it and i't ready, if you have an rpm package, it's also easy, not as much as a deb but, it's easy


hope it helps
juan

---

### Post by alienexplorers on 2007-10-31
First thing you should do is set up your restricted video card drivers.

---

