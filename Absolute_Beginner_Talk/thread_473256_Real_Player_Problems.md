---
title: "Real Player Problems"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Bostonian on 2007-06-13
I'm having trouble playing files in the realplayer format. so far i've tried:

```
$ sudo apt-get install realplayer 
```> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate


downloaded realplayer from their website and...

```
$ chmod -x RealPlayer10GOLD.bin 
$ ./RealPlayer10GOLD.bin
bash: ./RealPlayer10GOLD.bin: Permission denied

$sudo ./RealPlayer10GOLD.bin
```> sudo: ./RealPlayer10GOLD.bin: command not found



then helix
```
$ chmod -x hxplay-1.0.8.806-linux-2.2-libc6-gcc32-i586.bin 

$ sudo ./hxplay-1.0.8.806-linux-2.2-libc6-gcc32-i586.bin 
Password:

```> sudo: ./hxplay-1.0.8.806-linux-2.2-libc6-gcc32-i586.bin: command not found

any advice would be appreciated. I just want to view .rm files, i don't really care about the means. Thanks.

---

### Post by srt5 on 2007-06-14
shouldn't it be +x as opposed to -x?

---

### Post by ugm6hr on 2007-06-14
For Feisty - see my post here:

[http://ubuntuforums.org/showthread.php?t=454622](http://ubuntuforums.org/showthread.php?t=454622)

Much easier.

---

### Post by wpshooter on 2007-06-14
> **srt5 said:**
> shouldn't it be +x as opposed to -x?

I agree, I think if you use chmod +x, you will be fine.

---

### Post by Bostonian on 2007-06-17
Hi, I tried the +x to no avail, but my problem is different now:

```
$ ls R*[B]
RealPlayer10GOLD.bin[/B]
$ chmod a+x RealPlayer10GOLD.bin 
$ ./RealPlayer10GOLD.bin [B]
bash: ./RealPlayer10GOLD.bin: No such file or directory[/B]

```

Thanks for all the help so far.

---

### Post by ugm6hr on 2007-06-18
> **Bostonian said:**
> Hi, I tried the +x to no avail, but my problem is different now:

```
$ ls R*[B]
RealPlayer10GOLD.bin[/B]
$ chmod a+x RealPlayer10GOLD.bin 
$ ./RealPlayer10GOLD.bin [B]
bash: ./RealPlayer10GOLD.bin: No such file or directory[/B]

```

Thanks for all the help so far.

Seriously - try this:

Download this:
[http://www.youmortals.com/ubuntu/packages/realplayer_10.0.7-0.0_i386.deb](http://www.youmortals.com/ubuntu/packages/realplayer_10.0.7-0.0_i386.deb)

Then open it (double click from File Manager). It should automatically open and install in GDebi.

---

### Post by Michaelt74 on 2007-06-18
This may help
[http://opensourceroolz.wordpress.com/2007/06/10/radio-using-realplayer-on-ubuntu-feisty-704/](http://opensourceroolz.wordpress.com/2007/06/10/radio-using-realplayer-on-ubuntu-feisty-704/)

---

### Post by Arjunanda on 2007-07-21
> **ugm6hr said:**
> Seriously - try this:

Download this:
[http://www.youmortals.com/ubuntu/packages/realplayer_10.0.7-0.0_i386.deb](http://www.youmortals.com/ubuntu/packages/realplayer_10.0.7-0.0_i386.deb)

Then open it (double click from File Manager). It should automatically open and install in GDebi.

Did not work for me (feisty)

```
~$ realplayer 
Segmentation fault (core dumped)
```

---

### Post by ugm6hr on 2007-07-21
> **Arjunanda said:**
> Did not work for me (feisty)

```
~$ realplayer 
Segmentation fault (core dumped)
```

Really?  Unusual....  Have you installed realplayer before (or Helix Player) - if so, it needs to be uninstalled first (don't ask me how if you didn't use a* .deb* - but it is possible).  Maybe try re-downloading the link (maybe it got corrupted)

Other option (if the .deb is corrupted):
[http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

Follow the instructions here (for Feisty), it should add an entry to Synaptic "realplay" - I believe it's reliable, but I haven't tried it.

---

### Post by Arjunanda on 2007-07-21
> **ugm6hr said:**
> Really?  Unusual....  Have you installed realplayer before (or Helix Player) - if so, it needs to be uninstalled first (don't ask me how if you didn't use a* .deb* - but it is possible).  Maybe try re-downloading the link (maybe it got corrupted)

I had it previously installed from a similar .deb file. Before trying the file you pointed out, I performed 
sudo apt-get remove realplayer

and then run the install through gdebi. Now I re-downloaded the file and run the install again. 

```

Valitsen aikaisemmin valitsemattoman paketin realplayer.
(Reading database ... 117011 files and directories currently installed.)
Unpacking realplayer (from .../realplayer_10.0.7-0.0_i386-1.deb) ...
Säädän asetukset: realplayer (10.0.7-0.0) ...

```
but result is the same, core dumped.

Tried also the other option you pointed out.

> Other option (if the .deb is corrupted):
[http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)
Follow the instructions here (for Feisty), it should add an entry to Synaptic "realplay" - I believe it's reliable, but I haven't tried it.

Did not work either. Result:
```

$ sudo apt-get install realplay
Luetaan pakettiluetteloita... Valmis
Muodostetaan riippuvuussuhteiden puu       
Luetaan tilatietoja... Valmis       
Pakettia realplay ei ole saatavilla, mutta toinen paketti viittaa siihen.
Tämä voi tarkoittaa paketin puuttuvan, olevan vanhentunut tai
saatavilla vain jostain muusta lähteestä
E: Paketilla realplay ei ole asennettavaa valintaa

```
Which says roughly "package realplay is not available, but another package refers to it. This could mean the package is missing, is expired or available only from another source. E: The packet realplay has no installable selection-

While I was using edgy, I was able to install real player. Now it seems really a n ightmare. Perhaps next I will follow the other guide given above, whree you install the original bin file from real.com.

---

### Post by ugm6hr on 2007-07-21
> **Arjunanda said:**
> I had it previously installed from a similar .deb file. Before trying the file you pointed out, I performed 
sudo apt-get remove realplayer

Is it uninstalled according to Synaptic?  Usually you need to use dpkg command to uninstall a .deb

---

### Post by Arjunanda on 2007-07-21
> **ugm6hr said:**
> Is it uninstalled according to Synaptic?  Usually you need to use dpkg command to uninstall a .deb
Yes it was uninstalled according to synaptic. But I re-installed the .deb, and performed 

```

~$ sudo dpkg -r realplayer
(Reading database ... 117195 files and directories currently installed.)
Removing realplayer 

```

and again re-installed with gdebi, and still it does a core dump.

---

### Post by Arjunanda on 2007-07-23
I found the answer. RealPlayer has some issues with SCIM and as I have been experimenting with it, it has been causing the segmentation fault. Found the answer from here:
[https://help.ubuntu.com/community/RealplayerInstallationMethods#head-e3573c62070897ed8effe54aa71063b7bb35991f](https://help.ubuntu.com/community/RealplayerInstallationMethods#head-e3573c62070897ed8effe54aa71063b7bb35991f)

Now it works using command
```

export GTK_IM_MODULE=xim; realplay

```

Thanks

---

### Post by Arjunanda on 2007-07-23
Oh now I would need a shell skript that would set this environment variable and then call real player with an URL as an argument. I have created the following, but it merely starts the player, but does not pass the URL to the program. How could I modify it to enable the loading of URL?

```

#!/bin/bash
export GTK_IM_MODULE=xim
aoss realplay

```

---

### Post by Arjunanda on 2007-07-23
Ok, found it! Now it works
```

#!/bin/bash
export GTK_IM_MODULE=xim
aoss realplay $0

```

But still I have some issues with some content.

---

