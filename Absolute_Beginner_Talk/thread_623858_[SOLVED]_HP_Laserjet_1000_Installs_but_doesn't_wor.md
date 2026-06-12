---
title: "[SOLVED] HP Laserjet 1000: Installs but doesn't work"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by machavillain on 2007-11-26
I plug it in to Gutsy...it is auto-recognized and appears to be good to go. I am impressed*. Then when I try to print, I get a pop-up that "Laserjet 1000 may not be connected." I then installed foo2zjs as instructed at [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) - still no dice.

Any ideas?

*Because it took me half an hour to set up on my gf's XP laptop.

---

### Post by edwardLS on 2007-11-26
I may be able to help since I have three HP Printers on my Ubuntu network.

How is the HP Laserjet 1000 connected to your computer?  Is it Network connected? or USB connected?

---

### Post by machavillain on 2007-11-26
Thanks for the reply. It is USB connected.

---

### Post by LowSky on 2007-11-26
try this website out
[http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

---

### Post by christina_svats on 2007-11-26
Type the following in a terminal: 

 wget [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)

 tar xzvf foo2zjs.tar.gz

 cd foo2zjs

 make

 ./getweb 1000

 sudo make install

 sudo make install-hotplug

and then switch off your printer and reboot

It worked for me but I should say that I sometimes have to wait for half a minute or so from the moment I  send the page until it actually prints...

I hope it helps

---

### Post by machavillain on 2007-11-26
Will either I of these things prevent me printing from Windows? (I see firmware mentioned).

---

### Post by christina_svats on 2007-11-26
No it won't, as far as I know and have tested. Didi it work anyway?

---

### Post by stchman on 2007-11-27
I ahve my LJ1000 hooked up via USB and it runs flawlwssly.  Try my procedure.

[http://www.stchman.com/foo2zjs.html](http://www.stchman.com/foo2zjs.html)

Also leave the printer on all the time.

---

### Post by machavillain on 2007-11-28
Stchman: should I have the printer plugged in while I run this?

---

### Post by machavillain on 2007-11-28
Stchan: I ran your script, but CUPS didn't load at the end. Everything else seemed fine.
------
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
sudo: gnome-cups-manager: command not found
if [ -x /etc/init.d/cups ]; then \
            /etc/init.d/cups restart; \
        elif [ -x /etc/rc.d/rc.cups ]; then \
            /etc/rc.d/rc.cups restart; \
        elif [ -x /etc/init.d/cupsys ]; then \
            /etc/init.d/cupsys restart; \
        elif [ -x /etc/init.d/cupsd ]; then \
            /etc/init.d/cupsd restart; \
        elif [ -x /usr/local/etc/rc.d/cups.sh ]; then \
            /usr/local/etc/rc.d/cups.sh restart; \
        elif [ -x /usr/local/etc/rc.d/cups.sh.sample ]; then \
            cp /usr/local/etc/rc.d/cups.sh.sample /usr/local/etc/rc.d/cups.sh; \
            /usr/local/etc/rc.d/cups.sh restart; \
        fi
 * Restarting Common Unix Printing System: cupsd                         [ OK ]

---

### Post by stchman on 2007-11-28
> **machavillain said:**
> Stchan: I ran your script, but CUPS didn't load at the end. Everything else seemed fine.
------
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
sudo: gnome-cups-manager: command not found
if [ -x /etc/init.d/cups ]; then \
            /etc/init.d/cups restart; \
        elif [ -x /etc/rc.d/rc.cups ]; then \
            /etc/rc.d/rc.cups restart; \
        elif [ -x /etc/init.d/cupsys ]; then \
            /etc/init.d/cupsys restart; \
        elif [ -x /etc/init.d/cupsd ]; then \
            /etc/init.d/cupsd restart; \
        elif [ -x /usr/local/etc/rc.d/cups.sh ]; then \
            /usr/local/etc/rc.d/cups.sh restart; \
        elif [ -x /usr/local/etc/rc.d/cups.sh.sample ]; then \
            cp /usr/local/etc/rc.d/cups.sh.sample /usr/local/etc/rc.d/cups.sh; \
            /usr/local/etc/rc.d/cups.sh restart; \
        fi
 * Restarting Common Unix Printing System: cupsd                         [ OK ]
List the command you used to run the script.

Your command should have looked like this.  This assumes you are trying to install a Laserjet 1000.  If your printer is different then you need to cosult the chart.  The script should be in your home directory.  Also make sure you are hooked up to the internet while the script is running.

```

sudo ~/ubuntu_foo2zjs_install.sh 1000
```

I used this command and script to install the driver.

---

### Post by machavillain on 2007-11-28
Used the same command...no dice.

---

### Post by stchman on 2007-11-28
> **machavillain said:**
> Used the same command...no dice.

I was looking at your output and do you have gnome-cups-manager installed?  To verify this type the following:

dpkg -l | grep gnome-cups-manager

If you get nothing then you will need to install gnome-cups-manager

```
sudo apt-get -y install gnome-cups-manager
```

It should be installed by default.

Also, are you running Gnome or KDE?

---

### Post by machavillain on 2007-11-28
I think this is the problem:
# On Ubuntu 5.10/6.06/6.10/7.04, run "gnome-cups-manager"
# On Ubuntu 7.10, run "system-config-printer".

---

### Post by stchman on 2007-11-28
> **machavillain said:**
> I think this is the problem:
# On Ubuntu 5.10/6.06/6.10/7.04, run "gnome-cups-manager"
# On Ubuntu 7.10, run "system-config-printer".

The package gnome-cups-manager is located in the universe repository in Gutsy.  To install this package make sure the universe repository is enabled.  You can then 

```
sudo apt-get -y install gnome-cups-manager
```

See if that does the job.

Edit:  I did some reading and indeed it is system-config-printer

The script needs to be changed.

---

### Post by machavillain on 2007-11-28
So I finally got this to work, not by using gnome-cups-manager, but simply by removing the printer and then manually re-adding it (as opposed to the autodetect).

Whether this is a Ubuntu feature, or because I've now downloaded and tried to install drivers, you tell me....

And of course, thank you everyone for your help!

---

### Post by stchman on 2007-11-28
Here is the proper script for Gutsy.  Give the script executable privelages and run it.

I had to change the gnome-cups-manager to system-config-printer.

---

### Post by shanerdaner on 2007-12-03
> **stchman said:**
> Here is the proper script for Gutsy.  Give the script executable privelages and run it.

I had to change the gnome-cups-manager to system-config-printer.


How do I make it executable?  Just wondering I need my printer to work!  Thanks!!

---

### Post by LowSky on 2007-12-03
HP has mad a driver utility that make the printer work and its easy to set up

[http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

---

### Post by shanerdaner on 2007-12-03
> **LowSky said:**
> HP has mad a driver utility that make the printer work and its easy to set up

[http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)It still didn't work :(

---

### Post by shanerdaner on 2007-12-03
> **shanerdaner said:**
> It still didn't work :(

After installing it I cannot see my USB printer.......

---

### Post by stchman on 2007-12-03
> **shanerdaner said:**
> How do I make it executable?  Just wondering I need my printer to work!  Thanks!!

```
chmod 755 <script>
```

---

### Post by tdmoore on 2007-12-06
Christina,

You are a godsend!!!!

Your commands worked perfectly although I had to delete the 1000, then reinstall it and choose the last driver on the list (PPD).

Thanks again...another example of the fine people on this forum!

---

### Post by joy pabuhat on 2008-05-09
Hi ubuntu forums. I am just new to linux. I am using the live cd now. My HP laserjet 1000 printer is already installed the problem is could not make any printout. Had downloaded the foo2zjs.tar.gz the problem is i don't understand the language as I am used to Windows installation process. I don't even know how the installation goes at linux. Maybe you can help me sort this out. thanks in advance

---

### Post by drs305 on 2008-05-09
I have a LJ1000 working in hardy, so we can get it working. 

First, are you using hardy?

Second, is it a usb printer?

The attached picture shows my setup. Note the Device URI: usb://HP/LaserJet%201000 
If your LJ1000 is a usb printer, sometimes the address automatically selected doesn't work and the printer is recognized but won't print. That was one of my problems back in feisty or gutsy. The address above solved that.

If that doesn't work or isn't your problem and you want to install the foo2zjs files, follow the steps in post #5. Before you begin, you might check synaptic to see if the foo2zjs files are already installed. The unbuntu files are supposed to work but the writer of the files you downloaded with the wget command says not to use the ubuntu foo2zjs files. If they show installed in synaptic, uninstall them before following the commands in these posts. You can always restore them later if necessary.

You may find a more detailed explanation in post #9 at [http://ge.ubuntuforums.com/showthread.php?t=774414#9](http://ge.ubuntuforums.com/showthread.php?t=774414#9). If you follow that post, change step 
6 to ./getweb 1000 and stop after step 9 (you shouldn't need the last 2 steps). Repower your printer to see if it works now. All the commands will be run in terminal, so all you have to do is copy each command into a terminal window and hit enter for each one. You should start in the same directory as the downloaded foo2zjs file, probably ~/Desktop or ~

---

### Post by frbe0101 on 2008-06-18
I have Hardy i did the fixes before and the printer worked, but just today I got some update and now the printer does not work, I tried everything all over again and nothing works. My other printer (HP Desktop D1430) works but not this one. :(

---

### Post by frbe0101 on 2008-06-19
Never mind I solved it. It seems the standard version of HPLIP (2.8.2) was conflicting with the new version downloaded from HP (2.8.5) so removing HPLIP using Synaptic fixed the problem.

---

