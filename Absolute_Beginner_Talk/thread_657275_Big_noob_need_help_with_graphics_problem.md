---
title: "Big noob need help with graphics problem"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by omnipotentj on 2008-01-03
Hi everyone I am very new to Linux and Ubuntu been a windows user all my life I am quite confused about certain things. I am currently setting up compiz fusion and thought id finally done it using various guides on these forums. When i rebooted after installing the latest nvidia drivers with envy and compiz fusion my screen has tearing all over it and multi coloured lines banding accross the screen. Is there anyway i can edit a file of some description using the live cd to set the resolution or boot into some sort of safe mode? Thanks - Joel

---

### Post by taurus on 2008-01-03
You can boot your machine to recovery mode from GRUB menu when you turn on your machine (if you don't see the menu, press Esc).  Then, you can edit your /etc/X11/xorg.conf

```
nano -Bw /etc/X11/xorg.conf
```
Save it with <Ctrl>o and exit with <Ctrl>x.

Or you can reconfigure your X server again with

```
dpkg-reconfigure -phigh xserver-xorg
```

Reboot your machine with

```
shutdown -r now
```

---

### Post by omnipotentj on 2008-01-03
I am on the live CD and have created a new xorg.conf file however i cannot delete the original as I dont have permission how do I delete it and rename the replacment "xorg.conf"

---

### Post by Nimaran on 2008-01-03
What you have to do is log into Nautilus with sudo privileges. (That is how you gain permission to access root files.)

The easiest way I find to do this is enter:
```
sudo nautilus
```

That way you don't have to try deleting things via the command line. (That always makes my head hurt).

You should just be able to navigate to the location of the file you need to replace and do it by cut/paste or whatever.

---

### Post by omnipotentj on 2008-01-03
Im on the livecd and the file is on the hard drive i need to be able to log in or something to get privledges

---

### Post by Nimaran on 2008-01-03
You should be able to edit stuff on the hard drive with the above command. Try navigating to /media/ your hard drive should be one of those folders, if it is mounted, which it should be.

---

### Post by omnipotentj on 2008-01-03
The drive is mounted when i attempt to delete it it says " Error while deleting     "/media/disk.../xorg.conf" cannot be deleted because you do not have permission to modify its parent folder."

---

### Post by Nimaran on 2008-01-03
Are you using the nautilus window that came up after you typed:

```
sudo nautilus
```

---

### Post by omnipotentj on 2008-01-03
Ok I replaced the file ( thanks Nimaran ) now I have a config window asking for me to tell it what monitor type etc I want; last time I told it exactly what monitor I have (samsung synmaster 215tw digital input res of 1650x1050) this caused the problem, I have just set it to a generic monitor 1280 x 960 and it has done it again :S I have lines all accross the screen like some bad artifacting

---

### Post by taurus on 2008-01-03
> **omnipotentj said:**
> The drive is mounted when i attempt to delete it it says " Error while deleting     "/media/disk.../xorg.conf" cannot be deleted because you do not have permission to modify its parent folder."

Instead of deleting it, why not just change the name.

Applications -> Accessories -> Terminal
```
sudo mv /media/disk/etc/X11/xorg.conf /media/disk/etc/X11/xorg.conf.old
```

p.s.  What graphic card do you have?  Try putting the vertical and horizontal refreshing rates for your monitor in /etc/X11/xorg.conf.

---

### Post by omnipotentj on 2008-01-03
I have an 8800gtx

---

### Post by Nimaran on 2008-01-03
Sorry, I don't really have any experience in that area. My only suggestion would be selecting Failsafe Gnome from the sessions option at the main login screen and then disabling compiz. If that doesn't stop it then it is probably a driver problem. Oh, wait, have you enabled the restricted drivers?

---

### Post by omnipotentj on 2008-01-03
How do I renable the restricted drivers through the live cd?

---

### Post by taurus on 2008-01-03
Which driver are you using right now in /etc/X11/xorg.conf?

You can still install nvidia-glx-new from a prompt in the recovery mode (booting into recovery mode from GRUB menu) if you wish.

```
sudo apt-get update
sudo apt-get install nvidia-glx-new
```

---

