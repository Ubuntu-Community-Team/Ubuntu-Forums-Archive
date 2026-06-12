---
title: "How To: Install realpayer-- the easy way."
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Paulmd on 2007-08-01
As some of you may have noticed, the install from real.com doesn't work well. Luckily there is an easier way.

In the terminal:
```

#sudo pico /etc/apt/sources.list
```

Add the following line to the file, then save and exit.

```
deb http://www.debian-multimedia.org stable main

```

Get the key, so you don't get any warnings about trust. If you skip this step, it's not fatal, but you will get warnings.

[http://www.debian-multimedia.org/pool/main/d/debian-multimedia-keyring/debian-multimedia-keyring_2007.02.14_all.deb](http://www.debian-multimedia.org/pool/main/d/debian-multimedia-keyring/debian-multimedia-keyring_2007.02.14_all.deb)

then, in the terminal

```
#sudo apt-get update
#sudo apt-get install realplayer


```
Note: this also works for acrobat reader (another troublesome app to install from the website). Just replace 'realplayer' with 'acroread'.  

If you want to install both realplayer  and acrobat, the last line would read

```
#sudo apt-get install realplayer acroread
```

---

### Post by redefender on 2007-08-01
No good here:

> E: Couldn't find package realplay

---

### Post by Paulmd on 2007-08-01
> **redefender said:**
> No good here:

My mistake: the package name is realplayer, not realplay. I'll edit the instructions.

---

### Post by offchance on 2007-08-03
added the entry to the repo list, this is the outcome:


sudo apt-get install realplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate

---

### Post by silent1643 on 2007-08-03
doesn't [automatix2]("http://getautomatix.com/wiki/index.php?title=Software_and_Tweaks#Media_Players_and_Editors") have real player ???

---

### Post by ugm6hr on 2007-08-03
> **silent1643 said:**
> doesn't [automatix2]("http://getautomatix.com/wiki/index.php?title=Software_and_Tweaks#Media_Players_and_Editors") have real player ???

Yes - but as many previous discussions have made clear - you run the* risk* of making a mess of your entire installation with Automatix.

---

### Post by tashmooclam on 2007-08-03
I don't know whether I used automatix or add/remove or synaptics package manager, but I have real player.
Not that it ever starts. If I click a video, usually mplayer starts or totem by default.

---

### Post by NilsE on 2007-08-03
Since I am never comfortable about adding "external" and not necessarily supported repositories I tend to install things like RealPlayer the old tried, trusted and ultimately effective way.  After lots of experimenting and culling information from this forum I came up with the following steps that always work for me.

I have no problem with the above process and only post this in case it does not work for you for any reason.

1) In Synaptic make sure shared libraries: libstdc++.5 (or newer) is installed. 

2) Download RealPlayer from [http://www.real.com/linux](http://www.real.com/linux) to your **home folder** by clicking on the gold "Download RealPlayer" button.

3) In a **none root** terminal enter the following commands (none root so it is installed under the user not root). 

You can copy and paste each line.

```
cd /home/xxxxx  

NOTE: Where xxxxx is you home  folder
```
```
chmod +x RealPlayer10GOLD.bin

NOTE: Applies permissions
```
```
sudo ./RealPlayer10GOLD.bin

NOTE: As it does the install you can take all the defaults.
```

This will install RealPlayer and the Mozilla plugin.

---

### Post by Paulmd on 2007-08-03
> **offchance said:**
> added the entry to the repo list, this is the outcome:


sudo apt-get install realplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate

you remembered the 

#sudo apt-get update

part? It's important, it reloads the sources.list file.

---

### Post by kancler on 2007-08-04
> **Paulmd said:**
> you remembered the 

#sudo apt-get update

part? It's important, it reloads the sources.list file.

I did everything like you said. But still getting same message:

vlad@vlad-laptop:~$ sudo apt-get install realplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate


What should I try next? Thank you very much for help

---

### Post by kancler on 2007-08-04
> **NilsE said:**
> Since I am never comfortable about adding "external" and not necessarily supported repositories I tend to install things like RealPlayer the old tried, trusted and ultimately effective way.  After lots of experimenting and culling information from this forum I came up with the following steps that always work for me.

I have no problem with the above process and only post this in case it does not work for you for any reason.

1) In Synaptic make sure shared libraries: libstdc++.5 (or newer) is installed. 

2) Download RealPlayer from [http://www.real.com/linux](http://www.real.com/linux) to your **home folder** by clicking on the gold "Download RealPlayer" button.

3) In a **none root** terminal enter the following commands (none root so it is installed under the user not root). 

You can copy and paste each line.


```
cd /home/xxxxx  

NOTE: Where xxxxx is you home  folder
```
```
chmod +x RealPlayer10GOLD.bin

NOTE: Applies permissions
```
```
sudo ./RealPlayer10GOLD.bin

NOTE: As it does the install you can take all the defaults.
```

This will install RealPlayer and the Mozilla plugin.


Follow steps you recommended. Still getting stupid message:

vlad@vlad-laptop:~$ sudo ./RealPlayer10GOLD.bin
sudo: unable to execute ./RealPlayer10GOLD.bin: No such file or directory


Could you give any advice? Thank you!

---

### Post by Paulmd on 2007-08-04
> **kancler said:**
> I did everything like you said. But still getting same message:

vlad@vlad-laptop:~$ sudo apt-get install realplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate


What should I try next? Thank you very much for help

Some things to try:

Go into the Synaptic package manager and search for 'realplay', and see if 'realplayer' is available.

Also in Synaptic: click on the button that says 'Origin' and see if the repository is added.

Next would be to double check etc/apt/sources.list to make sure that the name of the repository is spelled right, and that the line is not commented out. Lines beginning with '#' are comments.

Edit:

One more thing: you have to be connected to the internet for this to work. I forgot to mention that.

---

### Post by ugm6hr on 2007-08-04
If you don't have a live Ubuntu internet connection - you can try this method (very easy):
[http://ubuntuforums.org/showpost.php?p=2720883&postcount=4](http://ubuntuforums.org/showpost.php?p=2720883&postcount=4) (Realplayer 10.0.7)

---

### Post by misfitpierce on 2007-08-04
I honestly dont know how alot of ppl get messed up packages from automatix... It has worked great for me and every friend's pc I load it too... Great tool. :)

---

### Post by Miroku on 2007-08-18
>  Since I am never comfortable about adding "external" and not necessarily supported repositories I tend to install things like RealPlayer the old tried, trusted and ultimately effective way. After lots of experimenting and culling information from this forum I came up with the following steps that always work for me.

I have no problem with the above process and only post this in case it does not work for you for any reason.

1) In Synaptic make sure shared libraries: libstdc++.5 (or newer) is installed.

2) Download RealPlayer from [http://www.real.com/linux](http://www.real.com/linux) to your home folder by clicking on the gold "Download RealPlayer" button.

3) In a none root terminal enter the following commands (none root so it is installed under the user not root).

You can copy and paste each line.


Code:

cd /home/xxxxx  

NOTE: Where xxxxx is you home  folder

Code:

chmod +x RealPlayer10GOLD.bin

NOTE: Applies permissions

Code:

sudo ./RealPlayer10GOLD.bin

NOTE: As it does the install you can take all the defaults.

This will install RealPlayer and the Mozilla plugin.

i installed it that way, and realplayer is still giving me problems. now i want to uninstall it but i cant do 'sudo apt-get remove'. 

how do you uninstall it now?

---

### Post by Paulmd on 2007-08-19
> **Miroku said:**
> i installed it that way, and realplayer is still giving me problems. now i want to uninstall it but i cant do 'sudo apt-get remove'. 

how do you uninstall it now?

It seems that programs not installed with the package manager cannot be deleted with the package manager.


See here:
[http://www.linuxforums.org/forum/debian-linux-help/35708-uninstall-realplayer-10-a.html](http://www.linuxforums.org/forum/debian-linux-help/35708-uninstall-realplayer-10-a.html)

[https://player.helixcommunity.org/2005/help/playerfaq.html#mozTocId185549](https://player.helixcommunity.org/2005/help/playerfaq.html#mozTocId185549)

[https://player.helixcommunity.org/2005/downloads/uninst.sh](https://player.helixcommunity.org/2005/downloads/uninst.sh)

Note: I have not tried this myself (because i want to KEEP realplayer :) ), the uninstall script s listed as "unsupported".  So use at your own risk.

---

### Post by philinux on 2007-08-19
The easy way is to install from Synaptic Package Manager :lolflag:

---

### Post by Miroku on 2007-08-20
yea, i just deleted the directory. and that was yesterday. so, so far so good. :)

---

### Post by oldos2er on 2007-08-20
>Follow steps you recommended. Still getting stupid message:

>vlad@vlad-laptop:~$ sudo ./RealPlayer10GOLD.bin
>sudo: unable to execute ./RealPlayer10GOLD.bin: No such file or directory

 I don't think you need sudo for this. Go to the directory where RealPlayer10GOLD.bin is, and type chmod +x RealPlayerGOLD.bin
 Then run sh ./RealPlayerGOLD.bin

---

