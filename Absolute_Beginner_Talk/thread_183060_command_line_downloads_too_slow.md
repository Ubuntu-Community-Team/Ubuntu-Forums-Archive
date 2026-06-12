---
title: "command line downloads too slow"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-05-27
when i install sudo apt-get install <package>

command line downloads the packages at 2.+kb/sec. it is too slow. how can i increase its speed.

---

### Post by el3ktro on 2006-05-27
what do you mean with 2.+ ?? Download sped depends on the type of Internet connection you have, and on the mirror you're using.

Tom

---

### Post by u04f061 on 2006-05-27
[QUOTE=el3ktro]what do you mean with 2.+ ?? Download sped depends on the type of Internet connection you have, and on the mirror you're using.

Tom[/QUOTE]

i mean 2.0kb/s,2.09kb/s etc
i know this but can't we increase it by download managers.

---

### Post by el3ktro on 2006-05-27
[QUOTE=u04f061]i mean 2.0kb/s,2.09kb/s etc
i know this but can't we increase it by download managers.[/QUOTE]

How do you think this should work? If your internet connection can't do more than 2.0kb/s then it's technically not possible to download at a higher speed! what kind of internet connection do you have?

Tom

---

### Post by sYs^ on 2006-05-27
Open up a terminal and type:

cat /etc/apt/sources.list

Then copy here the output, thx :p

Where are you from? Might you'll need another mirror located nearer to you.

---

### Post by u04f061 on 2006-05-27
here is the output
ejaz@ejaz:~$ cat /etc/apt/sources list
cat: /etc/apt/sources: No such file or directory
cat: list: No such file or directory
ejaz@ejaz:~$

---

### Post by sYs^ on 2006-05-27
lol sorry there was a typo

cat /etc/apt/sources.list

try this :p

---

### Post by u04f061 on 2006-05-27
thnx for recheckin
here is this
ejaz@ejaz:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse

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

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

##deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy universe
ejaz@ejaz:~$

---

### Post by sYs^ on 2006-05-27
Where are u from? You're using US mirrors if you live in a different country then you should use a nearer mirror.

---

### Post by u04f061 on 2006-05-27
[QUOTE=sYs^]Where are u from? You're using US mirrors if you live in a different country then you should use a nearer mirror.[/QUOTE]

i am in pakistan located in asia.ok tell me do we specify mirror in command line or it is prespecified in sources.list
if i should use asian mirror,how can i ?

---

### Post by sYs^ on 2006-05-28
Well, I just checked this page: [https://wiki.ubuntu.com/Archive]("https://wiki.ubuntu.com/Archive") and didn't find any pakistan mirror, but I think you should try a few from the nearer countries.

Like:

**China**
[LIST]
[*]  [http://debian.cn99.com/ubuntu/]("http://debian.cn99.com/ubuntu/")
[*]  [http://mirror.lupaworld.com/ubuntu/]("http://mirror.lupaworld.com/ubuntu/")[/LIST]**Turkey**[LIST]
[*]  [http://godel.cs.bilgi.edu.tr/mirror/ubuntu/]("http://godel.cs.bilgi.edu.tr/mirror/ubuntu/") (i386)
[*]  [ftp://godel.cs.bilgi.edu.tr/ubuntu/]("ftp://godel.cs.bilgi.edu.tr/ubuntu/") (i386)[/LIST]**Russia**[LIST]
[*]  [http://debian.nsu.ru/ubuntu/]("http://debian.nsu.ru/ubuntu/") (i386 and amd64)
[*]  [ftp://debian.nsu.ru/ubuntu/]("ftp://debian.nsu.ru/ubuntu/") (i386 and amd64)[/LIST]For example, if you want to you use a chinese mirror, then you should change your /etc/apt/sources.list like this: (sudo gedit /etc/apt/sources.list)

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://debian.cn99.com/ubuntu/ breezy main restricted
deb-src http://debian.cn99.com/ubuntu/ breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://debian.cn99.com/ubuntu/ breezy-updates main restricted
deb-src http://debian.cn99.com/ubuntu/ breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://debian.cn99.com/ubuntu/ breezy universe multiverse
deb-src http://debian.cn99.com/ubuntu/ breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://debian.cn99.com/ubuntu/ breezy-backports main restricted universe multiverse
deb-src http://debian.cn99.com/ubuntu/ breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

##deb http://debian.cn99.com/ubuntu// breezy universe
```

---

### Post by Offthedeepend on 2006-05-28
I am currently in China and have had similar slow downloads for updates.  I would like to try your suggestion sYs^, to see if it improves, but a couple of questions before I do:

First, I'm using Dapper, so is there anything I would need to change from your last post apart from changing "breezy" to "dapper" in the sources list?  

Also, are the mirrors (in China for example) basically the same, and up to date, as others in the US or Europe?  You probably already know, there is frequently slow connections/blocking difficulties accessing international websites from inside China, so I'm curious if the mirrors are the same.

Thanks for your advice.

PS.  I'm not trying to hijack the thread, but my problem is similar to the OP, so thought I would ask here first.

---

### Post by u04f061 on 2006-05-28
i have changed my mirrors from us to china still my download is slow as before.i think pakistan is treating both mirrors as international without caring distance.is'nt it?

---

### Post by sYs^ on 2006-05-28
[quote=Offthedeepend]
First, I'm using Dapper, so is there anything I would need to change from your last post apart from changing "breezy" to "dapper" in the sources list?  [/quote] 
No, I think that will just do the trick or you can use your own sources.list and just change all "[http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu")" urls to the chinese one. 

[quote=Offthedeepend] Also, are the mirrors (in China for example) basically the same, and up to date, as others in the US or Europe?  You probably already know, there is frequently slow connections/blocking difficulties accessing international websites from inside China, so I'm curious if the mirrors are the same.[/quote] 

Yes, I know about the chinese goverment's internet policy, I think those mirrors must be the same to the officials, because if they werent equal then it would be unmeaning to keep up them. There can be a little delay between the updates because the maintainers need some time to synchronize them.

[quote=u04f061]
i have changed my mirrors from us to china still my download is slow as before.i think pakistan is treating both mirrors as international without caring distance.is'nt it?[/quote] 
What kind of bandwith do you have? Try the others too. Unfortunately I don't know the ISPs in Pakitsan and if they restrict international bandwith. (But they shouldn't :>)

---

### Post by Offthedeepend on 2006-05-28
Just to follow up, I changed my sources list as suggested and download of updates was much faster, so thanks for your help.  :D 

For the benefit of other Dapper users in China, my sources list is below, but I'm new to all this, so hope it's correct...

u04f061, I wish I could help with the problem you're having in Pakistan, but like I said, I'm a noob.  Did you try the other mirrors?  I hope others here can help you through it.  Good luck!  

-------------------
## Uncomment the following two lines to fetch updated software from the network
deb [http://debian.cn99.com/ubuntu/](http://debian.cn99.com/ubuntu/) dapper main restricted
deb-src [http://debian.cn99.com/ubuntu/](http://debian.cn99.com/ubuntu/) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://debian.cn99.com/ubuntu/](http://debian.cn99.com/ubuntu/) dapper-updates main restricted
deb-src [http://debian.cn99.com/ubuntu/](http://debian.cn99.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://debian.cn99.com/ubuntu/](http://debian.cn99.com/ubuntu/) dapper universe multiverse
deb-src [http://debian.cn99.com/ubuntu/](http://debian.cn99.com/ubuntu/) dapper universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

deb [http://debian.cn99.com/ubuntu/](http://debian.cn99.com/ubuntu/) dapper-backports main restricted universe multiverse 
deb-src [http://debian.cn99.com/ubuntu/](http://debian.cn99.com/ubuntu/) dapper-backports main restricted universe multiverse

---

### Post by u04f061 on 2006-05-28
plz can u tell me how much is the difference of download speed between two is.it was working poorly than us mirror,so i changed that and came up to us again

---

### Post by sYs^ on 2006-05-28
It depends on your connection.

---

