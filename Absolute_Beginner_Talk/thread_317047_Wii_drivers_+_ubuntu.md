---
title: "Wii drivers + ubuntu"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by ceaseoleo on 2006-12-11
Hi
Just wondering if anyone has gotten the wii drivers to work on ubuntu yet.  here is the link [http://www.wiili.org/index.php/WMD]("http://www.wiili.org/index.php/WMD")
I will attempt this, and if I get it working will post a how to.  i wanna  [wii-mote saber]("http://www.engadget.com/2006/12/11/wiisaber-star-wars-kid-do-your-thing/") too .  :) .  Thanks

---

### Post by troymcdavis on 2007-01-06
There are multiple drivers for the Wiimote in both Linux and Windows. The most comprehensive site I've seen is [WiiLi]("http://www.wiili.org/index.php/Main_Page"). Their goal is to make a Linux distribution to install on the Wii, but they also have links for installing the Wiimote on your computer. [Here's a video of a Wiimote with Ubuntu and Beryl]("http://www.youtube.com/watch?v=ALqduQfm09c"). It's just a bluetooth device, so if you have bluetooth working, you don't really need "drivers" *per se*, it's just a matter of manipulating the data the Wiimote returns.

---

### Post by Acapulco on 2008-02-05
I  connected my Wii in Ubuntu using WMD without much hassle. 

Instructions here [http://www.circuitdb.com/articles/7/3]("http://www.circuitdb.com/articles/7/3")

Unfortunately I haven't been able to find suitable forums for WMD discussion as I would like to develop on top of that. For instance, how can I turn the Wiimote LEDs on and off?

---

### Post by UBfusion on 2008-02-15
I just tried today on Gutsy amd64 and both WMD and the Wmgui application that you can get via Synaptic work.

To save you from some frustration, if you want to try WMD using the howto from [http://www.circuitdb.com/articles/7/3](http://www.circuitdb.com/articles/7/3), make sure that:

1. you have edited **Config.py** like this: (taken from the french forum [http://gueux-forum.net/lofiversion/index.php/t137087.html):](http://gueux-forum.net/lofiversion/index.php/t137087.html):)

```
## Next, I will choose which IO Modes I want to use
## for sending keypresses, clicks, mouse movements and gestures
## *ATTENTION YOU SHOULD NOT EXPECT ANYTHING TO WORK IF YOU CHANGE IO_MODES OR IO_CHANNELS SETTINGS IN ANY WAY
'IO_MODES': {          # SET TO TRUE IF YOU HAVE:
  'UINPUT': True,     ## the uinput kernel module loaded.
  'XLIB': False,       ## python-xlib with the buffer overflow patch.
  'X_EVDEV': False,    ## evdev_drv and a customized xorg.conf.
  'PYOSD': False
},
```

and

```
## If I'm using IO_MODES['UINPUT'] I'll need to
## Set the path of my uinput device
##
#'UINPUT_DEV': "/dev/misc/uinput",
'UINPUT_DEV': "/dev/input/uinput",  ##ubuntu - you need to modprobe uinput first
#UINPUT_DEV: "/dev/uinput",
```


2. you are able to connect with the wiimote using sudo hidd --search

3. you are **disconnected** from the wiimote when running sudo python WMD.py

According to my little experience posted in [http://www.wiili.org/forum/bluetoothbluetootherror-(111-connection-refused)-t1693.html](http://www.wiili.org/forum/bluetoothbluetootherror-(111-connection-refused)-t1693.html), if you take the circuitdb guide literally and try to first connect and then run WMD, you will get an error (bluetooth.BluetoothError: (111, 'Connection refused')). So just let WMD do the connection for you. Hope this helps - we need more applications of wiimote in ubuntu!

@Acapulco: Wmgui can control the 4 wiimote LEDs independently.

---

### Post by zutronius on 2008-03-01
Has anyone had any luck getting the Wii Wireless device to work with Ubuntu? I tried to install the cd with WINE and i got an invalid operating system error.

---

