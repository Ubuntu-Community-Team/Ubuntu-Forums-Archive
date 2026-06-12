---
title: "wireless internal specs"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Fying_Hgh on 2008-02-25
I have Ubuntu 7.10 installed and most everything working.
I have been reading forums for quite abit on how to get the driver for the internal wireless to work.
Here are the specs to make this question brief.
Compaq C751NR
Device Manager shows this........
AR5006EG 802.11 b/g Wireless PCI Express Adapter
I am not sure if I have the correct driver and not sure how to install it from the terminal.
I am saving the drivers to my desktop (is this ok?)
Thanks to any out there for taking there time out to help. I have reading here a lot

I also want to say thanks to the forums for all that I have read and learned thus far!

---

### Post by northern lights on 2008-02-25
Oye, this [blog entry should solve your problem]("http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/")...

Cheers, Pille

---

### Post by Fying_Hgh on 2008-02-28
I really appreciate the reply. It is going to take me awhile though!
Meanwhile I am learning!!!!!! Dang this is fun!

---

### Post by Fying_Hgh on 2008-03-06
I have followed these instructions the best I can.

When I go to System- Administration - Windows Wireless Drivers
At first it says "Unable to see if hardware is present"
I click ok..............then i see a list of drivers.
net5211 Hardware present:Yes
net5416 Invalid Driver!
net 5416" Invalid Driver!
netathr Hardware present:Yes

I think from the instructions that netathr is gonna conflict with the other driver. I just can't seem to get rid of it.

Also this computer  (Compaq Presario C751NR) has a wireless button on it. It is orange now . I have read other posts on this that maybe it is a bios setting.
Obviously...........I am not doing something correct. Just not sure what. Any ideas?

---

### Post by Fying_Hgh on 2008-03-16
Now I have the net5416 working. When I type blacklist ath_pci in terminal.......it says ....

bash: blacklist: command not found

I can't get that to work..............any Ideas?

---

### Post by bsharp on 2008-03-16
```
sudo echo "blacklist ath_pci" | tee -a /etc/modprobe.d/blacklist
```

---

### Post by Fying_Hgh on 2008-03-16
I typed that command in terminal and I got this..........

tee: /etc/modprobe.d/blacklistr: Permission denied
blacklist ath_pci
Thanks to all who have helped me.

---

