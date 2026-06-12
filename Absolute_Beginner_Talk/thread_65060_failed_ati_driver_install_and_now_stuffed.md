---
title: "failed ati driver install and now stuffed"
date: 2005-09-12
forum: Absolute Beginner Talk
---

### Post by thepcdoctor on 2005-09-12
Ok...I read the dozens of posts about installing ati drivers and the countless problems people have had. Because there is no one definitive method to get this to work it's confusing for a noob to say the least.  This is the instructions I followed:

1. sudo apt-get install xorg-driver-fglrx

2.echo fglrx | sudo tee -a /etc/modules  
This command won't have any effect until you reboot. To load the kernel module immediately, run sudo depmod -a ; sudo modprobe fglrx, but this will only work if you have already rebooted since upgrading the kernel. If it doesn't work, perform the next step (below) and then reboot.
 3. Edit /etc/X11/xorg.conf and change "ati" to "fglrx" ...or use sudo dpkg-reconfigure xserver-xorg and select "fglrx" instead of "ati". 

So I changed ati to fglrx restarted PC and now Ubuntu won't boot and I'm stuck at the command prompt and have no idea how to sort out this mess!


Help!

---

### Post by poofyhairguy on 2005-09-12
[QUOTE=thepcdoctor]
So I changed ati to fglrx restarted PC and now Ubuntu won't boot and I'm stuck at the command prompt and have no idea how to sort out this mess!


Help![/QUOTE]

Use the 

> sudo dpkg-reconfigure xserver-xorg

Command. Pick the "ati" driver whent you have the choice to get a working desktop again.

---

### Post by thepcdoctor on 2005-09-12
Thanks, but I'm still stuck at the command prompt. How can get back to the desktop?

---

### Post by thepcdoctor on 2005-09-12
ok...delete last post...got it.

but can someone please tell me how to install the driver for ATI 9800pro card? I'm still running the mesa. It shouldn't be this complicated to set up what amounts to basic functionality for an OS.

I've downloaded the installer from ATI website but not sure if this is the best way to go. In any case I can't even run it.
theboss@ubuntu:~$ sudo /home/theboss/Desktop/ati-driver-installer-8.16.20-i386.run
sudo: /home/theboss/Desktop/ati-driver-installer-8.16.20-i386.run: command not found
theboss@ubuntu:~$ sudo ./home/theboss/Desktop/ati-driver-installer-8.16.20-i386.run
sudo: ./home/theboss/Desktop/ati-driver-installer-8.16.20-i386.run: command not found

---

### Post by atrus325 on 2005-09-12
[QUOTE=thepcdoctor]ok...delete last post...got it.

but can someone please tell me how to install the driver for ATI 9800pro card? I'm still running the mesa. It shouldn't be this complicated to set up what amounts to basic functionality for an OS.[/QUOTE]

You have unfortunately stumbled on one of the trouble spots I, personally, have had with Linux, that being the ATI drivers.  My laptop is running an ATI Xpress 200m, and I spent a great deal of time working on this before finally learning that I the current driver wouldn't work.  An older driver, however, would.

So, I'm basically telling you two things.  One, ATI doesn't make things as easy (or at least quite as easy as Nvidia).  Two, you might have to experiment a bit.  Have you searched the forums or Google to find out if anyone has worked with this specific card and Ubuntu yet?  

I bet this thread might be some help: [http://www.ubuntuforums.org/showthread.php?t=24557&page=1&pp=10&highlight=ATI+9800pro](http://www.ubuntuforums.org/showthread.php?t=24557&page=1&pp=10&highlight=ATI+9800pro)

J.

---

### Post by atrus325 on 2005-09-12
try 

$ sh ati-whateverthefilenameis.run

J.

---

### Post by poofyhairguy on 2005-09-12
[QUOTE=thepcdoctor]
but can someone please tell me how to install the driver for ATI 9800pro card? I'm still running the mesa. It shouldn't be this complicated to set up what amounts to basic functionality for an OS.
[/QUOTE]

Yeah. ATI's poor support is why I have a 6600 GT now. But before I switched I did get my ATI card to finally work. Here is how:

[http://www.ubuntuforums.org/showpost.php?p=122362&postcount=6](http://www.ubuntuforums.org/showpost.php?p=122362&postcount=6)

---

### Post by thepcdoctor on 2005-09-13
"1. download official driver .rpm from ATI
2. remove fglrx packages using Synaptic [COLOR=DarkOrange](How?)[/COLOR]
3. shut down Gnome (terminal: sudo /etc/init.d/gdm stop)
4. cd to download-location
5. sudo alien fglrx_ ... .rpm ([COLOR=DarkOrange]what's the ...?[/COLOR]
6. sudo mv /lib/modules/YOURKERNELVRSIONHERE/kernel/drivers/video/fglrx.ko $HOME
7. sudo dpkg --force-overwrite -i fglrx- ... .deb ([COLOR=DarkOrange]what's the ...?[/COLOR])
8. cd /lib/modules/fglrx/build_mod
9. sudo sh make.sh
10. cd /lib/modules/fglrx
11. sudo sh make_install.sh
12. sudo modprobe fglrx
13. sudo fglrxconfig
Note: before you start check if you have installed the linux-headers for your kernel and gcc (Synaptic)" ([COLOR=DarkOrange]how do you do that?)[/COLOR]

Is this really the simplest way to install a basic set of drivers??  I can already see the nightmares when the installation goes pearshaped.

---

### Post by atrus325 on 2005-09-13
Synaptic is your default GUI frontend for apt-get.  To get into it, you just need to enter Package Management and select Advanced.  You can do a search for fglrx and uncheck it.  It will then uninstall.  Search for whatever else you need to install and just check it.

I've never used the alien command before.  I guess it's just a .rpm installer.  I see no reason why your .run file wouldn't work rather than the .rpm, but might as well follow the guide.

J.

Edit:

> Is this really the simplest way to install a basic set of drivers?? I can already see the nightmares when the installation goes pearshaped

I would have given anything to have had a guide like this when I installed my ATI card.  Like I said above, ATI is just a bit more stinkery than Nvidia.

---

### Post by Lux Perpetua on 2005-09-13
thepcdoctor - a lot of people have found this post by Epskampie helpful: 

[http://ubuntuforums.org/showpost.php?p=297524](http://ubuntuforums.org/showpost.php?p=297524)

Note - if you are installing the latest driver (8.16.20), your installer will have a different name. FWIW, I don't recommend 8.16.20; for me, it actually had *worse* performance than 8.14.13, but YMMV.

---

### Post by poofyhairguy on 2005-09-13
[QUOTE=thepcdoctor]
Is this really the simplest way to install a basic set of drivers?? [/QUOTE]

For ATI and myself yes. Its the only thing that worked. I hope it helps you too.

---

