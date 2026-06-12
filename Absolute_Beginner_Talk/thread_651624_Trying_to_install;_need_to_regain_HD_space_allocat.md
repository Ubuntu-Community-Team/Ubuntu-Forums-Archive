---
title: "Trying to install; need to regain HD space allocated to past installations - help?"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by ChaosTheory on 2007-12-27
First time trying to install Ubuntu. I'm trying to use Wubi. My current OS is Vista.

First attempt: 
1) I said I wanted 15gb to Ubuntu. It downloaded the .iso file and finished the installation. I reboot. Ubuntu installs for the most part (I finished the "Finishing installation" blue screen), but I come to an error. After the error, nothing happened, so I thought the installation was messed up and I manually shut down the computer (I'm a total N00B :(). I try to install it again, but some error comes up and I'm unable to install as before. So, I start up Windows and I uninstall Wubi. But, when I right click my C:\ drive and go to properties, it says that 15gb is being used. 
2) I try again, this time I partition 30gb for Ubuntu, but again I get another error at the beginning of the installation process. I now have ever less free space than before, and Ubuntu is not working. 
3) I uninstall Ubuntu now. I regain some free space (now I'm at -23GB from when I started; I began with 93GB free, out of 140GB). 

I tried using GParted on my partially-installed Ubuntu (I burned the .iso to a disk and it ran as the computer booted up), but it said I didn't have any partitions. PartitionMagic 8.0 says the same thing (though it says I'm using all 144,000MB :confused:) and it said I didn't have any partitions (it also said I have 0MB free space). 

If I have to format Windows, I've got all of my stuff burned onto disks, so that isn't a problem (are there Vista installation files on my computer that I can burn to disk? where?). How do I gain that extra 23GB back?

---

### Post by flamelab on 2007-12-27
First of all ,

Wubi doesn't create partitions !

It creates three BIG files , aka virtual partitions , in C:\wubi 

called 

home.disk , swap.disk , root.disk

You can remove them by uninstalling Wubi .

More info about Wubi here -->[http://ubuntuforums.org/forumdisplay.php?f=234]("http://ubuntuforums.org/forumdisplay.php?f=234")

---

### Post by ChaosTheory on 2007-12-27
Do I just delete the files? 

Edit: Right, so I deleted the home.disk file (only file in the wubi.save folder) and it gave me 12GB back. Now what?

---

### Post by ChaosTheory on 2007-12-27
I can't find any of the other files? I deleted the Wubi folder altogether.  Is that it?

---

### Post by flamelab on 2007-12-30
I guess yes . But have you first uninstalled it through your Control Panel ? If haven't , do it .

---

