---
title: "Ubunto Live CD (64bit) Kernel error"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by Nicoleise on 2006-08-04
Hello everyone. 


I've downloaded the [ubuntu-6.06-desktop-amd64.iso]("http://www.klid.dk/homeftp/ubuntu-cd/6.06/")[COLOR="SeaGreen"] (Link to download site)[/COLOR] to give this Linux distribution a serious try. (It said in the description that that was the one to go for with an EM64T processor too)

The file was downloaded using GetRight 6.0a and burned using Cyberlink Power2Go @ 16x in an NEC DVD-RW drive. I performed Write Simulation and Data Verification.

My PC specs are : 

[LIST]
[*]Intel Pentium 4 HT (EM64T) 3.2 GHz clocked to 3.6 GHZ
[*]Intel 925X/XE chipset
[*]2560 MB DDR2 RAM Dual channel, symmetric
[*]Nvidia Geforce 6600GT 128 MB
[*]Western Digital 2x160 GB HDD, running RAID mirrored.
[/LIST] 

[LIST]
[*]Windows XP Professional Build 2600 (No Service Packs)
[*]NTFS Formatted partions.
[/LIST]
 
I think that's all the vital specs, if I left something out, 
please let me know. 

My problem comes in when I try to boot from the Ubunto CD, I burned from the image. When I hit "Start or Install Ubunto 6.06" it loads the kernel and all that. And then it runs through a string of commands, ending in : 

```

[40.364140] CR2: 00000000e0100000
[40.364178] <0> Kernel Panic - Not syncing : Attempted to kill init!
[40.364258]

```

The buttom line in the code is as far as it gets. 

I know, that the Kernel Panic line was the most important one, but I wanted you people to be able to see where it goes wrong. Since it requires a reboot, and I have nothing to do, I can't PrtScreen, so if you need any more info, let me know, I'll write some more down. 

Of course, I tried some stuff. I tried running it in Safe Graphics setting. Not really any change. I tried the CD checking utility. I tried the "Advanced settings" parametre, which brings up a cmd line for the boot. The problem is, I have no idea what all of that stuff does, so I tried running it with every parameter, it has in there, and that gave me a different result. I loaded the kernel again, but instead of the string of commands, it just went into a black screen (but kept the monitor alive). I left it like that for 5 minutes, but no dice. 

So now, I'm thinking that I might need one of those parametres but not some of the other ones...?

Or is any of my hardware/software incompatible ? I assumed it could run of NTFS for the check out CD boot only ?

I've googled the problem by the way, and also searched this forum. But what ever I find, it doesn't seem to be related. The Kernel Panic seems to be a common error message, so I get a lot of stuff... And there's not really any idea for me to download a new version, because some user of RedHat tryed making a server and got the same error. 

So I made a user here, and I hope some of you wizards has just the right answer... :)

Cheers, 
NicoLeise

P.S. On a side note, just to make sure. Is Ubunto and Dapper Drake the same ?

---

### Post by Nicoleise on 2006-08-04
Bump...

(It seems there are alot more activity now, so I hope someone can help me. ) :)

---

### Post by bobbob1016 on 2007-07-26
Just a thought, I have an P4 3.2 HT chip, and it isn't 64bit.  Try the 32bit version.

---

