---
title: "Google Earth"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by groeswenphil on 2007-03-14
Hi Group,

I've jsut downloaded Google Earth.
It arrived as a BIN file.

Now, I think I need something called X ORG?

So, what do I do next..............?

Phil from Wales

---

### Post by mahiyar on 2007-03-14
I installed google earth using Automatix 2, but of late it seems to be in trouble, but if .bin is what you have then no problem just cd into the directory having the bin file (from CLI) and run this ./filename.bin. Hopefully this installer will create all the short cuts etc. else you will have to search for the executable file and create a launcher (that too is not so difficult)

---

### Post by Native Dialect on 2007-03-14
To my knowledge, BIN files are generic binary code files that accompany data files. Typically a BIN file come with an ISO que of some sort to be burned. Did the file you download, come with that? If so, you may try burning the image to disc, and see what turns up.

---

### Post by Kobalt on 2007-03-14
Once you've downloaded the bin file you have to install it with this command line : ```
sudo sh GoogleEarthLinux.bin
```

---

### Post by mahiyar on 2007-03-14
if running the .bin grumbles about permission you may need to change the permissions with this command >>sudo chmod +x filename.bin .

Native Dialect -- You are right there are also bin files which can be burnt to a disk, but it comes with an accompanying .cue file. This type of .bin in linux is an installation file.

---

### Post by jjalocha on 2007-03-14
I've installed the "googleearth" package from the Ubuntu repositories, and it's working perfectly. Version 4.0.2735. I'm not sure if it's in Universe or Multiverse, though.

---

### Post by Vexed Arcanist on 2007-03-14
What version of Ubuntu did you find it in the repositories?  Previously I ran Edgy and I don't recall it being available.  I now run Feisty and it is in the repositories and installs/runs flawlessly.

---

### Post by noob_saioke45601 on 2007-03-14
> **jjalocha said:**
> I've installed the "googleearth" package from the Ubuntu repositories, and it's working perfectly. Version 4.0.2735. I'm not sure if it's in Universe or Multiverse, though.

yea im using 6.10 edgy and its not in my repositories.

---

### Post by DoorGunner on 2007-03-14
How to install Google Earth 

wget -c [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
sudo chmod +x ~/Desktop/GoogleEarthlLinux.bin
sudo sh GoogleEarthLinux.bin

** important. once the installler has finished installing DO NOT RUN the program. Just quit or exit

sudo chmod 777 -R ~/.googleearth

Now you can start google earth

---

### Post by guysmiley25 on 2007-03-14
Google Earth is in my repositories. I installed using
```
sudo aptitude install googleearth
```

Here is my /etc/apt/sources.list
```

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
                                                                                                                                     
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Morgoth - Ubuntu 6.10 "edgy eft"
deb http://morgoth.free.fr/ubuntu edgy-backports main
deb-src http://morgoth.free.fr/ubuntu edgy-backports main

## Medibuntu - Ubuntu 6.10 "edgy eft"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free

## Official Skype Repository
#deb http://download.skype.com/linux/repos/debian/ stable non-free

## IVTV Driver (mythtv)
deb http://dl.ivtvdriver.org/ubuntu edgy firmware

## Asher256's Repository
#deb http://asher256-repository.tuxfamily.org edgy main dupdate french
#deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french

## Alberto Milone (Ubuntu's Bleeding Edge Drivers)
#deb http://www.albertomilone.com/drivers/edgy/latest/32bit binary/
#deb http://www.albertomilone.com/drivers/edgy/latest/64bit binary/

## Listen
#deb http://theli.free.fr/packages/ edgy listen

```

And the dapper version
```

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

## Morgoth - Ubuntu 6.10 "dapper drake"
deb http://morgoth.free.fr/ubuntu dapper-backports main
deb-src http://morgoth.free.fr/ubuntu dapper-backports main

## Medibuntu - Ubuntu 6.10 "dapper drake"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ dapper free
deb http://medibuntu.sos-sts.com/repo/ dapper non-free
deb-src http://medibuntu.sos-sts.com/repo/ dapper free
deb-src http://medibuntu.sos-sts.com/repo/ dapper non-free

## Official Skype Repository
#deb http://download.skype.com/linux/repos/debian/ stable non-free

## IVTV Driver (mythtv)
deb http://dl.ivtvdriver.org/ubuntu dapper firmware

## Asher256's Repository
#deb http://asher256-repository.tuxfamily.org dapper main dupdate french
#deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french

## Alberto Milone (Ubuntu's Bleeding Edge Drivers)
#deb http://www.albertomilone.com/drivers/dapper/latest/32bit binary/
#deb http://www.albertomilone.com/drivers/dapper/latest/64bit binary/

## Listen
#deb http://theli.free.fr/packages/ dapper listen

```

I think Medibuntu could be the one responsible. But I'm not sure.

---

### Post by Vexed Arcanist on 2007-03-14
Yes, Medibuntu, I forgot I had added theirs in Feisty.

---

### Post by jjalocha on 2007-03-14
Weird... I'm running Edgy, and I'm NOT using Medibuntu... (didn't even know about that). Here's my /etc/apt/sources.list:

```


deb http://cr.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://cr.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://cr.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://cr.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://cr.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://cr.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://viewizard.com/linux debian/


```

I don't really know where the googleearth package comes from!

---

### Post by groeswenphil on 2007-03-14
OK...........I managed to get it to install........everything went nicely, then suddenly everything just vanished.
I can't see any reference to Google Earth in my program lists.

Now, about this.


sudo chmod 777 -R ~/.googleearth

You don't just copy that into Terminal do you?
Which bits do I change for my system.

Also, how do I get to and how long does it take to learn all these codes?

Thanks everybody,
Phil

---

### Post by jjalocha on 2007-03-14
A quick google tells you [how to use chmod]("http://www.analysisandsolutions.com/code/chmod.htm"). Instead of the numerical codes, you can set the permissions also with the **r**ead-**w**rite-e**x**ecute nomenclature. This way, you would type 
```

$ sudo chmod a+rwx -R ~/.googleearth

```
into your shell. Which means that **a**ll users have permission to **r**ead, **w**rite, and e**x**ecute.

I am not clear why you want to change the permissions, though. Have you tried executing the binary directly? Try the following in a shell:

```


$ ~/google-earth/googleearth &


```

---

### Post by DoorGunner on 2007-03-14
you need to be able to write all your saved locations to that directory.

---

### Post by BLTicklemonster on 2007-03-15
cd /home/bill/Desktop

sudo sh GoogleEarthLinux.bin

worked for me.

---

### Post by groeswenphil on 2007-03-16
Well, it looked like it was going to work, but then I got this in the terminal.

We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /root/.googleearth/crashlogs/crashlog-FB7D2013.txt

Sadly, I don't appear to be able to find the txt file and unless Google Earth starts up then I can't see how the Google Earth guys and galls will ever know about my bug.
Ho hum.
Now I'll never see my neighbour sunbathing in her garden.

All the best,
Phil

---

### Post by jhenager on 2007-03-16
groeswenphil - have you tried Synaptic, Add/Remove or Automatix as a way of installing this yet?
I know it is available via Automatix and almost certain about the other two.
It's a much easier way to install.

---

### Post by groeswenphil on 2007-03-16
Brilliant.

You know, I've got two well thumbed books on Ubuntu, Ubuntu Hacks and Ubuntu Linux for Non-Geeks.

I don't think either mentions Automatix.

I'm not sure whether I've got Google Earth working, but I've certainly got Real Player working within Firefox.........and that to me is miles more important. Now I can listen to all of my favourite shows on BBC radio.
Big thanks indeed,
Phil

---

