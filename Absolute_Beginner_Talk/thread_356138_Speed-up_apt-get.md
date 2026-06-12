---
title: "Speed-up apt-get"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by kitt on 2007-02-08
Hi folks,
            I have observed that apt-get is extremely slow at downloading the files it needs. In my case, wget downloads the same file from the same server almost twice as fast, while axel is nearly 10 times faster. Moreover, the connection is frequently closed in case of ap-get, and i end up wasting a lot of my time.
          Anyone else observed this, or is it only me? Also, is it possible to force apt-get to use wget/axel to fetch the required files?
          I'd be glad if someone helps me out here, thanks.

---

### Post by maxamillion on 2007-02-08
I have never heard of such a thing, but you might try aptitude and see if it does a little better.

```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install <blah>
man aptitude #for more info

```

might help .... not sure why it would, but you should use aptitude anyways.

aptitude is generally directly compliant with apt-get commands for ease of use for users who are used to apt-get.... if you need an explanation of what aptitude is, log onto irc.freenode.net #debian and type "!dpkg why aptitude" (without the quotes)

---

### Post by kitt on 2007-02-08
Aptitude, synaptic, adept, are all as slow as apt-get! :-(

---

### Post by tagginannie on 2007-02-08
> **kitt said:**
> Hi folks,
            I have observed that apt-get is extremely slow at downloading the files it needs. In my case, wget downloads the same file from the same server almost twice as fast, while axel is nearly 10 times faster. Moreover, the connection is frequently closed in case of ap-get, and i end up wasting a lot of my time.
          Anyone else observed this, or is it only me? Also, is it possible to force apt-get to use wget/axel to fetch the required files?
          I'd be glad if someone helps me out here, thanks.

Apt-get is only as fast as your Internet connection and the server. One thing can cause slow down file transfers is heavy usage,with the weekends being the
worst try downloading at different times during the day to see which time you 
get the fastest rate. Or try Synaptic, it is a GUI app similar to Windows Add and
Remove and groups the programs by category. I think it is the easiest and
fastest ways to install software in a Debain based distro. But what do I know?
this my first DEB. based distro lol. To get just type in sudo apt-get synaptic.




Suzy:KS

---

### Post by Rui Pais on 2007-02-08
> **kitt said:**
> Aptitude, synaptic, adept, are all as slow as apt-get! :-(

Isn't all of those suppose to use wget when packages are fetched?? 

Are you sure you get better time download same file from same server? 
that's very weird...

Have you tried to change mirrors. Even the ones close to you maybe slower then others faraway.

There is a nice app on repos called netselect or/and netselect-apt that automatically choose the best mirror to your case. Maybe give it a try and then check results. 

A big package fetched by apt (or any variant) should have an average download time identical of you get to any big package you manual download (without download accelerators). Small packages may vary, but bug ones are suppose to stabilize while downloading at maximum speed you network connection can handle.

---

### Post by kitt on 2007-02-08
Yes, i know it's wierd :-( 
I know this sounds unbelievable, but right now, apt is averaging 500 bytes/sec for a 3 mb file, while axel is up at 30 Kbps for a larger one (not same server though)

---

### Post by Rui Pais on 2007-02-08
> **kitt said:**
> Yes, i know it's wierd :-( 
I know this sounds unbelievable, but right now, apt is averaging 500 bytes/sec for a 3 mb file, while axel is up at 30 Kbps for a larger one (not same server though)

axel is a download accelerator. you must compare times with wget since apt will not use any accelerators.
 
The question should be, what is your normal download times using firefox or wget for an iso or a big file (500b/s? much higher?) if they are much higher then the you may have a slow mirror set to download (i'm used an ubuntu mirror that is on the same city i live and then i discover that the fastest is one on the north of the country much var away...)

Check netselect.

---

### Post by kitt on 2007-02-08
netselect returns this:
netselect was unable to find a mirror, this probably means that
you are behind a firewall and it is blocking traceroute.

PS: I am behind a proxy.

---

### Post by Rui Pais on 2007-02-08
> **kitt said:**
> netselect returns this:
netselect was unable to find a mirror, this probably means that
you are behind a firewall and it is blocking traceroute.

PS: I am behind a proxy.

Maybe that's the reason... i know very little about proxys and/or firewalls, can't help much here :(

Are 500 m/s much slower than the nominal speed give by your internet provider? 
(as examples, mine gives a nominal speed of 2M and i download stuff at ~210 K/s, before it was 1M and download ~100k/s...)

As i read around, there a typical problem where people have abnormal slow connection and solve the problem by turn off ipv6... may that would be your case...

good luck.

---

### Post by bikeboy on 2007-02-08
Ok, what's your current /etc/apt/sources.list look like?

Try changing it from eg. [http://archive.ubuntu.com](http://archive.ubuntu.com) to [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com), but use the appropriate country code for where you live.

---

### Post by kitt on 2007-02-08
I have disabled ipv6 and all.. :-(
Is there no way i can use axel to download the files? Any hacks?
And regarding the country specific mirrors, i had once used in.archive.ubuntu.com (i reside in India). It turned out to be slower..

---

### Post by Rui Pais on 2007-02-08
and here is a detailed list of ubuntu mirrors:
[https://wiki.ubuntu.com/Mirrors?action=show](https://wiki.ubuntu.com/Mirrors?action=show)

---

### Post by Rui Pais on 2007-02-08
> **kitt said:**
> I have disabled ipv6 and all.. :-(
Is there no way i can use axel to download the files? Any hacks?


There was a project, [apt-axel]("http://home.gna.org/apt-axel/"), but it's dead as far as i can see (but maybe the code still works, it's just a script, i think) 
Or maybe the [svn version]("https://gna.org/svn/?group=apt-axel") are still alive...
Other then that, a bad hack would be move wget -> wget_old and ln -s /usr/bin/axel /usr/bin/wget (:()

> And regarding the country specific mirrors, i had once used in.archive.ubuntu.com (i reside in India). It turned out to be slower..
Check my previous post for a list...
Yep, i remember that a few years ago here all portuguese mirrors was slow and luckily our neighbor Spain have excellent speedy ones. If netselect-apt fails you must need to make several trials...

---

### Post by dumbbeatnix on 2007-03-02
Thank you Bike Boy.

I was experiencing slow download from aptitude, but fast internet speeds (ie. with firefox).  Thanks to you I changed all my /etc/apt/sources.list to au.archive.[etc], and you wouldn't believe it I got 160Kbs.

Cheers :popcorn: 
dumbbeatnix

---

### Post by mgibson on 2007-11-22
Based on the assumption that my knowledge about apt-get is correct following proposal to accelerate overall install time with apt-get:

AFAIK apt-get first downloads all packages, and then installs them.
Instead of first downloading all packages apt-get could start installing as soon as the first package is downloaded. (while considering dependencies)
That would not speed up the download time, but it would reduce the overall installation time dramatically.
For the initial installation of a fresh ubuntu system this would be a dramatic improvement.

If my assumption is wrong pls. also let me know.

---

