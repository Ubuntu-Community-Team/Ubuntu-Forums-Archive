---
title: "Time Black Hole"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by CtrlAltDelete on 2006-11-25
I keep throwing time into this OS... nothing...I really want it to work... therefore I am going to stick totally with it for at least a month...

That being said: 

I have been reading through these forums for hours. I have Beezy because thats what I recieved in the mail.


1)I would like to have edgy but I can't work the cd writer
2)I can't work my linksys wireless card although direct hook up through an ethernet cord works
3)Easyubuntu and automatix seem imppossible to download especially when i get an "could not get lock /var/lib/dpkg/lock
or unable to lock admistration directory
4)Can I get my tuner card to work on this?(distant goal at this point)
5)I can;t get dvd's to play...no codec i guess
6)I kinda wish there was some sort of plug and play here or easy button
7)it would be nice to change themes or wallpaper but where do i do this
8)Is there a simple map or guide to get this show rolling

WHere is the easy button?

---

### Post by taurus on 2006-11-25
Hopefully, these guides would answer some of your questions...

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by CtrlAltDelete on 2006-11-25
thanks for your quick responce

---

### Post by CtrlAltDelete on 2006-11-25
Ok Now I am trying to upgrade my Beezy to Dapper so i can eventaully get to Edgy..

From my understanding i need to replace all teh breezy with dapper in my etc/apt/sources.list

this file is read only ... what needs to be done?

then all i have to do is 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

---

### Post by msak007 on 2006-11-25
You may also find this []("http://www.psychocats.net/ubuntu/")site extremely useful:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by CtrlAltDelete on 2006-11-25
Quickly browsing through that website helps a bunch... but following the directions, I am still left with the proble that the my source.list file that is need to be changed is read-only. How do will i be able to modify this

---

### Post by msak007 on 2006-11-25
> **CtrlAltDelete said:**
> Quickly browsing through that website helps a bunch... but following the directions, I am still left with the proble that the my source.list file that is need to be changed is read-only. How do will i be able to modify this
Well, in Linux you don't have administrator rights to the entire system. When you log in as yourself, by default you only have access to any files / folders in your "home" directory. In order to gain access to system files, such as sources.list, you must use "sudo". If you want to edit your sources, type the following in the terminal:
```
gksudo gedit /etc/apt/sources.list
```This will open gedit as an administrator (root) and allow you to edit the file. Save it and then open Synaptic again, and refresh the sources.

---

### Post by CtrlAltDelete on 2006-11-25
adam@ubuntu:~$ gksudo gedit /etc/apt/sources.list
(gedit:8366): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by msak007 on 2006-11-25
Try just using sudo instead of gksudo and see if that works.

---

### Post by Cannaregio on 2006-11-25
Had similar problems.
1) use sudo instead of gksudo, as msak007 says
2) don't try to update directly breeze-->edgy
   if you can make a _fresh_ edgy install

I have at the moment 3 laptops on dapper and the main desktop on edgy. The upgrade of this desktop went well, BUT the edgy I installed on a fifth box (of a friend) runs BETTER than my desktop I upgraded from dapper myself.

So my small 2 eurocents are: if you can fresh install, instead of upgrading edgy from dapper that's better.

Wish you luck

---

### Post by CtrlAltDelete on 2006-11-25
Thanksyou for your support. I completed the steps now to get to Drapper. I am not sure I am there. When i got to the update manager now and try to upgrade.. it is saying failed to fetch cdrom[ ubuntu 5.10_dapper badger release

---

### Post by taurus on 2006-11-25
Just put a # in front of the first line to comment out the CD-ROM thing in your /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by msak007 on 2006-11-25
I also like fresh installs, and even though one of Ubuntu's supposed advantages is that you can dist-upgrade to a new version instead of formatting and reinstalling, I tend to format and reinstall. I found that creating a separate /home partition is especially useful for the semi-annual formats and reinstalls. But I believe the OP said he was having problems with his burner, and that's why he couldn't burn a copy of Edgy. If he's successful in updating to Edgy and can burn the CD, then maybe he can format and reinstall.

---

### Post by CtrlAltDelete on 2006-11-25
Is this what you mean... I added a pound to teh first line since i can not cd place you are talking about. My hope is that I can be watching dvds on this thing by 2nite!

#deb cdrom:[Ubuntu 5.10 _dapper Badger_ - Release i386 (20051012)]/ dapper main restricted


deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricted

---

### Post by CtrlAltDelete on 2006-11-25
I would love to fresh install... I ordered install disk for dapper yesterday.  In the mean time i am hoping i can fix all my problem.. Ubuntu seems soo awesome if i can get rolling

---

### Post by CtrlAltDelete on 2006-11-25
Ok using a ## worked and upgrading is in session. Thankyou guys... this forum is awesome. I appreciate the time you invested in me

---

