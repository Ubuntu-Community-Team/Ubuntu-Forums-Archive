---
title: "Troubles with the Start Guide..."
date: 2005-09-15
forum: Absolute Beginner Talk
---

### Post by Insignius on 2005-09-15
I'm trying to follow the starter guide for a few things, but I am having trouble.

In some cases (Java I think for instance)

I would get this message:

```
Install these packages without verification [y/N]?
``` 

I would then type "y" and this would come up: 

```
E: Some packages could not be authenticated
``` 

In other cases I would get  this:

```
After unpacking 3146kB of additional disk space will be used. 
Do you want to continue [Y/n]? 
```  Again, I would press "Y," but it would come up and say "abort."  

What am I doing wrong?

---

### Post by Kapre on 2005-09-15
[QUOTE=Insignius]I'm trying to follow the starter guide for a few things, but I am having trouble.

In some cases (Java I think for instance)

I would get this message:

```
Install these packages without verification [y/N]?
``` 

I would then type "y" and this would come up: 

```
E: Some packages could not be authenticated
``` 

In other cases I would get  this:

```
After unpacking 3146kB of additional disk space will be used. 
Do you want to continue [Y/n]? 
```  Again, I would press "Y," but it would come up and say "abort."  

What am I doing wrong?[/QUOTE]


Insignius - are talking of the sun-java re1.5? If this is the one, are you using Hoary or Breezy? Reason I'm asking is if you're in Breezy you must use the universe - multiverse repos.

Try running sudo apt-get update and then try installing-d/l the file again.

K

---

### Post by rj686 on 2005-09-15
[QUOTE=Kapre]Insignius - are talking of the sun-java re1.5? If this is the one, are you using Hoary or Breezy? Reason I'm asking is if you're in Breezy you must use the universe - multiverse repos.

Try running sudo apt-get update and then try installing-d/l the file again.

K[/QUOTE]
 i did the apt-get update....and also what it says in teh guide to "add repositories" you hafta completely add the hoary repositories because as far as i can tell the "breezy restricted doesn't contain half the programs and or codecs we need"

---

### Post by Insignius on 2005-09-15
I tried that and it didn't work, but I didn't think it would.  I've run a bunch of updates even in the last few days. 

And, I am using Breezy, but I followed the "how to add extra repositories" part of the guide.

---

### Post by rj686 on 2005-09-15
[QUOTE=Insignius]I tried that and it didn't work, but I didn't think it would.  I've run a bunch of updates even in the last few days. 

And, I am using Breezy, but I followed the "how to add extra repositories" part of the guide.[/QUOTE]
 did u manually add the repositores ie type Hoary universe etc etc

---

### Post by Kapre on 2005-09-15
[QUOTE=rj686]did u manually add the repositores ie type Hoary universe etc etc[/QUOTE]

I just answered a thread regarding the repo list. [This](http://www.ubuntuforums.org/showthread.php?t=66032) shows my repo where I got what you're looking for

---

### Post by Insignius on 2005-09-15
[QUOTE=Kapre]I just answered a thread regarding the repo list. [This](http://www.ubuntuforums.org/showthread.php?t=66032) shows my repo where I got what you're looking for[/QUOTE]

I copied everything you had there into my source list. I think that only made it worse. Yikes.

---

### Post by Kapre on 2005-09-15
[QUOTE=Insignius]I copied everything you had there into my source list. I think that only made it worse. Yikes.[/QUOTE]

Insignius - Can you please post your repo list? Did you type refresh after you've copied the list? I'm using this list right now and no problem for me.

---

### Post by Insignius on 2005-09-15
```
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

```

straighted out sources.list file

---

### Post by openmind on 2005-09-16
I think I can help because I made the same mistake!

I think you're pasting multiple rows (or the whole paragraph)  out of the guide at the same time, that's the response you'll get.

Paste ONE line at a time, hit enter, then go back and do the next line etc. etc.......

let me know, 'cos it's my first attempt at actually helping someone! (I'm a noob myself).

---

### Post by poofyhairguy on 2005-09-16
I fixed it in your post. Copy and paste.

---

