---
title: "[SOLVED] Wireless trouble (New Santarosa Macbook)"
date: 2007-11-22
forum: Apple Intel Users
---

### Post by Redeyes_Gambit on 2007-11-22
}{ey everybody!

First of all, Happy Thanksgiving to all you in the states! Eat turky! Enjoy yourselves! What are you still doing on these forums?!?

Now then, to those who are still here, down to business :) . I have read the various posts in the forums on this topic, and as far as I can tell I need to use NDIS wrapper to get this card to function. I'm following [[COLOR="Red"]this[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-c9037d4dac23680f0939e488c2291413ce831ef3") tutorial, and using the driver from [[COLOR="Red"]this[/COLOR]]("http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html#4") tutorial. I get stuck on the step where it says to do:

```
sudo ndiswrapper -i bcmwl5.inf
```

It took me a sec to find the file (it's under a sub-folder "DRIVERS" that isn't in the tutorial) but once I did and executed the command, i get this:

```
driver bcmwl5 is already installed
```

well, if it's installed why isn't it working? :lol: I did blacklist the native driver with

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
``` and it returned "such and such blacklisted" so I'm guessing the blacklist worked.

Why is it saying the driver is installed already? How can I fix it? My OS is vanilla x64 Gutsy.

---

### Post by cleentrax on 2007-11-22
Mine stopped working today, after I installed the new version of gnome-system-tools, though that may be a coincidence. I have tried re-installing, but no luck.

---

### Post by Levo75 on 2007-11-22
Mine never worked. :(

Broadcom BCM4328

---

### Post by Redeyes_Gambit on 2007-11-22
Hm. Bummer. Is there a place where I can remove the current driver or force the install of the one I want?

---

### Post by cyberdork33 on 2007-11-22
did you modprobe ndiswrapper?

---

### Post by Redeyes_Gambit on 2007-11-23
Not yet. Never got to that step since the 

```
sudo ndiswrapper -i bcmwl5.inf
```

failed.

---

### Post by lvleph on 2007-11-23
I had a similar problem. (I use net8185)

My problem stemed from having some of my driver files still sitting in the /etc/ndiswrapper/net8185 folder, so I just ran sudo rm -r /etc/ndiswrapper/net8185 and then the installed worked just fine.

Try this:
```

sudo rm -r /etc/ndiswrapper/bcmwl5
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
sudo modprobe ndiswrapper 

```

---

### Post by Redeyes_Gambit on 2007-11-24
Thank you very much lvleph! That worked flawlessly. So, for the record, to get wireless working in 64 bit Ubuntu all you have to do is pop open a terminal and...

[COLOR="Sienna"][SIZE="4"]1. Blacklist the non-functional driver that comes with Ubuntu[/SIZE][/COLOR]
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

[COLOR="Sienna"][SIZE="4"]2. Install ndiswrapper-utils-1.9 (note, you must be connected to the internet for this to work)[/SIZE][/COLOR]
```
sudo apt-get install ndiswrapper-utils-1.9
```

[COLOR="Sienna"][SIZE="4"]3. Remove the non-functional folder/drivers that ndiswrapper inexplicably created (thanks lvleph, for the solution to this!)[/SIZE][/COLOR]
```
sudo rm -r /etc/ndiswrapper/bcmwl5
```

[COLOR="Sienna"][SIZE="4"]4. Make a new hidden directory in your home folder called ".wireless_driver"[/SIZE][/COLOR]
```
mkdir .wireless_driver
```

[COLOR="Sienna"][SIZE="4"]5. Change into the folder we just made[/SIZE][/COLOR]
```
cd ~/.wireless_driver
```

[COLOR="Sienna"][SIZE="4"]6. Download the 64bit Windows driver from Dell[/SIZE][/COLOR]
```
wget http://ftp.us.dell.com/network/R151517.EXE
```

[COLOR="Sienna"][SIZE="4"]7. Unzip the .exe[/SIZE][/COLOR]
```
unzip -a R151517.EXE
```

[COLOR="Sienna"][SIZE="4"]8. Change into the "DRIVER" folder that we just unzipped[/SIZE][/COLOR] (I missed this the first time, but it was in the tutorial I am basing most of these commands off of)
```
cd ~/.wireless_driver/DRIVER
```

[COLOR="Sienna"][SIZE="4"]9. Install the Windows driver with ndiswrapper[/SIZE][/COLOR]
```
sudo ndiswrapper -i bcmwl5.inf
```

[COLOR="Sienna"][SIZE="4"]10. List the currently installed drivers[/SIZE][/COLOR]
```
sudo ndiswrapper -l
```

[COLOR="Sienna"][SIZE="4"]11. Load ndiswrapper module dependencies[/SIZE][/COLOR]
```
sudo depmod -a
```

[COLOR="Sienna"][SIZE="4"]12. Add ndiswrapper to the kernel modules[/SIZE][/COLOR]
```
sudo modprobe ndiswrapper
```

[COLOR="Sienna"][SIZE="4"]13. Make a copy of /etc/network/interfaces for backup purposes[/SIZE][/COLOR]
```
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
```

[COLOR="Sienna"][SIZE="4"]14. Copy some stuff into the file we just made a backup of[/SIZE][/COLOR]
```
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
```

[COLOR="Sienna"][SIZE="4"]15. Create a "wlan0" interface using our new driver[/SIZE][/COLOR]
```
sudo ndiswrapper -m
```

[COLOR="Sienna"][SIZE="4"]16. Add ndiswrapper to the modules loaded at startup[/SIZE][/COLOR]
```
echo 'ndiswrapper' | sudo tee -a /etc/modules
```

[COLOR="Sienna"][SIZE="4"]17. Enable WPA encryption capabilities for the new interface[/SIZE][/COLOR] (I think... This bit of code confuses me. I use WPA encryption on my wireless, and yet it looks to me that this turns it off. *shrug* I did this and my WPA encryption still works.)
```
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

[COLOR="Sienna"][SIZE="4"]18. Reboot, and VIOLA! You should have wireless capabilities in your network manager.[/SIZE][/COLOR]






Credits: Most of the commands are from the wonderful tutorials found at the links in my first post. I do not claim to have the smarts to have come up with this all on my own :lol: . I just thought it would be nice to put all the pieces together.

---

### Post by Redeyes_Gambit on 2007-11-24
One last thing of note; drivers like this tend to go away when least convenient. If somebody who owns a fileserver or webserver could host the driver at an alternate location I, and many other people, would be all smiles I'm sure :D .

---

### Post by lvleph on 2007-12-03
You should really write a script to do all that. If you did, people would appreciate it. I would, but I have my own problems.

---

