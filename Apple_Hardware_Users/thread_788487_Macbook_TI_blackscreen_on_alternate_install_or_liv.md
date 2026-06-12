---
title: "Macbook TI blackscreen on alternate install or liveCD"
date: 2008-05-09
forum: Apple Hardware Users
---

### Post by reverend1313 on 2008-05-09
ok so I have a Macbook TI that runs the old 6.06 ubuntu just fine but I wanted to give the newer stuff a try. I tried 7.04 through 8.04 live CDs for PPC but all I get on boot is a black screen with a faint white bar at the bottom. Anyone know how to get around that?

In addition to the above i tried the 8.04 alternate PPC install and it ran through and installed fine but on the first boot without the CD in it once again gives me the wierd black screen and seems to hang. any ideas

---

### Post by reverend1313 on 2008-05-09
Ok i got my 8.04 instll to boot so I can login now by stopping the boot process by holding "L" like you would hold C to boot to a CD. Then I type "Linux video=ofonly" and it boots into the OS fine. Now how do I add that command so it runs everytime I boot.

---

### Post by cyberdork33 on 2008-05-10
just for future reference, if you have a PPC proc you do not have a Macbook. It is a Powerbook or iBook.

---

### Post by avtolle on 2008-05-10
> **reverend1313 said:**
> Ok i got my 8.04 instll to boot so I can login now by stopping the boot process by holding "L" like you would hold C to boot to a CD. Then I type "Linux video=ofonly" and it boots into the OS fine. Now how do I add that command so it runs everytime I boot.

You will need to edit your /etc/yaboot.conf file. At the terminal, ```
sudo cp /etc/yaboot.conf /etc/yaboot.conf.bak #Make a backup file, just in case
sudo nano /etc/yaboot.conf
```Make the change needed ("video=ofonly") to both the image=/boot/vmlinux and /boot/vmlinux.old entries, save and exit nano. Then, to make it permanent, ```
sudo ybin -v -C /etc/yaboot.conf
```Note the uppercase "C" in the last command.
Then reboot.
BTW, at the second stage of booting, hit TAB to give you a bit more time, then type Linux video=ofonly to pass the parameter a bit more easily (IMHO) if you need to restart before getting these changes made. Hope that helps.

---

