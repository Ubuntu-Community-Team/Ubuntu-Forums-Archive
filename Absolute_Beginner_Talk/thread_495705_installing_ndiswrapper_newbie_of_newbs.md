---
title: "installing ndiswrapper newbie of newbs"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by pavelbure on 2007-07-08
can someone please help me install ndiswrapper. i have a wmp54gs card that isnt supported with ubuntu. i tried to use the add/remove programs feature, but seeing as how i cant connect to the internet it is pretty much useless. 
i don't know how to add it from the cd. i downloaded the package from the internet, unzipped it in windows and just transfered the file over to linux desktop.

i tried to follow these instructions, [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/) but even they are too complicated for me. i start to get lost in the "compile and install" section. any help would be appreciated.

thanks

---

### Post by Outrunner on 2007-07-08
Go to Applications -> Accessories -> Terminal and type:

```
sudo apt-cdrom add
```

and follow instructions. Then go to the Synaptic Package Manager (System -> Administration) and search for(with CTRL-F) 'ndiswrapper'. Then you can install it from your CD.

---

### Post by helliewm on 2007-07-08
I have instructions to unzip my EXE file that is on my DEsktop using "unzip -a". How do I do this?

---

### Post by Outrunner on 2007-07-08
Go to the terminal again and type this:

```
cd Desktop
```

This 'changes directory'(cd) to Desktop

and then type

```
unzip -a *.exe
```

---

### Post by pavelbure on 2007-07-08
> **Outrunner said:**
> Go to Applications -> Accessories -> Terminal and type:

```
sudo apt-cdrom add
```

and follow instructions. Then go to the Synaptic Package Manager (System -> Administration) and search for(with CTRL-F) 'ndiswrapper'. Then you can install it from your CD.

i put the stuff in the terminal, loaded the cd when it asked. it seemed to do everything fine there. when i went to the package manager and put ndiswrapper in the sear field it only found 1 thing, and it wasn't ndiswrapper.

---

### Post by Outrunner on 2007-07-08
> **pavelbure said:**
> i put the stuff in the terminal, loaded the cd when it asked. it seemed to do everything fine there. when i went to the package manager and put ndiswrapper in the sear field it only found 1 thing, and it wasn't ndiswrapper.

OK. Then what was it? Maybe you should search again.

---

### Post by pavelbure on 2007-07-08
ok, when i put the stuff in terminal it mounted the cd drive, at the end it said

unmounting cd-rom repeat this process for the rest of the cds in your set.

im not sure if that ^^^^ meant anything.

my only search result was a package called

linux-image-2.6.20-15-generic

---

### Post by pavelbure on 2007-07-09
bump. any help ?

---

### Post by Mazza558 on 2007-07-09
2 questions...

If you go to the terminal,and type "lspci" (without quotes), can you find the line "network controller"?

if so, does it look something like this:

> 00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)


and do you have a USB stick?

---

### Post by pavelbure on 2007-07-10
> **Mazza558 said:**
> 2 questions...

If you go to the terminal,and type "lspci" (without quotes), can you find the line "network controller"?

if so, does it look something like this:



and do you have a USB stick?

i got this



00:11.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

when you say usb stick, you mean a memory stick ? if so then yes, but it isn't plugged in.

on a side note, why doesn't ubuntu just install ndiswrapper by default or at least ask you during installation ?:)

---

### Post by kevdog on 2007-07-10
Here is what you want to do (yea its stupid ndiswrapper isnt on the CD by default)

These are exactly beginner tricks, but you will learn fast.  
Type all commands at command line:
1. Stick in Ubuntu CD, wait to become ready
2. sudo apt-cdrom add
3. sudo aptitude update
4. sudo aptitude install build-essential

Now
mkdir ~/ndiswrapper
cd ndiswrapper
Download ndiswrapper-1.47.tar.gz and place in ~/ndiswrapper directory: [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)
tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
make distclean
make
sudo make install

Now if you can do this command at command prompt and cut and paste output we will finish up:
ndiswrapper -v

---

### Post by pavelbure on 2007-07-10
> **kevdog said:**
> Here is what you want to do (yea its stupid ndiswrapper isnt on the CD by default)

These are exactly beginner tricks, but you will learn fast.  
Type all commands at command line:
1. Stick in Ubuntu CD, wait to become ready
2. sudo apt-cdrom add
3. sudo aptitude update
4. sudo aptitude install build-essential

Now
mkdir ~/ndiswrapper
cd ndiswrapper
Download ndiswrapper-1.47.tar.gz and place in ~/ndiswrapper directory: [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)
tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
make distclean
make
sudo make install

Now if you can do this command at command prompt and cut and paste output we will finish up:
ndiswrapper -v

i skipped step #3, it was trying to connect to the internet, which i cannot do yet.


i got this

pavelbure@pavelbure-desktop:~/ndiswrapper$ ndiswrapper -v
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
filename:       /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.38
vermagic:       2.6.20-15-generic SMP mod_unload 586 

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)
pavelbure@pavelbure-desktop:~/ndiswrapper$

---

### Post by pavelbure on 2007-07-10
bump

---

