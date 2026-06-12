---
title: "[SOLVED] A lot of packages are not found!? Why!?"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by RonB123123 on 2006-07-31
A lot of packages are not found!? Why!?

I recently reinstalled Ubuntu and did all the updates and rebooted a few times. Then I tried to install Firestarter, Flash, and Java. For each of those I did the exact command that the [Ubuntu Starter Guide](http://ubuntuguide.org/wiki/Dapper) specified, and it said the package was not found.

I tried using each command with and without sudo. I got the same error.

Ubuntu did the same thing last time I installed it, but then in 2 or 3 days, the packages magically appeared and I didn't manual install them. Is this a bug or something? I searched on the forums, but I couldn't find any information on it.

I also checked the Synaptic Packet Manager and searched for Firestarter, Flash, and Java. Java came up with some results, but didn't come up with the same packages I had last time. 

Reply back soon. Thank you.

---

### Post by djsroknrol on 2006-07-31
You might try updating your sources.list...and check:
System>Admisistration>Package Manager to adjust your settings...it sounds like your on auto update...;)

---

### Post by catlett on 2006-07-31
You have to add the repository list from the Dapper guide. It is at the beginning of the guide it tells you to enter this command 
```
sudo gedit /etc/apt/sources.list
```Then to erase everything in the file and copy/paste this list in
> ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-freeThen run this command to update the systems repository cache ```
sudo apt-get update
```
Then you follow the guide.

This is the section. [http://doc.gwos.org/index.php/DapperGuide#How_to_add_extra_repositories](http://doc.gwos.org/index.php/DapperGuide#How_to_add_extra_repositories)

---

### Post by RonB123123 on 2006-07-31
Thank you so much Catlett.

It worked!!! :) Thank you!!!

---

### Post by catlett on 2006-07-31
Your more than welcome. The Dapper Guide is what I use when I install a new system. Just don't forget to go to the restricted formats section and get the win32codecs [https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5](https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5)
That is two commands. Cut/paste the wget command and then cut/paste the sudo dpkg command. I might as well post it here.
```
wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb
```
```
sudo dpkg -i w32codecs_20060611-0.0_i386.deb

```You should also install mpg123 and vorbis tools. This gives you a "cool" little feature. After you install this, if you have an mp3 file on your desktop (it can be anywhere but if it;s on your desktop you can do it whenever) you just hover your mouse over the file and it plays. No media player or music player is launched. The file just plays. Here is the command.
```
sudo apt-get install mpg321 vorbis-tools
```
When I am bored I mess around with these sound effects on my desktop. They are free. Nothing great but different i.e. gunshot, waves, "I'll be back", "yo quiero taco bell" you get the idea [http://simplythebest.net/sounds/MP3/MP3_sounds.html](http://simplythebest.net/sounds/MP3/MP3_sounds.html)

Enjoy Ubuntu. See you around the forum.

---

