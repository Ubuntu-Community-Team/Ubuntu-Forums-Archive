---
title: "gnucash-2.0.2.tar.bz2"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by captgadget on 2006-11-10
Now, that I have this downloaded as a new Linux user what are the steps I need to follow to get this program installed and running? Since I don't understand all the codes used but am trying to learn please tell me as clearly as possible. After using Windows for 12 years there is somewhat of a learning curve so appreciate everyone's help in the forums. Using Ubuntu 6.1

Thank you

---

### Post by bluefrog on 2006-11-10
will be simpler if you use synaptic programm manger to begin with.

open synaptic, then find in the upper menu its preferences and enable (check) universe and multiverse. close preferences, click on the reload button (you need internet connection to be enabled before that)

then search for gnu cash in the list and install from there.

James

---

### Post by captgadget on 2006-11-10
And it would be nice if they had the newest version.

---

### Post by Oki on 2006-11-10
My version of Gnucash is 1.8.12(from Synaptic). From Gnucash homepage I can se there as been a lot of changes [http://www.gnucash.org/](http://www.gnucash.org/) Like on line banking! So I understand your need for the latest version of it. 

I agree, sometimes the latest is a must, other times not. I have no need for FireFox2.0, since 1.5 is good enough for me, and it is stabel. And sometimes the program are not at all in synaptic.

As I understand it, the Ubuntu team dos not just add a program to the synaptic package register. Ubunut(D D) has the goal to be stabel, so they must test it, make changes and so on for it to "fit" Ubunut. In other words; Firefox from Synaptic isn't "Firefox", but Firefox for Ubuntu since they have changed things. Therefore it takes some time to get newer version to synaptic. I think the keyword is "dependencies". And my further "noob" understanding is that a program that not "fit" Ubunut correctly can damage the entire OS(read more here; [http://www.newsforge.com/article.pl?sid=04/12/02/1710208](http://www.newsforge.com/article.pl?sid=04/12/02/1710208))

Coming form Windows this part of Linux world is som hard to understand I think(for me at last), and also hard to settle with - cus in Windows I have always used the latest versions and never had any trouble. And if any, then it only affected the program itself and not the OS. 

Perhaps this can help you with the latest version: [http://ubuntuforums.org/showthread.php?t=213130&page=2](http://ubuntuforums.org/showthread.php?t=213130&page=2)

And Linux-fanboys; just to let you know - I am rely enjoying Ubuntu and do my best to get out of the "Windows grip"... It is not easy!

---

### Post by Oki on 2006-11-10
You could also look at Grisbi or KmyMoney, the latest version is in Synaptic:-) Never tried it myself!

And sorry for my poor English..

---

### Post by Bachstelze on 2006-11-10
There's a README and an INSTALL file, have you read them ?

---

### Post by captgadget on 2006-11-10
And you know I maybe jumping the gun here. I did use Synaptic to download the 1.8 and when I imported my files from Microsoft money it was pretty messed up. So I thought if I maybe had the new vesion it would do a better job of importing. I do appreciate all the honest answers. I will try to find the read me file.

Thanks again and don't give up on me!!!

---

### Post by Bachstelze on 2006-11-10
They're just in the dir you extracted, like in 99.999 % of the apps you'll download as source. Just *cd* to the dir and do

```
gedit INSTALL &
```

which will open the file with installation instructions in gedit. Don't forget the & at the end if you don't want to open another terminal window ;)

---

### Post by Holzster on 2006-11-10
> **bluefrog said:**
> will be simpler if you use synaptic programm manger to begin with.

open synaptic, then find in the upper menu its preferences and enable (check) universe and multiverse. close preferences, click on the reload button (you need internet connection to be enabled before that)

then search for gnu cash in the list and install from there.

James

Remeber the synaptic version does NOT have online banking support because the piece that GNUCash uses for that is free but not open source.  So if you need online banking support you have to install from source.

sorry for that news

---

