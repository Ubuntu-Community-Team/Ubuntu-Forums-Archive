---
title: "cant boot from live cd"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by pgar23 on 2007-08-19
I have checked the threads before posting a new one, No one had a similar problem as me.

When trying to boot from the Live cd(or alternate for that matter) it hangs at squashfs: Version 3.2-r2...and I know it is supposed to stall here for a while, but I waited about 10minutes and it didn't boot from either cd.

I do not want to start a fresh install because it took me and a friend(javajake: thanks so much btw) about 5 hours to get around some of the problems I was facing.

Specs:
Computer: Dell Optiplex GX60
Processor: Intel Celeron 1.70GHz
Memory: 256 MB
HDD: 160 GB
Firmware: BIOS-Version A09

---

### Post by redfox1160 on 2007-08-19
sry that this is off topic, but could you tell me what the LiveCD is?

---

### Post by nitro_n2o on 2007-08-19
why do u wanna boot from the liveCD?

---

### Post by pgar23 on 2007-08-19
The live Cd is a test Ubuntu CD that u can safely try without altering any of the files or anything else on your computer.

---

### Post by fr0stbound on 2007-08-19
the live cd is a cd that can also boot on ubuntu on itself without installing. it just uses files from the cd. if you have already installed ubuntu, most likely this is what you have.

have you tried using the command "linux acpi=off" prior to selecting install?(without the quotes)

---

### Post by Jimmyfj on 2007-08-19
> **redfox1160@verizon.net said:**
> sry that this is off topic, but could you tell me what the LiveCD is?

The live Cd is the Cd containing an image. You just insert in your Cd/DVD drive and reboot your computer with the Live Cd in your drive. You can get it from:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Or you could go to [http://www.ubuntu.com](http://www.ubuntu.com) and ask for the free Cd by mail

---

### Post by nitro_n2o on 2007-08-19
> **pgar23 said:**
> The live Cd is a test Ubuntu CD that u can safely try without altering any of the files or anything else on your computer.
But u already have installed ubuntu... what do u wanna try? 
is there any specific problem(s) with your PC and you need to recover it with the LiveCD?

---

### Post by pgar23 on 2007-08-19
> **nitro_n2o said:**
> why do u wanna boot from the liveCD?

I wanna boot from live cd so I can open a terminal and enter this code so I can see my GRUB menu again.
```

$ sudo grub
$ find /boot/grub/stagel
$ root (hd0,6)
$ setup (hd0)
$ quit

```
ps. is this the right code and also do I need the money signs or is that already there?

BTW I have Ubuntu on my computer already, I did a fresh install of XP...forgetting that it would overwrite my grub, but now i Just want the grub menu back so I can acces Ubuntu again

---

### Post by nitro_n2o on 2007-08-19
> **pgar23 said:**
> I wanna boot from live cd so I can open a terminal and enter this code so I can see my GRUB menu again.
```

$ sudo grub
$ find /boot/grub/stagel
$ root (hd0,6)
$ setup (hd0)
$ quit

```

BTW I have Ubuntu on my computer already, I did a fresh install of XP...forgetting that it would overwrite my grub, but now i Just want the grub menu back so I can acces Ubuntu again
ohh i seee :) this is a trouble then.. don't worry about my previous post.. 
do u have the LiveCD or the alternate text based?

---

### Post by pgar23 on 2007-08-19
> **nitro_n2o said:**
> ohh i seee :) this is a trouble then.. don't worry about my previous post.. 
do u have the LiveCD or the alternate text based?

yes i have both cd's...but neither boot, it hangs at the squashfs: version 3.2-r2...and never does anything

also is that the correct code above?

---

### Post by fr0stbound on 2007-08-19
it would be much easier if you had the alternate install disc. im not sure about this, but if you just have to boot to get to the command line, maybe you can just boot using a small distro like puppy or dsl

---

### Post by pgar23 on 2007-08-19
I Have The Alternate Install Disk And The Live Cd! neither boot tho, this is my problem at the moment.

---

### Post by nitro_n2o on 2007-08-19
you code looks right 
but 
$ root (hd0,6)
$ setup (hd0)
depends on the output of find 
and it might be better to 
setup(hd0, 6) 
or whtever the output is...
try using super grub [http://geocities.com/supergrubdisk/](http://geocities.com/supergrubdisk/)

---

### Post by fr0stbound on 2007-08-19
have you tried 
```
acpi=off
```

---

### Post by pgar23 on 2007-08-19
> **nitro_n2o said:**
> you code looks right 
but 
$ root (hd0,6)
$ setup (hd0)
depends on the output of find 
and it might be better to 
setup(hd0, 6) 
or whtever the output is...
try using super grub [http://geocities.com/supergrubdisk/](http://geocities.com/supergrubdisk/)

I took a look at super grub, but I would prefer to do it manually, as I dont want anything moved or messed up since it took me and a friend forever to even get the installation.

and wut do u mean it depends on the output of find.

---

### Post by nitro_n2o on 2007-08-19
so you'll type 
sudo grub 
then 
```
find /boot/grub/stage1 
```
this find will give you something like hda(0,6)  or sda(0,1) whtever is that thing you use it as a parameter for root and setup


and try acpi=off as fr0stbound suggested

---

### Post by pgar23 on 2007-08-19
> **fr0stbound said:**
> have you tried 
```
acpi=off
```

I havent tried that because I dont have a command line or terminal to enter this. 

This is my dilema(simply explained):

I turn on my computer and it boots to Windows automatically (no grub menu)
I want to turn on my computer and have a grub menu to choose which OS to boot.
I cant boot from either the LIVECD or AlternateCD.
I have no command line or terminal to work from.

---

### Post by nitro_n2o on 2007-08-19
you can use the System rescue CD [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) this will boot for sure and has some useful utils..

---

### Post by pgar23 on 2007-08-19
> **nitro_n2o said:**
> you can use the System rescue CD [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) this will boot for sure and has some useful utils..

maybe i will use this. Once I install that and wutever else, should I be able to boot from LIVECD?

That system rescue wont change anything I did to install Ubuntu will it?
I CANNOT ALTER THE METHOD OF INSTALLING UBUNTU. it took us too long to restart and do everything again. lol

---

### Post by pgar23 on 2007-08-19
i just found this easy how to for anyone who has problems veiwing the grub menu--------------------->[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

