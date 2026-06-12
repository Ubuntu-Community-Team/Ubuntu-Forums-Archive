---
title: "Best way to run Ubuntu and OS X?"
date: 2010-11-23
forum: Apple Hardware Users
---

### Post by aaronklemm on 2010-11-23
Hello,

I am a long-time Ubuntu user, but have been using a MacBook Pro and OS X for the last 3 months. I want to run Ubuntu on this hardware as my primary environment, but preserve the OS X install I've been using.

Dual-booting would be o.k., but not ideal as I would like to use OS X daily (iPhone/iTunes stuff, Google Sketchup, Xcode, and a few other things).

What solution will give me: 
1) native performance from Ubuntu 
2) access to all (or most) hardware features of the laptop 
3) upgrade safe for both Ubuntu and OS X

Will bootcamp do this? If not, then Parallels?

Thanks in advance for your advice. Let me know what else I may need to consider, as I'm new to Ubuntu on Mac.

ak

---

### Post by MisterGaribaldi on 2010-11-23
VMware should run Ubuntu quite handily, from what I've heard. Parallels may likely do just as good a job.

---

### Post by gamebusterzade on 2010-11-24
> **MisterGaribaldi said:**
> VMware should run Ubuntu quite handily, from what I've heard. Parallels may likely do just as good a job.

virtualbox is free and will do just as good as far as performances of visualization goes but u will not reach full potential of the computer (have tried this in the past)

duel-booting you will reach full potential but you need to restart the computer and other steps you will need to follow i found that this sight [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) should get you going for this(this is what i am doing now)

fyi i have a macbook the steps are the almost the same

---

### Post by smoors on 2010-11-24
Hey ho!

I'm in the same situation, a  linux user for a long time with apple hardware :) I can't recommend virtualization for this sort of users. It has some nice points (no hassle with your hardware...) and it is very fast(esp. with Parallels) but it's not the real deal. I'm using ubuntu 10.10 on macbook pro 5.5 and it's a dream. Better then OS X when it comes to responsiveness and everything is working, no more hardware issues (sigh, at the moment). For me, dualbooting was the only real solution for daily linux work. Virtual Machines aren't bad, but more a temporary solution. Hint: You can install Mac OS X in virtualbox under ubuntu :) Perfect solution for me ;-)

---

### Post by aaronklemm on 2010-11-24
Thanks for the advice, everyone! Sounds like dual-booting and then virtualizing OS X with VirtualBox in Ubuntu is the best route. I'll give that a shot.

Any gotchas about upgrading OS X once I've started dual-booting?

Regards,

ak

---

### Post by gamebusterzade on 2010-11-24
just make sure that u have rEFIt installed before you start

other than that you should be good

---

### Post by untmdsprt on 2010-11-26
> **smoors said:**
> Hey ho!

I'm in the same situation, a  linux user for a long time with apple hardware :) I can't recommend virtualization for this sort of users. It has some nice points (no hassle with your hardware...) and it is very fast(esp. with Parallels) but it's not the real deal. I'm using ubuntu 10.10 on macbook pro 5.5 and it's a dream. Better then OS X when it comes to responsiveness and everything is working, no more hardware issues (sigh, at the moment). For me, dualbooting was the only real solution for daily linux work. Virtual Machines aren't bad, but more a temporary solution. Hint: You can install Mac OS X in virtualbox under ubuntu :) Perfect solution for me ;-)

How did you get OS X to run in virtualbox? From my understanding on the virtualbox website is I need the server version of OS X to get this to work. Personally I don't see why I need a server version vs a reg retail version because I'll be using my Macbook.

I'd love to go this route myself as I practically use about 3 native Mac apps while the rest could be done under Linux.

---

### Post by Spyderkid on 2010-11-27
Well a cool way would be to combine MAC OSX    AND!!  Ubuntu in the same OS

If you want to do this it's quite simple....
Install Ubuntu

then run these very simple commands in Terminal under Accesories

```

wget https://downloads.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz -O /tmp/Macbuntu-10.10.tar.gz

tar xzvf /tmp/Macbuntu-10.10.tar.gz -C /tmp

cd /tmp/Macbuntu-10.10/

./install.sh

```

Then just watch the code rattle by in Terminal and just press Y[Yes] or N[No] for certain options which there are 4. It would be a good idea to choose yes for all of them.

---

### Post by gamebusterzade on 2010-11-27
@[Spyderkid]("http://ubuntuforums.org/member.php?u=1191200") 

check your code it didn't work for me i got errors

yes it is in virtualbox 

[IMG]file:///Users/zac/Library/Caches/TemporaryItems/moz-screenshot.png[/IMG][IMG]file:///Users/zac/Library/Caches/TemporaryItems/moz-screenshot-1.png[/IMG]

---

### Post by gamebusterzade on 2010-11-27
> **untmdsprt said:**
> How did you get OS X to run in virtualbox? From my understanding on the virtualbox website is I need the server version of OS X to get this to work. Personally I don't see why I need a server version vs a reg retail version because I'll be using my Macbook.

I'd love to go this route myself as I practically use about 3 native Mac apps while the rest could be done under Linux.


it is hard to do and takes some research but it is possible to visualize the none server one

---

### Post by nataraj88 on 2010-11-27
> **smoors said:**
> Hey ho!

I'm in the same situation, a  linux user for a long time with apple hardware :) I can't recommend virtualization for this sort of users. It has some nice points (no hassle with your hardware...) and it is very fast(esp. with Parallels) but it's not the real deal. I'm using ubuntu 10.10 on macbook pro 5.5 and it's a dream. Better then OS X when it comes to responsiveness and everything is working, no more hardware issues (sigh, at the moment). For me, dualbooting was the only real solution for daily linux work. Virtual Machines aren't bad, but more a temporary solution. Hint: You can install Mac OS X in virtualbox under ubuntu :) Perfect solution for me ;-)

About a year ago, I was able to setup fedora on local disk partitions and then create a virtual machine under vmware fusion so that the same fedora install could be dual booted directly as well as under vmware fusion. It did take a bit of hackery with vmware to get them both to boot. You must be extremely careful not to suspend or hibernate the linux install under one boot method and then reboot under the other, as this can trash the filesystem.

I don't know if it would be possible to get the same MacOS install to boot under vmware as well as directly.


Nataraj

---

### Post by untmdsprt on 2010-11-28
> **gamebusterzade said:**
> it is hard to do and takes some research but it is possible to visualize the none server one

Not a clue of what you're getting at. Possibly a trollish answer, possibly a typo, or whatever. Why don't you clarify?


I HAVE the retail version, Virtualbox's website states it needs the OSX server version. I HAVE tried installing the retail version under virtualbox on my Macbook and it didn't work.

---

### Post by gamebusterzade on 2010-11-29
> **untmdsprt said:**
> Not a clue of what you're getting at. Possibly a trollish answer, possibly a typo, or whatever. Why don't you clarify?


now if you think about my answer you would under stand that yes it is possible to VM the regular OS X but i don't have the answer on how

---

### Post by smoors on 2010-11-29
> **untmdsprt said:**
> Not a clue of what you're getting at. Possibly a trollish answer, possibly a typo, or whatever. Why don't you clarify?


I HAVE the retail version, Virtualbox's website states it needs the OSX server version. I HAVE tried installing the retail version under virtualbox on my Macbook and it didn't work.

Hey!!

Are you sure that you're using the latest version of virtualbox? I tried it with ubuntu 10.04 and my retail SL retail dvd. Worked nicely,  the installation is some month old. But i'm using it not a lot.. 
 As i understood it, the reason why virtualbox says that you have to use Snow Leopard Server is that the EULA of the "normal" SL forbids the virtualisation.

---

### Post by ubaddn on 2010-12-27
. after reading about the Qubes security system
and how the designer of that 
used vmware fusion on the mac to
 furthur isolate the kernel from the internet
I wrote a tutorial
for using ubuntu on mac.vmware`fusion .
[moving qubes`way on the mac]("http://amerdreamduh.blogspot.com/2010/12/moving-qubesway-on-mac.html")
. an intro to security with virtualization
and a getting started manual for mac os x .
 .  this shows how some security experts have agreed,
vmware`Fusion can make the mac *more* secure .

---

