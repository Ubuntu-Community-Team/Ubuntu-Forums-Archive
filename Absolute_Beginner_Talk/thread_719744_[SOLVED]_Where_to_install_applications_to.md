---
title: "[SOLVED] Where to install applications to"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by drubin on 2008-03-09
Hi I was wondering where is the "default" place to install applications to. In windows it was c:\program files\

The reason i asked was i just tried to install netbeans6.0.1  and it wanted to install to /home/rubin/netbeans6.0.1 

Should i just accept that? aren't applications suppose to be some where else, NONE of my other applications I installed are there...

Thanks

---

### Post by szymon_g on 2008-03-09
default directories for applications are:

/usr/bin
/usr/local <<--- those one for apps installed from source only, AFAIK
/bin <<--- only systems-application should be here
/opt/ -- used in some distribution for *optional* apps. in theory, all closed-source apps should be installed here

anyway, i suggest to read Linux Filesystem Hierarchy or Linux Standard Base

btw, netbeans is in repo, isn't it :?

---

### Post by dwanders on 2008-03-09
WHen the system is installing the application in your home folder (e.g. /home/rubin) it is installing for your user only. There is nothing wrong with installing like this. It even makes it easier to backup just your stuff. For the other folders, check this out:

[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

It will tell you what all the folders are for and where you can/should install global applications.

---

### Post by aysiu on 2008-03-09
There seem to be a number of Netbeans packages in the repositories:
[http://packages.ubuntu.com/search?keywords=netbeans&searchon=names&suite=gutsy&section=all](http://packages.ubuntu.com/search?keywords=netbeans&searchon=names&suite=gutsy&section=all)

Is it really necessary to know what directories they install to?

---

### Post by drubin on 2008-03-09
Great but what happens when other users need to use the application? 

I would LOVE to be able to back up my settings for netbeans, (hopfuly those will be stored in my  /home folder)

But the application i think i will install to /usr/bin/ 

Any one here used/installed netbeans on Ubuntu before?

---

### Post by drubin on 2008-03-09
> **aysiu said:**
> There seem to be a number of Netbeans packages in the repositories:
[http://packages.ubuntu.com/search?keywords=netbeans&searchon=names&suite=gutsy&section=all](http://packages.ubuntu.com/search?keywords=netbeans&searchon=names&suite=gutsy&section=all)

Is it really necessary to know what directories they install to?

On your first point, I tried but they are only 5.5 and i wanted the latest version that is 6.0.1  :)

Also on the second point, It is part of learning to know where/what things are doing. It is just ignorance/bliss that i was trying to get away from with Windows. 

Linux for me is more about a learning curve and expanding my knowledge base!! then the destination (In this case just having a working version of Netbeans) 

Thanks for your help.

---

### Post by dwanders on 2008-03-09
Definitely - if you are going to have multiple users running on this one computer, I would suggest you install the application to /usr/opt (as indicated earlier) or possibly /usr/local as indicated by the link I posted. 

As for your netbeans config - I am not positive, but I believe you will eventually have a            

/home/rubin/.netbeans (note the dot which indicates a hidden folder) folder that will hold your configuration settings etc...

It really just comes down to personal pref and whether or not your running a multi user server.

---

### Post by drubin on 2008-03-09
Thanks for every ones help, In showing me where files/folders are on the file system.

The main reason it was trying to install netbeans to my home dir, was because I ran the install with OUT sudo permissions. (and  I don't have right access to the /usr/bin dir).

I re ran it as "root"  worked great.

---

### Post by smartboyathome on 2008-03-09
Also, it usually only installs to /home/username when you don't run it as root. Try running it as root and it should install it to the correct system-wide location.

---

### Post by dwanders on 2008-03-09
I have tried playing with NetBeans, and Eclipse both but have truly determined that my low level development skills never go beyond the needs of Jedit running on my external USB drive - I have found the big IDE's add lots of un-needed stuff and overly complicate my little scripts :)

---

### Post by dwanders on 2008-03-09
Brilliant pick up too (smart & ru) sudo install would do just that !

---

### Post by drubin on 2008-03-09
> Re: Where to install applications to
I have tried playing with NetBeans, and Eclipse both but have truly determined that my low level development skills never go beyond the needs of Jedit running on my external USB drive - I have found the big IDE's add lots of un-needed stuff and overly complicate my little scripts 

I develop in java...... I have been using windows for a long time now, So it has been a learning curve to change over to Ubuntu. So the IDE thing is a must. :) 

PS, I lost the link to mark this thread as solved? could some one please point me the right direction.

---

### Post by smartboyathome on 2008-03-09
> **rubinboy said:**
> I develop in java...... I have been using windows for a long time now, So it has been a learning curve to change over to Ubuntu. So the IDE thing is a must. :) 

PS, I lost the link to mark this thread as solved? could some one please point me the right direction.

Thread Tools > Mark Thread as Solved. :)

---

### Post by drubin on 2008-03-09
I feel so stupid, I was watching something and had it set to always ontop. -It was covering that link :)  

I knew it was there, juts a bit of a long day hey. 
Thanks again.

---

