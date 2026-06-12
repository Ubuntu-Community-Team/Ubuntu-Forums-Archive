---
title: "Internet Connection Problems"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by Stuart_Young on 2006-04-26
Hi, as a completely new user to Linux and Ubuntu, I am having slight problems connecting to the Internet at my workplace.

I am able to connect at home usidng Firefox (the one that came with Ubuntu), but I have yet to connect using Firefox or Konquerer.  The main difference is that the school I work for has a proxy server.  I have inputted the relevent settings into Firefox/Konquerer/System -> Preferences -> Proxy thing. and all are set to the same 10.131.108.61. I have also disbaled ipv6 but this had no effect.

I know it will work, as it works with FF in Win XP! So it must be something I have/haven't done.

Any advice would be more than welcome, this problem is driving me crazy ](*,)  and as soon as i fix it I can delete windows for good!

Thanks in advance and sorry if there is a post about this already, but I have been searching for around 30mins and couldn't find a solution.

---

### Post by ntsb on 2006-04-26
I think you should try like this:

System>Administration>Networking settings

---

### Post by Sef on 2006-04-26
From Worty:  Here's another thing to try to set up your connection, if you have DSL.

> 
Quote:
Originally Posted by Mr Aragorn
I turn it on, but I dont know were to put mi login and password to make the connection.

Hi Mr Aragorn, assuming your network card is detected and everything works, go to the console and type:

Quote:
sudo pppoeconf

after you go through the setup, type

Quote:
pon dsl-provider
to turn it on

and

Quote:
poff

to turn it off.

Go here for some other options and help.
[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

[http://www.ubuntuforums.org/showthread.php?p=951507#post951507]("http://www.ubuntuforums.org/showthread.php?p=951507#post951507")

---

### Post by Stuart_Young on 2006-04-27
Thank you both for the advice, but I found out that the problem wasn't with Ubuntu but with the access point that I was using, thankfully there are a number of them around the building so I can just use another.

Thanks again

---

