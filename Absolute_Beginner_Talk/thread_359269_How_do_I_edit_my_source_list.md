---
title: "How do I edit my source list???"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by matheuu on 2007-02-11
Is it Posssible to edit my source list? 
I have tried to erase this problem line from the list but it wont let me.


oem@mat:~$ sudo apt-get update
Password:
E: Type 'wget' is not known on line 37 in source list /etc/apt/sources.list



Help 
Mat

---

### Post by coastdweller on 2007-02-11
Post your entire sources.list file

---

### Post by nickoli_02 on 2007-02-11
I'd recommend making a backup first before changing sources.list:

```
cp /etc/apt/sources.list /etc/apt/sources.list_bkp
gksudo gedit /etc/apt/sources.list
```

In general, the only editing you want to do to your sources.list file is adding/removing repositories. You can comment out repositories using #, and uncomment restricted repositories by removing the # in front of the entries.

---

### Post by matheuu on 2007-02-11
HI

I have four source list files in the apt. THis one is just plain old source list.
 
I highlighted the line below.


deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

# 
# #deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial maindeb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
## Automatix repo
**wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)**
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -
&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main&#8221;
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse



Cheers
Mat

---

### Post by matheuu on 2007-02-11
oem@mat:~$ cp /etc/apt/sources.list /etc/apt/sources.list_bkp
cp: cannot create regular file `/etc/apt/sources.list_bkp': Permission denied
oem@mat:~$ gksudo gedit /etc/apt/sources.lis

wouldn´t let me make a back up!

Um.. which list should I be putting the #&#347; in  there is the .... sources.list   ......   sources.list.d ....... sources.list.save     and  sources.list-eu-2007-2-7-23-19-44

---

### Post by taurus on 2007-02-11
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_bkp
```

---

### Post by meng on 2007-02-11
You need to use sudo:

sudo nano -B /etc/apt/sources.list

will create a backup AND give you a text editor.
Either delete or place # in front of the 3rd, 4th, 5th and 6th lines from the bottom. No idea how they got in there - that's a complete mess!!

```
wget http://www.getautomatix.com/apt/key.gpg.asc
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -
&#8220;deb http://www.getautomatix.com/apt edgy main&#8221;
```

---

### Post by nickoli_02 on 2007-02-11
oops, forgot you had to be superuser to copy files. Apt-get uses the sources.list file. Any other file similar to sources.list (ie sources.list.d, sources.list_bkp) will be ignored. You only want these if you make a mistake and want to restore the file how it was before.

The lines you want to uncomment include a URL. These are the repositories apt-get uses to retrieve packages. The default sources.list comes with some restricted repositories (which are commented so apt doesn't see them by default) for legal reasons. These repos include non-free software that Ubuntu can't legally use by default.

---

### Post by nickoli_02 on 2007-02-11
Ohh I see your problem. You recently installed (or was trying to) Automatix right? The line highlighted with wget, and the other two below it, are not supposed to be included in the sources.list file. You were supposed to type these into the terminal. You can remove these, and leave the rest of the lines.

---

### Post by matheuu on 2007-02-11
Hey meng, 
That worked a treat.

I think those lines got in there when I was trying to load automatix from their site?

One big last question ... If you dont mind.....  where is the best place to learn how to operate the  Ubuntu system..... Im coming from using windows ..... and I didn´t really know what I was doing with that ..didnt really wat to know.. .... But for some reason I am very keen on learning how to get around in Ubuntu... I like it


mat

---

### Post by matheuu on 2007-02-11
Thanks Nickoli.

That makes sense.. thanks for the help... now I have 5 sources.list.... files!! cool.


So if I was to un hash all the hashed up urls in my source.list I would have access to more repositories.... also cool.
If I can get my head round this hopefully I´ll be helping newbies aswell some time! 


Thanks.

---

### Post by meng on 2007-02-11
Wow we seem to be getting a lot of Australians here lately (I'm Australian myself, just overseas right now). There are many places to look for guidance. These forums, of course.
[www.psychocats.net/ubuntu](www.psychocats.net/ubuntu)
[www.ubuntuguide.org](www.ubuntuguide.org)
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

---

### Post by matheuu on 2007-02-11
Meng
OS .. where bouts? fun? Its raining in sydney

Could have something to do with that new vista thing just being released..... new opperating systems ........ $$MS$$.... bit of a google..... find Ubuntu ....Free ... down load and try right now  or go down the shops and hand Mr gates a whole bunch of cash....

Anyway since I loaded ubuntu about 2 weeks now I have been spreading the word to most people who will listen......

---

### Post by meng on 2007-02-11
Rochester, Minnesota, it's been below freezing all week. At least we only got 3 inches of snow, not 100 like in New York.

---

### Post by matheuu on 2007-02-11
Way to cold. Perfect week end on the beach near Newcastle....rained in sydney....not enough thought to save us from losing to the Poms......well almost a perfect weekend... I&#7743; assuming you aready heard.....ah well we will kill them in the Carribean..... I don´t even like cricket....

---

### Post by meng on 2007-02-11
The team needed a wake up call.

---

### Post by nickoli_02 on 2007-02-11
Welcome to linux :) the only way to learn is to use it, so stick with it and you'll come to enjoy it much more than windows. Then you'll come to a point where you wonder why anyone ever used windows at all?

---

