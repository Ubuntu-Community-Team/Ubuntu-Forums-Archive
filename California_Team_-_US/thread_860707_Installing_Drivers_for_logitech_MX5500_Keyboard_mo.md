---
title: "Installing Drivers for logitech MX5500 Keyboard mouse combo"
date: 2008-07-15
forum: California Team - US
---

### Post by super-panik on 2008-07-15
I was wondering if someone had the drivers for this setup, on Ubuntu

---

### Post by sdlyr8 on 2008-07-20
I too just got the mx5500 and have hardy haron. Has anyone gotten the special features to work correctly?

---

### Post by stanna on 2008-10-01
i myself have this keyboard, not that the special functions are all that snazzy or important, im still interested if its possible..

---

### Post by Vargas on 2008-11-28
I'm about to buy this keyboard on Amazon.
Anyone had any functionality issues with this keyboard/mouse?
I read some things about the numpad

Also, anyone got the special features to work?

---

### Post by grantbow on 2008-12-01
I don't have this keyboard or mouse but I found these links that are somewhat related.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291269](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291269)

[http://ubuntuforums.org/showthread.php?t=890118](http://ubuntuforums.org/showthread.php?t=890118)

[http://www.xpmediacentre.com.au/community/other-hardware-vista/33605-logitech-bluetooth-mx5500-mouse-problem-fixed.html](http://www.xpmediacentre.com.au/community/other-hardware-vista/33605-logitech-bluetooth-mx5500-mouse-problem-fixed.html)

[http://fedoraforum.org/forum/showthread.php?p=1109907](http://fedoraforum.org/forum/showthread.php?p=1109907)

---

### Post by miesnerd on 2009-08-22
hey guys i have the MX5500 and I love it.
I'm wondering though, is there any way that is known (even if its difficult) to get the lcd display screen at the top of the keyboard to work?

Thanks!

---

### Post by Vargas on 2009-08-23
> **miesnerd said:**
> hey guys i have the MX5500 and I love it.
I'm wondering though, is there any way that is known (even if its difficult) to get the lcd display screen at the top of the keyboard to work?

Thanks!
Quite a good question
Unfortunately, the complete lack of interest to support any non-windows environment from logitech is quite sad.
As far as I know, there is no way to make the lcd display work in ubuntu.
I've also yet to get the usb bluetooth dongle to work as such.

---

### Post by Stef74 on 2009-10-02
Actually there is a small solution for the LCD:
```
sudo apt-get install libnetpbm10-dev libgtk2.0-dev
wget http://download.gna.org/mx5000tools/mx5000tools-0.1.2.tar.gz
./configure
make 
sudo make install

```
if you get : *libmx5000.so.0: cannot open shared object file: *
then do : *sudo link /usr/local/lib/libmx5000.so.0.0.0 /usr/lib/libmx5000.so.0*

test beep: 
```
sudo mx5000-tool -d /dev/usb/hiddev0 -b
```

Set LCD time to current system time: 
```
mx5000-tool -d /dev/usb/hiddev0 -t now 
```

Display the name of the current user on the keyboards LCD:
```
sudo mx5000-tool -d /dev/usb/hiddev0 -n $USERNAME 
```

Change temperature unit to Celsius or Fahrenheit
```
mx5000-tool -d /dev/usb/hiddev0 -c # Celsius
mx5000-tool -d /dev/usb/hiddev0 -f # Fahrenheit

```	

See keys:
```
sudo mx5000d -d /dev/usb/hiddev0 -f
```

Tested with 9.04

---

### Post by BuayaGuy on 2009-10-31
This last post seemed like a great help - I installed all the packages, and it compiled fine. The only problem now is that I don't have a /dev/usb directory to locate my device.

I'm also using the latest Ubuntu, 9.10...did these devices change location?

---

### Post by farchumbre on 2009-11-06
i am also using 9.10.
i run it from a different directory and I always get

"Could not open device or improper device (No such file or directory)"

any ideas what might be the problem?

---

### Post by cryogenic on 2009-11-10
FYI, mine was /dev/usb/hiddev1 to get it working, but dude's instructions above (aside from that fact) worked perfectly fine. Basically do an ls /dev/usb and choose whatever the highest hiddev device you have. That should do the trick.

---

### Post by Automat2 on 2009-11-12
I tried to follow Stef74´s steps. Although I am stuck after downloading mx5000tools-...gz.

I don´t know how to execute the command ¨./configure¨

It tells me > bash: ./configure: No such file or directory


PS: I am very novice at Ubuntu. ;)

---

### Post by Denisiuk on 2009-11-22
Here is solution.

[http://translate.google.com/translate?js=y&prev=_t&hl=ru&ie=UTF-8&u=http%3A%2F%2Fdmitry-denisiuk.blogspot.com%2F2009%2F11%2Fcordless-desktop-mx-5500-revolution_22.html&sl=ru&tl=en&swap=1](http://translate.google.com/translate?js=y&prev=_t&hl=ru&ie=UTF-8&u=http%3A%2F%2Fdmitry-denisiuk.blogspot.com%2F2009%2F11%2Fcordless-desktop-mx-5500-revolution_22.html&sl=ru&tl=en&swap=1)

Original on russian: [http://dmitry-denisiuk.blogspot.com/2009/11/cordless-desktop-mx-5500-revolution_22.html](http://dmitry-denisiuk.blogspot.com/2009/11/cordless-desktop-mx-5500-revolution_22.html)

---

### Post by deece803 on 2009-11-28
um, just d/l the mx5000-tools...tar.gz but i cant unpack it? i've tried tar -zxvf (filename) but it says its not in gzip format. help?

---

### Post by Automat2 on 2009-11-29
> **farchumbre said:**
> i am also using 9.10.
i run it from a different directory and I always get

"Could not open device or improper device (No such file or directory)"

any ideas what might be the problem?

You have got the keybord connected via Bluetooth. Those instructions work only if you have the keyboard connected via USB.

Take the BT dongle out the USB port, keep it on your hand for a few seconds, plug it back in and wait until the mouse and keyboard are detected. Then, you can type the instructions on the Terminal.

They work for me. But now I have to find out the way to do it via BT.

---

### Post by Kzin on 2010-01-31
@Automat2 
To get the dongle into BT mode, you hold down the red button on the dongle while you plug it into the computer.  It then shows up as a BT device that you can pair to.
Only problem is that I couldn't pair to the kb/mouse at all, either with the dongle in BT mode or my regular BT dongle.
The MX5000 pairs fine this way, but not the 5500.  It would seem like the this is an issue w/ the kb/mouse as the same results exist for 2 different dongles and the 5000 pairs fine.
I saw some launchpad bugs with regards to this but I don't think they have been assigned yet.
While trying to pair BT the keyboard will sometimes prompt for passkey, once passkey is entered it beeps like everything worked.  It then goes back into discovery mode. Then, until you remove the batteries the KB wont prompt you for passkey again.
For the mouse, sometimes it seems like it paired fine, and the bluetooth-wizard (Set Up New Device) says it pairs, but the mouse wont work.
Have you made any progress?

---

### Post by Automat2 on 2010-06-22
@Kzin
Sorry for the delay, mate. I've been looking through other threads as well, and now I'm using Lucid (10.04).

Now I have no answer, because the keyboard only works on BT.

PS: I was using MX5000, anyway.

---

### Post by Demosthenesaus on 2010-10-17
Thanks for the tool!!!

Gettting "Could not open device or improper device (Success)" here, although I have /dev/usb/hiddev0 present (only device in /dev/usb).

Using a 3rd party USB dongle, and paired with Ubuntu generated passcode, any ideas?

---

### Post by miesnerd on 2010-10-17
the only thing I cant get to run now is the right hand keypad.
I assume this has to do with the keyboard layout, so it should be an easy fix. Any suggestions?

---

### Post by rolvo_volvo on 2010-11-27
@miesnerd:

```
numlockx off
``` did the trick for me.

---

### Post by Wolly_29 on 2011-10-22
Hello Guys

I habe a MX5500 and use Ubuntu 10.10 and have following problems:

The num works fine but when i type "123" on the numblock i get "789"
When i type "789" i get "123"

:confused:

Can you help me please?

Thx 

Kr Wolly

---

### Post by Valis667 on 2011-10-23
Go to System>Preferences>Keyboard.

When Keyboard is open go Layouts>Options. Under there you can change Numeric Keypad Layout options.

---

