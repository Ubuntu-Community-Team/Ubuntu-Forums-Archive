---
title: "install unrar"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by amadeco on 2006-05-06
hello everybody 
i am absolutely new to this and i have got no idea how to install unrar, so i searched and found this [http://ubuntuforums.org/showthread.php?t=1070](http://ubuntuforums.org/showthread.php?t=1070) but i dont know how to add something to sources.list and how and is there another way {easy} to install unrar , i need to unrar a file in parts. 
{please answer in a way which is understandable for a total dummie lol thanks}
any help is much appreciated...
thanks

---

### Post by kingmonkey on 2006-05-06
[http://ubuntuguide.org/#rar](http://ubuntuguide.org/#rar)

---

### Post by amadeco on 2006-05-06
thanks kingmonkey but this can not work for me as i have modified my sources.list. when i try to restore the old one there is an error. what i would need is either the original sources.list file, so i can istert that or an alternate way to install unrar.


any help????


thanks

---

### Post by richbarna on 2006-05-06
If you are using Ubuntu Breezy, 
Open your console and copy and paste this :-
> sudo gedit /etc/apt/sources.list
when it opens with your text editor (gedit)
Delete all the lines and copy and paste this :-
 > deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

## created by arnielistenadded

 
Save and exit.

Next in your console again, copy and paste this :-
> sudo apt-get update

A load of text will scroll down and everything should be ok.> 

---

### Post by amadeco on 2006-05-06
Thank you richbarna

much appreciated i suppose that unrar is included now or am i wrong?
thanks

---

### Post by confused57 on 2006-05-06
Definitely do what richbarna instructed.

If you're using Breezy, you might want to look into installing Automatix, which "automatically" installs a lot of programs, codecs,Newer Firefox,rar, etc:

[http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)

---

### Post by richbarna on 2006-05-06
Hi again Amadeco, confused57 has a good point, Automatix installs practically everything you need with a nice GUI interface.

Open your console and type :-
> sudo apt-get install automatix

and for unrar (there are two types; free and nonfree) i use the nonfree version :-

> sudo apt-get install unrar-nonfree

Happy Hackin' ; )

---

### Post by amadeco on 2006-05-07
thank u it was really helpful

cheers

---

