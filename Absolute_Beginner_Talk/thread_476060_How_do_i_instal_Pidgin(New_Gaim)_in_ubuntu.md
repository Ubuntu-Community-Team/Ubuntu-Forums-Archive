---
title: "How do i instal Pidgin(New Gaim) in ubuntu"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Robert98374 on 2007-06-16
As the title is stated...
I would love to be able to use Pidgin since you can put themes on Pidgin and not gaim :-)

---

### Post by skymera on 2007-06-16
download pidgin

```
 wget http://download.ubuntu.pl/_Feisty_Fawn/pidgin/pidgin_2.0.0-1_i386.deb 
```

install

```
 sudo dpkg -i pidgin_2.0.0-1_i386.deb 
```

---

### Post by Kosimo on 2007-06-16
You can do it by downloading the source code and compile it... But if you want a very esasy way (and last version)

Go to [http://www.getdeb.net](http://www.getdeb.net)

Download the last version 2.0.2, (first data, and then pidgin)  are just two debs, double click on them
Done.

;)

---

### Post by Robert98374 on 2007-06-17
Thanks,
Especially for that website, tried the terminal codes but they didnt work...

---

### Post by Kosimo on 2007-06-18
> **Robert98374 said:**
> Thanks,
Especially for that website, tried the terminal codes but they didnt work...

I really like that website.
Almost all debs works pretty well, in my opinion a site to trust in. You'll always find almost any latest version in a easy deb file.

---

### Post by Robert98374 on 2007-06-20
Kewl ill keep that in mind i already have tried some other stuff from there and loving it :)

---

### Post by meborc on 2007-06-20
sometimes the deb's from getdeb.net will not install oob... then you need to run "sudo apt-get -f install" to get all the dependencies and then you are fine

never before had a major problem with getdeb... only few days back the GLEST deb got compromised :)

---

### Post by fox1 on 2007-07-24
Hi

why I must instal Pidgin this way? Why there is no possibility to instal it through Synaptic or Add remove application? And why the terminal codes from the first post do not work?

---

### Post by zanglang on 2007-07-24
> **fox1 said:**
> Hi

why I must instal Pidgin this way? Why there is no possibility to instal it through Synaptic or Add remove application? And why the terminal codes from the first post do not work?

Pidgin was released after Feisty/7.04's, so it wouldn't be in the repository, that's why you can't for now.

Are you sure you copied the line properly by the way?

---

### Post by fox1 on 2007-07-24
Oh I see. So it will not be available until** some repository uploads it**?

Yes I copied properly the commands. But I downloaded two deb files and it installed perfectly. 

Maybe I made some mess **uninstalling Gaim**. Couse when I installed the smaller file (of the two deb) it additionally **downloaded two files.** Maybe I deleted something that was important for Pidgin so the commands couldn't work ?! But the deb files fixed everything as I see.

---

### Post by zanglang on 2007-07-24
> **fox1 said:**
> Oh I see. So it will not be available until** some repository uploads it**?
Yeah, in fact you were downloading from the Ubuntu.pl repository. Gutsy also has the packages now, so when 7.10 is released users should be able to just get it off Synaptic and Add/Remove just as easily.

> Yes I copied properly the commands. But I downloaded two deb files and it installed perfectly. 

Maybe I made some mess **uninstalling Gaim**. Couse when I installed the smaller file (of the two deb) it additionally **downloaded two files.** Maybe I deleted something that was important for Pidgin so the commands couldn't work ?! But the deb files fixed everything as I see.
Was it installing something like libavahi-xyz? That might be normal, because the Pidgin package you downloaded just might require extra dependencies than the old Gaim. Otherwise can you post any error messages?

---

### Post by fox1 on 2007-07-24
Sorry I didn't save the message I got ! But as everything is ok now I think that you are right. I think that while I uninstaled Gaim I also uninstaled something that was needed by Pidgin. By starting two deb files the update was done and everything was back to normal.

Btw I couldn't find Pidgin in my Synaptic...

---

### Post by Mornedhel on 2007-07-24
If you installed it via .deb packages, select Status (on the left panel), then look for a category named Local.

---

### Post by kevdog on 2007-07-24
Here is a great sight that is simple and easy to use.  Just cut and paste the commands into a terminal -- and boom -- done!
[http://howto.landure.fr/gnu-linux/ubuntu-feisty-fawn-1/software-for-ubuntu-feisty-fawn/pidgin-previously-gaim-on-ubuntu-feisty-fawn](http://howto.landure.fr/gnu-linux/ubuntu-feisty-fawn-1/software-for-ubuntu-feisty-fawn/pidgin-previously-gaim-on-ubuntu-feisty-fawn)

---

### Post by zanglang on 2007-07-24
> **fox1 said:**
> Btw I couldn't find Pidgin in my Synaptic...

Pidgin has *only* been added to Gutsy 7.10 (which will only be officially released in October); thus if you're using the earlier versions like Dapper or Feisty, since it's not available you won't be able to find it in Synaptic. *Unless* you've installed it from a .deb file, which then it'll show up as a locally installed package, as Mornedhel has pointed out. ;)

---

### Post by fox1 on 2007-07-24
Thanks guys.. yes I have Fiesty... Thanks once again.. I installed it and already added accounts from MSN, IRC and Google talk... it works perfectly and beautifully !!!

---

