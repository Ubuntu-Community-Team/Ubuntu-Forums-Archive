---
title: "Installing Breezy again"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by KeyboardJockey on 2006-05-14
I seem to have completly broken my installation but not knowing what I'm doing.  Can anyone give me step by step plain English instructions on how to re install Breezy without affecting my data that I already have on the drive.

I really don't want to lose my data but I messed up the system before I got a chance  to back up my data.

Can anyone help on this one.

I think that my install is terminally broken and nothing can rescue it as it is an apt-get problem.  Installing Automatix has just made things much much worse.  Here is the output from the terminal.  The apt.conf.d  on the first  line is highlighted in blue text btw if thathelps. 

marc@marc:~$ ls -l /etc/apt/
total 88
drwxr-xr-x  2 root root  4096 2006-05-12 23:22 apt.conf.d
-rw-------  1 root root     0 2006-05-12 22:42 secring.gpg
-rw-r--r--  1 root root  2133 2006-05-14 14:14 sources.list
-rw-r--r--  1 root root  2131 2006-05-14 14:11 sources.list~
-rw-r--r--  1 root root  1865 2006-05-13 22:50 sources.list_backup_200605141017
-rw-r--r--  1 root root  2129 2006-05-14 12:28 sources.list.save
-rw-------  1 root root  1200 2006-05-14 10:16 trustdb.gpg
-rw-r--r--  1 root root 30390 2006-05-14 10:17 trusted.gpg
-rw-r--r--  1 root root 29464 2006-05-14 10:16 trusted.gpg~
marc@marc:~$
marc@marc:~$ sudo apt-get update
Password:
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [30.9kB]
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy Release.gpg
Get:7 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy Release
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [59.8kB]
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Sources
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [39.0kB]
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Packages
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Sources
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [18.6kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14.0kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [26.1kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [17.2kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [35.0kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [5007B]
Fetched 300kB in 21s (14.2kB/s)
Reading package lists... Done
marc@marc:~$ apt-get -f install
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
marc@marc:~$

---

### Post by catlett on 2006-05-14
You need to put sudo before running apt-get. That is why it says locked. Try running these commands to see if you can clean things up ```
sudo apt-get update
``` Then enter ```
sudo apt-get dist-upgrade
``` This will refresh apt-get and install the latest breezy packages available.

P.S. I just looked more closely. You are using sudo. Could your superuser file be messed up? Sudo should work unless the user you are using doesn't have superuser priveleges.
Why can't you back up your data?

---

### Post by catlett on 2006-05-14
If you think Automatix messed it up you can do two things to reverse it. First change your apt-get source list back to the breezy original. Open the list in a text format you can edit.```
 sudo /etc/apt/sources.list
```
Erase that whole list and replace it with this 
> ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
Then you can rub ```
sudo apt-get update 
```and ```
sudo apt-get dist-upgrade
```
You can remove the software installed by following the directions on this thread [http://ubuntuforums.org/showthread.php?t=90797](http://ubuntuforums.org/showthread.php?t=90797)

---

### Post by Kvark on 2006-05-14
[QUOTE=catlett]P.S. I just looked more closely. You are using sudo.[/QUOTE]
He used sudo to update and that worked fine. But he did not use sudo to install and thats why it didn't work.

KeyboardJockey, you do not have permission to install things or mess with anything else outside of your home dir. Only root is allowed to do that. So you need to use sudo to execute the install command as root.

The difference between root and your normal user account may seem strange if you are the only one using the computer. It is good because the less time you spend as root the less risk there is that you accedentally mess up the whole system. And only programs that you use with sudo can mess up or take over the whole system if they would contain bugs or even trojans. Also if you give someone else access to your computer then don't give their account the right to use sudo to become root, that way they can only mess up their own home dir, the rest of your computer is safe from whatever stupid things they may try.

---

### Post by KeyboardJockey on 2006-05-14
[QUOTE=catlett]You need to put sudo before running apt-get. That is why it says locked. Try running these commands to see if you can clean things up ```
sudo apt-get update
``` Then enter ```
sudo apt-get dist-upgrade
``` This will refresh apt-get and install the latest breezy packages available.[/QUOTE]


I've done this and the TW did't show any errors of the /var file sort.
[QUOTE=catlett]
P.S. I just looked more closely. You are using sudo. Could your superuser file be messed up? Sudo should work unless the user you are using doesn't have superuser priveleges.
Why can't you back up your data?[/QUOTE]

It may well be a superuser file problem.  I used the same password anduser name for the system on the new drive and on the old drive.  Would that be causing the problem?

I don't thnk I have enough CD's back the data up for all the data I want to save and the shops are shut at present.

---

### Post by catlett on 2006-05-14
Wait for the shops to open and get more cds before you do anything. Right now your system is running good enough to copy your data to cds. You can then reinstall if you think it is best.
I don't know a whole lot about the superuser file because it is made by default during install. If the user name and password you are using was made during install it should be fine.
Did you see the previous post about sudo when installing? Have you been using sudo for installations? Since you are looking for amule when all this started try ```
sudo apt-get install amule
```
See what happens. If you ran the apt-get update and the apt-get dist-upgrade and no errors came up you should be alright. Are any other errors coming up?

---

