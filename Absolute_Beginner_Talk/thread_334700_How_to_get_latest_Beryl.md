---
title: "How to get latest Beryl"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by Eddie Wilson on 2007-01-09
Good Day All,
I've installed Beryl on my Dapper os and I've noticed that its not the latest version. How would a person go about getting the latest Beryl version and how would you install it. Thanks  in advance for your help.
Eddie

---

### Post by gosh on 2007-01-09
What version do you have?
What repos do you use?

---

### Post by Eddie Wilson on 2007-01-09
I have the version in the ubuntu repos. I think that its version 1.01. I'm at work so I'm not really sure.
Eddie

---

### Post by bodhi.zazen on 2007-01-09
[How to Beryl](http://ubuntuforums.org/showthread.php?t=263851)

---

### Post by CowzRule on 2007-01-09
Open a terminal and put```
sudo gedit /etc/apt/sources.list
```Add the following to the list```
deb http://ubuntu.beryl-project.org/ dapper main
```Save the file then close.
In the terminal put```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```When that's finished put```
sudo apt-get update
```Then put```
sudo apt-get upgrade
```That will give you the latest version of Beryl.
If you want to try the "svn" versions (seems to be updated daily) replace > deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) dapper mainwith```
deb http://download.tuxfamily.org/3v1deb dapper beryl-svn
```and replace> wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -with```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```

---

### Post by Eddie Wilson on 2007-01-09
Thanks a lot. I will try that as soon as I get home. Its been a good day!
Eddie

---

### Post by Eddie Wilson on 2007-01-10
Well I finally got to apply the code listed by CowzRule. When I started Beryl it stated Beryl 0.1.1. I'm not sure if this is the latest Beryl. Everything does seem to work tho. How would a person check for the latest version?
Eddie

---

### Post by Eddie Wilson on 2007-01-10
Would it work out better if I used the svn versions?
Eddie

---

### Post by Sef on 2007-01-10
> Would it work out better if I used the svn versions?

svn versions are the bleeding edge, so stability is not as assured.  If you like bleeding edges, then go  for it, but be prepared for problems to crop up.

---

### Post by kpkeerthi on 2007-01-10
Are you still on Dapper? [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu) says "Beryl is not supported on Ubuntu Dapper. Please consider upgrading to a newer version of Ubuntu instead."

---

### Post by Eddie Wilson on 2007-01-10
Well it must not be supported. Today with beryl and xgl running my Dapper install is super slow. Not sure why. I do have the Edgy cd. Maybe I need to upgrade to that but I hate to lose stability. Thanks everybody for your help.
Eddie

---

### Post by jvc26 on 2007-01-10
I've had little stability issues with Edgy - its been one heck of a lot more stable than my old XP was ;) Anyhew, - I used to run Beryl on Dapper - is this just the new 0.1.4 that is not supported? I could run 0.1.1 on it without problems.
Il

---

### Post by PriceChild on 2007-01-10
I host one of the official beryl mirrors for ubuntu.

We no longer package and maintain packages for Ubuntu Dapper.

If you do decide to upgrade to Edgy to use our repositories please be aware Beryl isn't a very good reason to upgrade. Backup all data etc.

Pricey

---

### Post by Eddie Wilson on 2007-01-10
Is it true that with the new Nvidia drivers you don't need xgl or aiglx to run Beryl on Edgy?
Eddie

---

### Post by Eddie Wilson on 2007-01-10
Ok, Thanks Everybody.

---

### Post by PriceChild on 2007-01-10
With the newest nvidia drivers you can run without aiglx or xgl on xorg7.1 or above.

(You don't even need that but beryl haven't implemented it)

---

