---
title: "Avast vs ClamAV"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by tech9 on 2007-09-06
Could I get someone elses opinion on Avast Anti-Virus...
I used Avast, but when running a thorough scan on the entire system as root, the program freezes the whole ubuntu OS.

I tried ClamAV as well, but when running the commands, clamscan -r --bell / , the program shows that it's own files as (getfiles) contains viruses

Any other good AV programs out there?

---

### Post by Steve1961 on 2007-09-06
i use Avast which seems to do a reasonable job.  As I share files with windows I use it to make sure files are clean before I drop them into a fat32 data partition.  I believe AVG also do a linux version, but haven't used it.

---

### Post by str8line on 2007-09-06
Like the Mac, Ubuntu is not as prone to viruses.  Without Internet Explorer you are not open to ActiveX controls and spyware the same way you were with M$ Windows.  I have used both programs to test on multiple machines and the system resources used does not balance to the threat that exists for an Ubuntu machine.

If you are dual booting then definitely go for antivirus but if not utilizing a good firewall is vastly superior to running antivirus software at this point.

---

### Post by asmoore82 on 2007-09-06
> **tech9 said:**
> Could I get someone elses opinion on Avast Anti-Virus...
I used Avast, but when running a thorough scan on the entire system as root, the program freezes the whole ubuntu OS.

I tried ClamAV as well, but when running the commands, clamscan -r --bell / , the program shows that it's own files as (getfiles) contains viruses

Any other good AV programs out there?

[https://wiki.ubuntu.com/CriticismFAQ#head-1663544b421081799ed551bdfa891411191121f2](https://wiki.ubuntu.com/CriticismFAQ#head-1663544b421081799ed551bdfa891411191121f2)

---

### Post by por100pre1 on 2007-09-06
You can use F-Prot with XFPROT, check this [how-to]("http://ubuntuforums.org/showthread.php?t=88357"). Use the XFPROT .deb file for an easier install.

But instead of that you can check for rootkits with chkrootkit and rkhunter.

In terminal:

```
sudo aptitude install chkrootkit rkhunter
```

to use them:

```
sudo chkrootkit
```

```
sudo rkhunter --update && sudo rkhunter -c -sk
```

Hope this helps. :)

---

### Post by n3tfury on 2007-09-06
> **str8line said:**
> Like the Mac, Ubuntu is not as prone to viruses.  Without Internet Explorer you are not open to ActiveX controls and spyware the same way you were with M$ Windows.  I have used both programs to test on multiple machines and the system resources used does not balance to the threat that exists for an Ubuntu machine.

If you are dual booting then definitely go for antivirus but if not utilizing a good firewall is vastly superior to running antivirus software at this point.

forgive me, but that's not very good advice.  IE may have something to do with spyware and malware infections, but you can get the same through FF as well with malicious scripts from websites.  unless you really know what you're doing and you don't do p2p or use an email client, then you could probably get away with not using an antivirus.

---

### Post by tech9 on 2007-09-06
> **asmoore82 said:**
> [https://wiki.ubuntu.com/CriticismFAQ#head-1663544b421081799ed551bdfa891411191121f2](https://wiki.ubuntu.com/CriticismFAQ#head-1663544b421081799ed551bdfa891411191121f2)


I realize that Linux is way less prone to viruses than ms windows, but that doesn't mean that people won't start writing viruses for popular OS such as ubuntu...

I would rather be safe than sorry...

I found the following post in the forum and agree with Suntin...

______________________________________________________

suntinMarch 15th, 2007, 02:07 AM
[http://linuxmafia.com/~rick/faq/index.php?page=vir](http://linuxmafia.com/~rick/faq/index.php?page=vir) us

You don't need a virusscanner unless you want to protect windowsmachines in your network.


You said "Linux doesn't need anti virus" our survey says "uh uh"

While there aren't many viruses for Linux right now and while Linux inherently makes virus writing harder they do happen, they will grow in number as the Linux user base grows, (sadly) particularly on Ubuntu which is rapidly growing in popularity. 

...And statments like "linux is cool, you'll never see a virus again" will eventually make you look stoopid and will make people question the value of a great OS simply because they didn't prepare.

it would be like saying I don't know anyone that's been hit by a car so I don't need to look.

______________________________________________________________________

Exactly!

---

### Post by tech9 on 2007-09-06
> **n3tfury said:**
> forgive me, but that's not very good advice.  IE may have something to do with spyware and malware infections, but you can get the same through FF as well with malicious scripts from websites.  unless you really know what you're doing and you don't do p2p or use an email client, then you could probably get away with not using an antivirus.

I agree n3tfury

---

### Post by n3tfury on 2007-09-06
thanks :)  alot of people, especially in this particular forum, are not tech savvy, so to say "you won't need it because you're now using <insert unix based OS here>" is just not good advice.

---

### Post by str8line on 2007-09-06
My apologies for my last post, but the resources used by an antivirus program in Ubuntu do not balance with the threat currently posed by viruses on the net.  On 4 machines I run no antivirus software and have never (knock on wood) had an issue with infection (I do a monthly check using ClamAV then uninstall).  The one windows machine that I have (used for media center only) does have AVG installed and is constantly finding malware of all types.

A good hardware or software firewall and keeping your distro up to date is much more effective in protecting your computer than running a dedicated AV program at this time.

As for not being tech saavy, too each his own but passing judgement is not what the forums are meant for.  When and if the day comes that Linux viruses are common place then I will consider increasing the level of protection for my Ubuntu machines but as has been said many times across the forums....Ubuntu is not Windows and heaven help us if it ever goes that route.

Open Source software by its nature is more secure because of the volume of different eyes looking at the code and improving it all the time.  Keeping your Ubuntu up to date will close the holes and keep you safer than a 3 hour virus scan ever could.

---

### Post by n3tfury on 2007-09-06
> **str8line said:**
> The one windows machine that I have (used for media center only) does have AVG installed and is constantly finding malware of all types.



um, unless you surf malicious sites daily, that's b.s.  i dual boot XP and have a dedicated media center PC and don't even REMEMBER the last time i had any sort of virus infection *edit* i just checked the AVG history and on 1/17/07 it "found" one, but it was a false positive (all seeing eye.exe)

no need to exaggerate things.

also, i wasn't saying YOU weren't tech savvy, but it's apparent most users that post questions are not.

---

### Post by str8line on 2007-09-06
n3tfury,

I would agree that unless you surf to "unsavory" sites on a regular basis then the most a common user would encounter is "tracking cookies" but from experience with Windows even one infection regardless of where the infection came from can be painful.  One compared to none is a substantial increase but from dealing with the common computer user every day.....it is never just one.  

Experience has shown me that  most Windows users would not have been infected had they just updated the Windows program itself (think back to the Sasser Worm...I had one of the original Beta Tester versions of XP that I used for years and would be infected by the Sasser every install if I didn't have a copy of SP1 and SP2 installed before I connected to the internet).

---

### Post by oilchangeguy on 2007-09-06
> **n3tfury said:**
> thanks :)  alot of people, especially in this particular forum, are not tech savvy, so to say "you won't need it because you're now using <insert unix based OS here>" is just not good advice.

read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
and this:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)


i've got two computers running ubuntu 6.06lts. neither has any type of a/v or anti-spyware software installed. both computers have been like this for almost a year, and no problems. i don't share files with a windows machine. this may be the only exception where something is needed. i suggest reading the links i've provided. so you'll be a more informed ubuntu user, and not one spreading incorrect facts.

---

### Post by n3tfury on 2007-09-06
> **oilchangeguy said:**
> read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
and this:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)


i've got two computers running ubuntu 6.06lts. neither has any type of a/v or anti-spyware software installed. both computers have been like this for almost a year, and no problems. i don't share files with a windows machine. this may be the only exception where something is needed. i suggest reading the links i've provided. so you'll be a more informed ubuntu user, and not one spreading incorrect facts.

from the first link (which i've read alot of his articles, btw)

> Disclaimer
I am not a security expert at all

that's enough for me.

the second one i read back in August.  what's your point?  there's STILL a chance when you're talking about non-savvy users.  the linux base is rapidly growing - wait for it.  also, i never said my *opinion* was fact.  talk about spreading incorrect information...

---

### Post by oilchangeguy on 2007-09-06
> **n3tfury said:**
> from the first link (which i've read alot of his articles, btw)



that's enough for me.

the second one i read back in August.  what's your point?  there's STILL a chance when you're talking about non-savvy users.  the linux base is rapidly growing - wait for it.  also, i never said my *opinion* was fact.  talk about spreading incorrect information...

ok, here's a thought, search the forum, google, whatever. and see what you can find on the probability of a virus written just for ubuntu. i've not used vista, but as for xp, be it home, pro, or media center. it's still xp under the skin. and due to it's large installed base, 90+ percent of the world's computers run a microsoft operating system. i'd say that's a pretty large target. so that leaves less than 10 percent of the worlds computers running linux, mac, etc. and each distro of linux is slightly different. someone would have to be very bored to take the time to write a virus just for a certain distro. and even then it would need to be root to run. so you and all of the other scared people can continue to use system resourses to run your anti-virus programs, those of us in the know, will not. also keep in mind, your a/v software is probably looking for windows based viruses. theres just simply not much else for it to watch for.

---

### Post by syms on 2007-09-06
u really dont need an antivirus in linux

---

### Post by asmoore82 on 2007-09-06
> **tech9 said:**
> I realize that Linux is way less prone to viruses than ms windows, but that doesn't mean that people won't start writing viruses for popular OS such as ubuntu...

I would rather be safe than sorry...

Viruses are **NOT a popularity contest.** Even if they were, the most valuable targets
would be UNIX/Linux based servers. Linux has been **calling out** viruses since birth
and guess what? Nothing.
People can write Viruses until their keyboards fall off and **It will not matter**.

Up to date GNU/Linux systems **such as Ubuntu** are secure and will not allow a virus to propagate.
The only way your system could be infected is if **you** run the baddie with root priviledge.
And If you are the type person who is going to do such a thing, the damage will be
done long before any antivirus can stop it.

---

### Post by tech9 on 2007-09-13
> **str8line said:**
> My apologies for my last post, but the resources used by an antivirus program in Ubuntu do not balance with the threat currently posed by viruses on the net.  On 4 machines I run no antivirus software and have never (knock on wood) had an issue with infection (I do a monthly check using ClamAV then uninstall).  The one windows machine that I have (used for media center only) does have AVG installed and is constantly finding malware of all types.

A good hardware or software firewall and keeping your distro up to date is much more effective in protecting your computer than running a dedicated AV program at this time.

As for not being tech saavy, too each his own but passing judgement is not what the forums are meant for.  When and if the day comes that Linux viruses are common place then I will consider increasing the level of protection for my Ubuntu machines but as has been said many times across the forums....Ubuntu is not Windows and heaven help us if it ever goes that route.

Open Source software by its nature is more secure because of the volume of different eyes looking at the code and improving it all the time.  Keeping your Ubuntu up to date will close the holes and keep you safer than a 3 hour virus scan ever could.


I didn't mean to offend or pass judgement... just merely stating my opinion

---

### Post by tech9 on 2007-09-14
> **por100pre1 said:**
> You can use F-Prot with XFPROT, check this [how-to]("http://ubuntuforums.org/showthread.php?t=88357"). Use the XFPROT .deb file for an easier install.

But instead of that you can check for rootkits with chkrootkit and rkhunter.

In terminal:

```
sudo aptitude install chkrootkit rkhunter
```

to use them:

```
sudo chkrootkit
```

```
sudo rkhunter --update && sudo rkhunter -c -sk
```

Hope this helps. :)

Couldn't get this to work... also clamav said that there are virus signatures in test.f-prot

---

### Post by bodhi.zazen on 2007-09-14
> **asmoore82 said:**
> [https://wiki.ubuntu.com/CriticismFAQ#head-1663544b421081799ed551bdfa891411191121f2](https://wiki.ubuntu.com/CriticismFAQ#head-1663544b421081799ed551bdfa891411191121f2)

+1

No, no ,  +10 \0/

As a new user migrating from a new OS you need to change your mindset. 

1. Keep your system up to date, including security updates.

2. Do not install packages (software) from untrusted sources.

See this link : [[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by por100pre1 on 2007-09-14
> **tech9 said:**
> Couldn't get this to work... also clamav said that there are virus signatures in test.f-prot

What exactly doesn't work? Let me know. :-k

---

### Post by Shaythong on 2008-07-10
I haven't really tried ClamAV yet but Avast has been pretty good. 8-)

---

### Post by tech9 on 2008-07-11
I kind of left this all by the waste side. Until I see actual signs of virus activity... I am not worried about it

---

### Post by benny bronx on 2008-07-11
I agree that an antivirus is not necessary with Ubuntu at the moment.  I have avast because I occasionally receive and forward files from windows users for my work, but I rarely ever use the av.  But what system resources does avast use?  Besides disk space, which is not a problem for most computers nowadays, it does not run any processes or services when not scanning or updating.

---

