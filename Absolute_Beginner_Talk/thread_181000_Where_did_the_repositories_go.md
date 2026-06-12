---
title: "Where did the repositories go?"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by Belathor on 2006-05-23
I loaded synaptic today and find that most of my repositories were "moved permanently". I upgraded the kernel to K7, could that be causing it?

Thanks!

```
http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz: 301 Moved Permanently
http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz: 301 Moved Permanently
http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz: 301 Moved Permanently
http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz: 301 Moved Permanently
http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz: 301 Moved Permanently
http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz: 301 Moved Permanently
http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz: 301 Moved Permanently
http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz: 301 Moved Permanently
http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz: 301 Moved Permanently
http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz: 301 Moved Permanently
```

---

### Post by learning on 2006-05-23
I though it was just me!  Glad you posted this.  Figured I had messed something up again! :o

---

### Post by Deus42 on 2006-05-23
I have the same problem on my computer.

---

### Post by nalmeth on 2006-05-23
THat would make sense, all those packages coming up are for i386. With k7 you should be on some grade of i686 or something.

---

### Post by tlogank on 2006-05-23
Yes, I am getting the exact same message!  I want to update my stuff because I haven't in forever on my laptop.  Any fix for this?  or perhaps any ETA?

---

### Post by Belathor on 2006-05-23
Where can I find the K7 repos then?

EDIT: It seem a lot of people are having this problem. Perhaps the servers are down for a bit.

---

### Post by SubWolf on 2006-05-23
Getting the same thing this morning, plus warnings about unverified packages - makes one tempted to not install!

---

### Post by togume on 2006-05-23
I got a similar error on my sudo apt-get update, echo below:
> togume@togubuntu:~$ sudo apt-get update
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
  301 Moved Permanently
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
  301 Moved Permanently
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
  301 Moved Permanently
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
  301 Moved Permanently
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
  301 Moved Permanently
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
  301 Moved Permanently
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
  301 Moved Permanently
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Sources
  301 Moved Permanently
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
  301 Moved Permanently
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
  301 Moved Permanently
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
  301 Moved Permanently
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
  301 Moved Permanently
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
  301 Moved Permanently
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:2 [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release.gpg [191B]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
  301 Moved Permanently
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
  301 Moved Permanently
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
  301 Moved Permanently
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
  301 Moved Permanently
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
  301 Moved Permanently
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
  301 Moved Permanently
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
  301 Moved Permanently
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/aiglx Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper/aiglx Packages
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
Fetched 2B in 1s (1B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  301 Moved Permanently
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  301 Moved Permanently
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  301 Moved Permanently
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  301 Moved Permanently
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz)  301 Moved Permanently
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz)  301 Moved Permanently
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz)  301 Moved Permanently
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz)  301 Moved Permanently
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  301 Moved Permanently
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  301 Moved Permanently
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  301 Moved Permanently
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  301 Moved Permanently
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz)  301 Moved Permanently
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz)  301 Moved Permanently
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz)  301 Moved Permanently
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz)  301 Moved Permanently
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz)  301 Moved Permanently
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz)  301 Moved Permanently
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz)  301 Moved Permanently
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz)  301 Moved Permanently
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


Wonder what happened...

---

### Post by SubWolf on 2006-05-23
Interestingly enough, my friend in the UK noticed that his update went just fine. I switched my sources.list to the gb host instead of us, and everything is going smoothly.

Quite glad about that, at one point a few packages were showing broken.

US mirror fubar'd?

---

### Post by Soilman on 2006-05-23
Yikes!
I'll go have a cup of coffee and maybe it will be better when I return.
DiG

---

### Post by lolke on 2006-05-23
There are no i686 or K7 repositories. i386 is the name of the architecture and it applies to the whole 32 bit Intel/AMD family.

Anyway I cut and paste the  [http://us.archive.ubuntu.com/ubuntu/dists](http://us.archive.ubuntu.com/ubuntu/dists) link in a browser and I get [http://mirrors.tds.net/bandwidth_exceeded.html](http://mirrors.tds.net/bandwidth_exceeded.html)  back. So it looks like the bandwith for this server was exceeded. 

Who is the ftp-master for the Ubuntu repositories? They should have a look at it.

Lolke

---

### Post by Prefader on 2006-05-23
This may have appeared elsewhere on the boards, but you can resolve this by editing your sources.list.  Change your repositories from
```
http://us.archive.ubuntu.com
```
to 
```
http://archive.ubuntu.com
```

---

### Post by arkepp on 2006-05-23
Paste the URL of the repository into a regular webbrowser and you'll see:

Not Found
The requested URL /bandwidth_exceeded.html was not found on this server.

So it looks like at least tds.net can't keep up. I've also noticed their Gentoo server has become annoyingly slow lately.

Free bandwidth -> can't complain :)

---

### Post by tlogank on 2006-05-23
[QUOTE=SubWolf]Interestingly enough, my friend in the UK noticed that his update went just fine. I switched my sources.list to the gb host instead of us, and everything is going smoothly.

Quite glad about that, at one point a few packages were showing broken.

US mirror fubar'd?[/QUOTE]
And how do I do such a switch?

---

### Post by hanexar on 2006-05-23
I'm having the same error here.  The update was going fine and then stop.  It seems like a problem on the server side.  I hope it will be fixed soon.

---

### Post by tlogank on 2006-05-23
[QUOTE=Prefader]This may have appeared elsewhere on the boards, but you can resolve this by editing your sources.list.  Change your repositories from
```
http://us.archive.ubuntu.com
```
to 
```
http://archive.ubuntu.com
```[/QUOTE]
Sorry, but I am a total n00b...can you tell me exactly how you do that?

---

### Post by erikdhansen on 2006-05-23
[QUOTE=tlogank]Sorry, but I am a total n00b...can you tell me exactly how you do that?[/QUOTE]

[QUOTE=SubWolf]Interestingly enough, my friend in the UK noticed that his update went just fine. I switched my sources.list to the gb host instead of us, and everything is going smoothly.

Quite glad about that, at one point a few packages were showing broken.

US mirror fubar'd?[/QUOTE]

Edit /etc/apt/sources.list and do a search replace on the URL that is currently pointing to the us archives.  I switched 'us' to 'uk' and my update completed.  I'll switch it back later when things appear to have stabilized.

---

### Post by evilgold on 2006-05-23
Okay first off, there are no K7 repos... there are only types of archs supported by ubuntu, PowerPC, i386, and AMD64. The K7 kernel is in the i386 repo, that is the only k7 optimized package you will find, with a few excetions. if you want full k7 optimiztions you have to recompile.  So this is not due to your recent change in kerenel...or anything you did for that matter.

Second... when going to us.archive.ubuntu.com... you will see this message:
Not Found

The requested URL /bandwidth_exceeded.html was not found on this server.
Apache/2.2.0 Server at mirrors.tds.net Port 80


Which means that the US repos have been getting hit up hard....  

Quick fix till they are back up... remove us from your source urls...
make them all point to [http://archive.ubuntu.com](http://archive.ubuntu.com) instead of us.archive.ubuntu.com

Edit: you guys beat me too it :(

---

### Post by Belathor on 2006-05-23
> sudo gedit /etc/apt/sources.list and then find where it says what Prefader wrote and change it to what he said to change it to.

---

### Post by hanexar on 2006-05-23
[QUOTE=Prefader]This may have appeared elsewhere on the boards, but you can resolve this by editing your sources.list.  Change your repositories from
```
http://us.archive.ubuntu.com
```
to 
```
http://archive.ubuntu.com
```[/QUOTE]

It worked that way.  thanx

---

### Post by the gnome on 2006-05-23
Wow I'm relieved and disenheartened all at the same time lol.

I thought I had installed gcc correctly because I need to compile some new tools for mySQL but then I noticed the error when trying to get some library dependencies.  Well time for a cuppa, and cross my fingers that this gets fixed soon! :-D

---

### Post by hanexar on 2006-05-23
[QUOTE=tlogank]Sorry, but I am a total n00b...can you tell me exactly how you do that?[/QUOTE]

Make a backup of your old sources.list
```
 sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup 
```

Edit your sources list

```
 sugo gedit /etc/apt/sources.list 
```

change every ```
 us.achive.ubuntu.com 
``` by ```
 archive.ubuntu.com 
```

EDIT: Don't forget to ```
 sudo apt-get update 
```.  You should be able to upgrade now

---

### Post by Prefader on 2006-05-23
<snip!>

Too slow!  :)

---

### Post by the gnome on 2006-05-23
Do you need to reboot after changing the source list?  I ran another apt-get after making the change and it was still going after the us.achives....

---

### Post by lolke on 2006-05-23
[QUOTE=the gnome]Do you need to reboot after changing the source list?  I ran another apt-get after making the change and it was still going after the us.achives....[/QUOTE]
No reboot but you need to run "apt-get update" before you can run the upgrade again.

---

### Post by Prefader on 2006-05-23
```
sudo apt-get update
```
should take care of that.

---

### Post by tlogank on 2006-05-23
See...that is what I love about this community, the response time is incredible when asking for help!  THanks again!

---

