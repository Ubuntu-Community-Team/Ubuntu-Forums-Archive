---
title: "Ubuntu does not like video card in permanent - no problem in safe mode"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by rrsodl on 2008-01-24
As I posted in another thread, I am running ubuntu 710 from a USB pendrive.

The problem that I have now is that I can run it OK if I bootup in safe mode, but I cannot make permanent any configuration which means I would have to re-configure every time I run ubuntu.

I tried to hit F4 and use the same resolution used by graphics safe mode and then use the permanent option to book ubuntu but when it boots up and the desktop is shown the screen is all distorted and I cannot do anything from there.

Is there anything I could do?


Also, the live CD has exactly the same behavior.

Rick

---

### Post by blueridgedog on 2008-01-24
Can you get to a terminal and try:
```

sudo dpkg-reconfigure xserver-xorg
```

---

### Post by rrsodl on 2008-01-25
Hi,

thanks for replying.

Unfortunately I can't, I cannot see enough to find my wave to the menu and open a terminal, unless there is a key combination that can achieve that without going through the menus.

The weird thing is that running a non permanent option is ok, but whatever changes I might make they will not save - I don't know if that applies to commands issued in a terminal. I think I will try that, I will boot in graphics save mode, try the command you just gave me and then try to reboot the permanent option.

I will post my results here :)

Thanks

Rick

---

### Post by RomeReactor on 2008-01-25
Hi. What video card do you have? With regard to opening the terminal without using the menus, you can press ALT+F2 and type or paste:
```
gnome-terminal
```
However, to run the dpkg-reconfigure command, you need to shut down GDM; press CTRL+ALT+F1 to switch to a terminal, log in if asked to, then run:
```
sudo /etc/init.d/gdm stop
```
Now, make a backup of your current configuration (always a good thing to do):
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
then you can run dpkg-reconfigure:
```
sudo dpkg-reconfigure xserver-xorg
```
Accept all the defaults for now; once it finishes, you should be brought to your desktop. If you're not, run:
```
sudo /etc/init.d/gdm start
```

If after this, you want to restore your previous configuration, again open a terminal and run:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
then press CTRL+ALT+BACKSPACE to restart the display.

---

### Post by rrsodl on 2008-01-25
Hi,

Thanks for replying.

I've attached a screen shot of my video seen by ubuntu.... ubuntu sees the card as a RV280 Radeon 9200 Pro while Windows see it as a Radeon 9250 :confused:

I did try the command line sudo pk-reconfigure.... and it did saved the configuration but made no difference, I still cannot boot up in anything but save graphics mode.

 I will follow the last advice now "However, to run the dpkg-reconfigure command, you need to shut down GDM; press CTRL+ALT+F1 to switch to a terminal, log in if asked to, then run:" 

I will report how I get on with that.


Again, your help in very much appreciated.

Rick

---

### Post by RomeReactor on 2008-01-25
Can you give us more information about your system--CPU, RAM, etc? Also, were you running the LiveCD when you took the screenshot, or did you take it while running Ubuntu from the USB? In your screenshot, you're identified as a **Live session user**, which probably means you don't have a user set up, and are running Ubuntu as a 'Live CD', which would in turn explain why the changes aren't being stored. Have you tried this [wiki page]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent"), this [thread]("http://ubuntuforums.org/showthread.php?t=71567"), or this [tutorial]("http://www.pendrivelinux.com/2008/01/11/run-ubuntu-710-from-windows/")?

---

### Post by rrsodl on 2008-01-25
> **RomeReactor said:**
> Can you give us more information about your system--CPU, RAM, etc? Also, were you running the LiveCD when you took the screenshot, or did you take it while running Ubuntu from the USB? In your screenshot, you're identified as a **Live session user**, which probably means you don't have a user set up, and are running Ubuntu as a 'Live CD', which would in turn explain why the changes aren't being stored. Have you tried this [wiki page]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent"), this [thread]("http://ubuntuforums.org/showthread.php?t=71567"), or this [tutorial]("http://www.pendrivelinux.com/2008/01/11/run-ubuntu-710-from-windows/")?


OK, I did all the steps from the previous message but no luck :(

At the end of the configuration the sytem came back with @ There already appear to be an x server running on display :0 - Should another display No tried?

I said NO but it came back with the same message. I said Yes and the screen went blank and I had to reboot.

Now, the screen shot from before was taking while running Save Graphics mode on the USB.


The following screen shot is taken from the same environment.

The processor is an Athlon Septrom 3000 - about 1.8 Mhz
1 GB of Ram
a 200 GB Sata Seagate HD

The video card is a Radeo 9250 - 250 GB RAM - AGP interface.

No, I have not created any account as yet - and you might be right in thinking that could be the reason no changes are being stored. I will get on it right away :)

I will read the links you gave me .

Thanks a lot for all the help.

P.S.

I read the links but I have already done that - the problem is that I cannot run the permanent option now :(

I prepared the USB by creating a primary and extended partition. formated them ... and installed Ubuntu 710. 




Rick

---

### Post by rrsodl on 2008-01-26
I followed the advised steps yesterday, stop the GDM, reconfigure xserver, re-start GDM. Unfortunatelly it made no difference.

I then created a new user, logged in as the new user and followed the steps mentioned above - but nothing - no change - the user I had created is not there, all changes I make are deleted :confused:


Any more ideas? 


Thanks in advance.


Rick

---

### Post by rrsodl on 2008-01-27
Today I tried to do a little more investigation on why nbuntu does not boot in permanent mode.

It appears that it detect my video card correctly, well, /media/casper-rw/etc/X11/xorg.conf contains the line ATI Radeon 9200 Pro and yet it fails to display the desktop correctly, on the other hand, when  booting under Safe Graphics mode, the xorg.conf file says Generic Video Card - Vesa. :confused:

I tried to edit the file, and also to copy the version used by Safe Graphics Mode but the system complains about other things. Is there a way to make permanent configuration changes when not booting in permanent mode?

Is there anything I'm doing wrong?

Thanks in advance


Rick

---

