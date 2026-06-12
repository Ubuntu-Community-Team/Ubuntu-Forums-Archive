---
title: "Newbie in over his head"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2006-12-30
Guess I need a whole lotta help on this one. I was attempting to install automatix, but instead of using the commands for the Dapper version I mistakenly started using the ones for the Edgy version. I tried to exit the session but guess I did it wrong, now there is an icon in the upper right hand corner of the screen that wasn't there before. When I hover the pointer over it, I get message "An error occured, please run Package Manager from the right-click menu or apt-get on a terminal to see what is wrong. The error message was: "Error: opening the cache (E:Type 'exit' is not known on line 39 in source list /etc/apt/sources.list, E:The list of sources could not be read.)" It tells me to go to the repository to correct the problem. How do I do this or did I just mess up really bad. Sorry for the long winded post but I don't know how much info you might need to help me with this. Thanks in advance for your patience.

---

### Post by d3v1ant_0n3 on 2006-12-30
In the terminal (Applications>Accessories>Terminal if your menus are standard) copy and paste the following text ```
sudo gedit /etc/apt/sources.list
```

IT should promt for your password, then open the text editor with a file (sources.list - your repositories list). Copy and paste all of the text in that file on here- i'm guessing there's something in line 39 that there shouldn't be.

---

### Post by jerrynewt on 2006-12-30
# 
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
exit
tornado1
exit
wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)

login

---

### Post by d3v1ant_0n3 on 2006-12-30
> **jerrynewt said:**
> 
exit
tornado1
exit



Delete those lines from your sources.list file and then save it again.

To install Automatix the easy way, save the file from [ here ](http://www.getautomatix.com/wiki/index.php?title=Installation) ( you can find it in the 'Easy Direct Installation' section. When it's downloaded, right click on it and select 'Open with Gdebi Package Installer'. That should install it.

---

### Post by jordanmthomas on 2006-12-30
Is that your password in there?

---

### Post by d3v1ant_0n3 on 2006-12-30
> **jordanmthomas said:**
> Is that your password in there?


I was kinda wondering the same thing actually- I wa trying to work out what would require that pattern of user input.

---

### Post by Mimsy on 2006-12-30
> **jordanmthomas said:**
> Is that your password in there?

If it is, may I suggest changing it?

I know. I have a gift for pointing out the obvious. :)

/Mimsy

---

### Post by jerrynewt on 2006-12-30
Worked like a charm guys, thanks for the help--by the way that was my password. I was trying anything to quit the session--I know dumb, dumb, dumb, but I am learning and also I have changed the password, and things are looking up now. I think I am going to like the linux family- so far I have gotten all of the help I have needed--Think I have found a home---and it doesn't have ANY GATES!!

---

### Post by 3rdalbum on 2006-12-30
In a world without walls, who needs Gates?

---

### Post by Sef on 2006-12-30
> I know dumb, dumb, dumb

Not dumb.  You asked for help.   We all have made mistakes at times, and by asking, like you did, we have learned from them.

> All lines in the sources.list must begin with one of these three things:

#
deb
deb-src

If there's any lines in your source.list that don't begin with either of these three things, then put a # in front of them.

Good point, 3rdalbum.

---

### Post by dasunst3r on 2006-12-31
Also, for future reference, it is by convention that # is used to denote a comment in the configuration file and is to be ignored by the program.  This is also used for shell script programming.

Welcome to the Linux community!  We're gonna knock on Bill Gates' door and go like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=21937&stc=1&d=1167542161[/IMG]

---

### Post by MkfIbK7a on 2006-12-31
lol priceless

---

