---
title: "Ubuntu and Kubuntu"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by lifemaximum on 2006-09-27
Hello

I just got my kubuntu CD , and i wanted to install it on my system to run along with my ubuntu , why ? cause it looks good...8) 

so how do i do that with losing any info ? and without getting my harddisk formated ??

---

### Post by xpod on 2006-09-27
Would`nt you be just as well installing the kde desktop if it`s just one pc?
I got 2 on separate pc`s and "yes" it is good but on just one pc you`d probably be just as well with the extra desktop environment??

Stll is`nt a problem doing it though i dont think

EDITBackup back up:D

---

### Post by lifemaximum on 2006-09-27
alright ...thanks for the advice ;)

---

### Post by bigken on 2006-09-27
just do a sudo aptitude install kubuntu-desktop then log out and select kde from session menu

---

### Post by xpod on 2006-09-27
```
sudo aptitude update 
```

First...;)

---

### Post by ajgreeny on 2006-09-27
Always use aptitude for a meta-package like kubuntu-desktop, as it remembers all the packages installed and makes it so much easier to remove it all if ever you want to.  If you use apt-get or synaptic and try to remove kubuntu-desktop, it will only remove the small meta-package, not all the actual program packages as well.

Worth doing the kubuntu-desktop install, incidentally;  that's exactly what I have done since hoary hedgehog, and have not had any problems with it at all.

---

### Post by lifemaximum on 2006-09-27
hahah yea i could have done that... not install the whole os haha...thanks guys...:shock:

---

### Post by lifemaximum on 2006-09-27
]
Err [http://kubuntu.org](http://kubuntu.org) dapper/main konqueror 4:3.5.4-0ubuntu1~dapper2
  Connection timed out
Get:22 [http://kubuntu.org](http://kubuntu.org) dapper/main kwin 4:3.5.4-0ubuntu1~dapper2 [1007kB]
Err [http://kubuntu.org](http://kubuntu.org) dapper/main kwin 4:3.5.4-0ubuntu1~dapper2
  Connection timed out
Get:23 [http://kubuntu.org](http://kubuntu.org) dapper/main libarts1-akode 4:3.5.4-0ubuntu2~dapper1 [163kB]
Err [http://kubuntu.org](http://kubuntu.org) dapper/main libarts1-akode 4:3.5.4-0ubuntu2~dapper1
  Error reading from server - read (104 Connection reset by peer)
Get:24 [http://kubuntu.org](http://kubuntu.org) dapper/main kdelibs4c2a 4:3.5.4-0ubuntu2~dapper1 [9705kB]
Err [http://kubuntu.org](http://kubuntu.org) dapper/main kdelibs4c2a 4:3.5.4-0ubuntu2~dapper1
  Connection timed out
Fetched 20.4kB in 11m46s (29B/s)
E: Unable to correct for unavailable packages



that is the error i got ? what should i do now?:rolleyes:

---

### Post by deadgobby on 2006-09-27
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)
 See if these instructions can help. It all so can be the server is down too. But at last, try the above link and see if it drives.
Gobby

---

### Post by lifemaximum on 2006-09-28
thanks everyone got it working...looks prety nice...abit different from ubuntu though...got to figure out where the menus and stuff are though...but it is great.

---

### Post by hyper_ch on 2006-09-28
Don't you wanna add Xcfe also? So you have K/X/U/buntu?

^^

---

### Post by bigken on 2006-09-28
> **sjau said:**
> Don't you wanna add Xcfe also? So you have K/X/U/buntu?

^^
 you forgot about edubuntu 8)

---

### Post by lifemaximum on 2006-09-28
hey... i added Kubuntu it works fine and all but my multimedia keys in my laptop are not working? you know like the volume controller and stuff like that what should i do ?/

---

### Post by pay on 2006-09-29
Gnome and KDE use different volume controls and stuff so you'll have to bind your keys again. I don't use KDE so I can't help you here.

---

