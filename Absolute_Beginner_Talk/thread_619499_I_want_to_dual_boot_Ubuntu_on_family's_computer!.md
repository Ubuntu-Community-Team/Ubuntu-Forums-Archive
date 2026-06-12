---
title: "I want to dual boot Ubuntu on family's computer!"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by 449 on 2007-11-21
Hey, I want to install Ubuntu on my family's computer so the rest of them can give it a try! 

Compaq
Presario
AMD Athlon 64 Processor 
3200+
2.00 GHz, 512 MB of RAM

I have a 143 GB HDD with 63 GB of free space. Could someone explain to me how I install Ubuntu without overwriting XP/saved data? Also I already have a live cd burned of Ubuntu ,but it was for a Pentium 4. Do I need a different version? And if I do need another cd can I burn the live cd onto a dvd? 

Thanks!

---

### Post by Pumalite on 2007-11-21
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by 449 on 2007-11-21
Just to make sure, this guide will work the same for 7.10 and also with Windows XP? (XP already installed)

---

### Post by mellowd on 2007-11-21
Yes it will

---

### Post by mellowd on 2007-11-21
Obviously only start form the ubuntu install, you dont want to install windows again

---

### Post by anjilslaire on 2007-11-21
> **449 said:**
> Just to make sure, this guide will work the same for 7.10 and also with Windows XP? (XP already installed)

yes, just start with the ubuntu section, since Windows is already installed. Just resize the NTFS partition to make room for ubuntu.

---

### Post by Incense on 2007-11-21
Be careful though mate. Make sure you have all the important data backed up somewhere. Ubuntu is normally pretty good at setting up a duel boot for you, but if it's the family computer, it would be really bad for something to go wrong at this point, and all the data be lost. It just takes checking the wrong box to erase all the data on the drive.. 

Don't let that scare you away though. It is a very simple process, and I have not lost anything yet. Have fun!

---

### Post by mellowd on 2007-11-21
> **Incense said:**
> Be careful though mate. Make sure you have all the important data backed up somewhere. Ubuntu is normally pretty good at setting up a duel boot for you, but if it's the family computer, it would be really bad for something to go wrong at this point, and all the data be lost. It just takes checking the wrong box to erase all the data on the drive.. 

Don't let that scare you away though. It is a very simple process, and I have not lost anything yet. Have fun!

+1

Backup anything you can't afford to lose. Most of the time it goes without problems but it only takes 1 time...

---

### Post by karrank% on 2007-11-21
Just did the same myself only with Dapper. No prob and I'm a noob.
Just haven't got the dual display thing happening yet with our Vizio hometv.
Otherwise all good so far.
Emachines T3302
Sempron 3200
1.5G Ram
Nvidia 5500
Logitech L710 wireless keyboard/mouse
Dualboot W XP SP2

---

### Post by 449 on 2007-11-21
> **Pumalite said:**
> [http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

Thanks for the guide!

I have some questions I want to ask so I don't mess anything up. :)

I'm at the "Prepare Partitions" page in the installation and am a bit confused here. It says:

/dev/hda
/dev/hda1 fat32 /media/hda1   5527MB unknown
/dev/hda2 ntfs /media/hda2   154503MB unknown
free space                           7MB

Now I have /dev/hda highlighted and I click "New Partion Table" ,but it tell me it will partion the entire drive and I don't want to do that. Help Please?

---

### Post by Pumalite on 2007-11-21
Stop here. Get Gparted Live CD and resize XP partition. A good scheme for the new partition is:
10 GB for '/'
2x /swap up to 1 GB
The rest for /home
Then install going to Manual and use the partitions you made.

---

### Post by 449 on 2007-11-21
> **Pumalite said:**
> Stop here. Get Gparted Live CD and resize XP partition. A good scheme for the new partition is:
10 GB for '/'
2x /swap up to 1 GB
The rest for /home
Then install going to Manual and use the partitions you made.

Is it possible to burn a live cd to a dvd disk? I'm out of cd-r/ :confused:

And I'm guessing it's not possible to use Add/Remove to do a temporay install.

---

### Post by Pumalite on 2007-11-21
Download ImgBurn: [http://www.imgburn.com/](http://www.imgburn.com/)
Install. Go to Mode>ISO>Burn (you can use a DVD)

---

