---
title: "uh oh"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by zombietls on 2006-08-27
this is what i keep doing when i try install automatix

The following problems were found on your system:

E: Type 'http://www.getautomatix.com/apt' is not known on line 33 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

were do i go to fix it could someone help please

---

### Post by Bachstelze on 2006-08-27
Add 'deb ' (without quotes) before the URL.

---

### Post by zombietls on 2006-08-27
i did lol

---

### Post by zombietls on 2006-08-27
ok maybe ill just reinstall it all over again and retry from the begining because i keep getting the same error everytime i try doing it. even when i try to remove i get the same error

---

### Post by Bachstelze on 2006-08-27
Have you run sudo apt-get update ?

---

### Post by zombietls on 2006-08-27
no i havent, ill try that

---

### Post by zombietls on 2006-08-27
ok i tryied that and this is what i got

zombie@zombie-desktop:~$ sudo apt-get update
E: Type 'http://www.getautomatix.com/apt' is not known on line 33 in source list /etc/apt/sources.list
zombie@zombie-desktop:~$

---

### Post by mssever on 2006-08-27
Before you re-install, post your sources.list. We can probably spot the problem.

---

### Post by zombietls on 2006-08-27
how do i pull up my suorces

---

### Post by msak007 on 2006-08-27
> **zombietls said:**
> ok i tryied that and this is what i got

zombie@zombie-desktop:~$ sudo apt-get update
E: Type 'http://www.getautomatix.com/apt' is not known on line 33 in source list /etc/apt/sources.list
zombie@zombie-desktop:~$

Did you include the whole line when copying / pasting? I don't see the "dapper main" part at the end. Here's how the entry should look in your sources.list:

```
deb http://www.getautomatix.com/apt dapper main

```

---

### Post by mssever on 2006-08-27
> **zombietls said:**
> how do i pull up my suorces

Open /etc/apt/sources.list and copy the contents of the file here.

---

### Post by zombietls on 2006-08-27
> **msak007 said:**
> Did you include the whole line when copying / pasting? I don't see the "dapper main" part at the end. Here's how the entry should look in your sources.list:

```
deb http://www.getautomatix.com/apt dapper main

```

ya i tried that before to and got same thing

---

### Post by zombietls on 2006-08-27
zombie@zombie-desktop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
zombie@zombie-desktop:~$


?????

---

### Post by christhemonkey on 2006-08-27
You need to do what Hymn To Life says to do, so the line in /etc/apt/sources.list looks like this:
```
deb http://www.getautomatix.com/apt dapper main 
```

To open the file do:
```
gksudo gedit /etc/apt/sources.list 
```

---

### Post by mssever on 2006-08-27
> **zombietls said:**
> zombie@zombie-desktop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
zombie@zombie-desktop:~$


?????

Try ```
sudo gedit /etc/apt/sources.list
``` The sudo is only necessary if you want to change the file.

---

### Post by zombietls on 2006-08-27
i did and i get same thing ill try again though

---

### Post by mssever on 2006-08-27
Did you catch my edit? I made a typo in the command I gave.

---

### Post by zombietls on 2006-08-27
i did this 
sudo gedit /apt/sources.list, with and without sudo and it open a text document but there was nothing in it ??

---

### Post by zombietls on 2006-08-27
lol hold on i got it after i posted

---

### Post by zombietls on 2006-08-27
ok i pasted that in and this is what pulled up 


deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
[http://www.getautomatix.com/apt](http://www.getautomatix.com/apt)
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt)
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt)
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

---

### Post by christhemonkey on 2006-08-27
You need to remove 3 of those lines at the end, like this:
```
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://www.getautomatix.com/apt dapper main

```

---

### Post by zombietls on 2006-08-27
i just delte them and save it

---

### Post by christhemonkey on 2006-08-27
Delete those 3 lines, save the file.
Run:
```
sudo apt-get update 
```

Then continue with your automatix loving.

---

### Post by zombietls on 2006-08-27
ok so it has seemed to work lol wish i was that good so what do i do from here

---

### Post by zombietls on 2006-08-27
do i select everything to install

---

### Post by mssever on 2006-08-27
You need to delete all getautomatix lines except the last--or else comment them out by putting # at the beginning of the line.

EDIT: christhemonkey beat me to it...

---

### Post by zombietls on 2006-08-27
i deleted them and it seem to work, i clicked on mark all possible upgrades, how do i upgrade now ??

---

### Post by mssever on 2006-08-27
Select whatever you want from the menu.

---

### Post by mssever on 2006-08-27
Hit the apply button...or OK...or whatever it's called.

---

### Post by zombietls on 2006-08-27
ok i also typed in the terminal this: sudo apt-get update 
will that work just as well or no

---

### Post by christhemonkey on 2006-08-27
That will make your system upto date by performing an upgrade.

You should type:
```
sudo apt-get install automatix 
```
When its complete.

---

### Post by zombietls on 2006-08-27
i guess it worked it did something so, how would i go about hooking up another hard drive that has my music on it i just shut down hooked it up and now its not mounting 

Unable to mount the selected volume.

error: device /dev/hdb1 is not removable

error: could not execute pmount

---

### Post by mssever on 2006-08-27
What kind of hard drive is it? USB? IDE?

---

### Post by zombietls on 2006-08-27
it is an IDE

---

### Post by zombietls on 2006-08-27
well dont want to say it but i dont think that it worked anyways here is what i got trying to play mp3

You do not have a decoder installed to handle this file. You might need to install the necessary plugins.

---

### Post by zombietls on 2006-08-27
it is also still missing the java runtime

---

### Post by mssever on 2006-08-27
OK...you need to set up an fstab entry for it. You need to find out several things: First, what is the device name? It will be something like /dev/hda, /dev/hdb, /dev/hdc, etc., depending on how it's hooked up on the IDE chain. The way I know to find this out is to try the various possibilities one at a time. /dev/hda is your first HD, so it's probably not the name of the new one.

Next, what type is the filesystem? FAT32 (vfat in linux)? NTFS? ext2/3?

Now, make an empty folder where you want the files to appear. I'll use /media/music for this example, but you can use whatever you want.

Assuming it's vfat and called /dev/hdb1 (the 1 is for the first--or only--partition on the disk), add the following line to /etc/fstab:
```
/dev/hdb1       /media/music          vfat    defaults,utf8,umask=007,gid=46 0       1

``` Make sure to change the first field to your actual device, the second field to the mount point, and the third field to the filesystem type (vfat or ntfs). If your disk has a different filesystem than NTFS or vfat, then you'll have to make more changes.

---

### Post by mssever on 2006-08-27
> **zombietls said:**
> well dont want to say it but i dont think that it worked anyways here is what i got trying to play mp3

You do not have a decoder installed to handle this file. You might need to install the necessary plugins.

If you can see the files on your disk, then it's already mounted.

for MP3s, use automatix to get w32codecs and whatever other media stuff you might need. I think you can get the Java runtime from there, as well. If it isn't in automatix, it's in Synaptic

---

### Post by zombietls on 2006-08-27
um lol i have no idea what you were saying about getting an fstab and i put in an mp3 cd and got the error

---

### Post by zombietls on 2006-08-27
how do i use automatix to get these files ?? sry but im new to this

---

### Post by mssever on 2006-08-27
> **zombietls said:**
> um lol i have no idea what you were saying about getting an fstab and i put in an mp3 cd and got the error
See my post above explaining this. If there's something in those instructions you don't understand, let me know.
> **zombietls said:**
> how do i use automatix to get these files ?? sry but im new to this
Type the following lines one at a time:
```
sudo apt-get automatix
automatix
```

---

### Post by zombietls on 2006-08-27
i have somewhat figured out how to use this synaptic package manager which mp3 option should i use i alread installed mp32ogg should i install mp3blaster what else should i do

---

### Post by mssever on 2006-08-27
> **zombietls said:**
> i have somewhat figured out how to use this synaptic package manager which mp3 option should i use i alread installed mp32ogg should i install mp3blaster what else should i do

If you can't play MP3s, you need the MP3 codecs. You can get them from Synaptic if you enable the additional repositories (see [http://psychocats.net/ubuntu/sources)](http://psychocats.net/ubuntu/sources)), or, you can use automatix.

---

### Post by mssever on 2006-08-27
Get w32codecs, gstreamer-plugins-bad and gstreamer-plugins-ugly

---

### Post by mssever on 2006-08-27
Another option is to install totem-xine and libxine-extracodecs

---

### Post by zombietls on 2006-08-27
one last thing how do i use automatix and synapse and how do i Get w32codecs, gstreamer-plugins-bad and gstreamer-plugins-ugly

---

### Post by mssever on 2006-08-28
Here are instructions for installing software: [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

And using automatix is simple. Select it from the menu, or type automatix. Check the boxes for what you want, hit OK and follow the instructions.

---

### Post by zombietls on 2006-08-29
> **mssever said:**
> 

And using automatix is simple. Select it from the menu, or type automatix. Check the boxes for what you want, hit OK and follow the instructions.

i did that but could not find the mp3 codecs that you listed for me to find

---

### Post by mssever on 2006-08-29
Looks like they changed what they call it. Multimedia codecs should get you what you need.

---

