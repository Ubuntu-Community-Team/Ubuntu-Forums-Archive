---
title: "Possible malicious update from the repositories?"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by CidBahamut on 2007-11-22
Still being relatively ignorant I figured it best to ask around on here about what I encountered this morning.
I got on and clicked the little orange "updates available" button on my Dapper Drake install. Proceed to click the install button and get a warning in this form: 
[IMG]http://i91.photobucket.com/albums/k318/cidbahamut/Screenshot-5.png[/IMG]

Now I trust the people running the repositories, but I've also opened up more than the official ubuntu repositories as well and I want to know if anyone else has run into this recently and if it's a good idea to install these specific updates. 
I'm a bit wary as I just recovered my system recently and I'll be needing it stable for schoolwork over break.

Any advice, information or general banter would be appreciated.

---

### Post by tyggna1 on 2007-11-22
yeah, it could be malicious--but if you already trust the repositories, then all it is really saying is "You're going to update this from a non-official (ubuntu) source."   
I get that all the time with wine, 'cause I get it from wineHQ, and not from Ubuntu.

It's kosher, if you trust the source.

---

### Post by tyggna1 on 2007-11-22
hal stands for hardware abstraction layer--hides your private network from the internet.   If that one is malicious, then it could cause problems on the computer. (either enabling someone to install a rootkit, or something like that).   However, if it's genuine, then it's likely a security update--and will prevent that sort of thing from happening.

As with everything in Ubuntu, it's "use at your own risk."

Worse-case scenario:  you can't get online, until you repair hal.   You could probably do that by typing in
sudo dpkg-reconfigure hal

---

### Post by CidBahamut on 2007-11-22
Well I you're right about the whole "use at your own risk" part, but just in case I'd like to get a second opinion before proceeding. Just one of those drawbacks of being cautious I guess.

---

### Post by Dark_X on 2007-11-22
Paste this into the terminal and tell me what is in there.
```
gedit /etc/apt/sources.list
```

---

### Post by Paulmd on 2007-11-23
> **CidBahamut said:**
> Still being relatively ignorant I figured it best to ask around on here about what I encountered this morning.
I got on and clicked the little orange "updates available" button on my Dapper Drake install. Proceed to click the install button and get a warning in this form: 
[IMG]http://i91.photobucket.com/albums/k318/cidbahamut/Screenshot-5.png[/IMG]

Now I trust the people running the repositories, but I've also opened up more than the official ubuntu repositories as well and I want to know if anyone else has run into this recently and if it's a good idea to install these specific updates. 
I'm a bit wary as I just recovered my system recently and I'll be needing it stable for schoolwork over break.

Any advice, information or general banter would be appreciated.

What that refers to is that the repositories that those packages are from haven't been signed by gpg.

It's easier to show than to explain. Here is a fairly typical example:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

If you forget the part about adding the gpg key, when adding a package to your list, the update manager will whine that your packages can't be authenticated. (you can tell it to go to hell and update anyway, but it's better to authenticate all your repositories)

Different repositories sometimes have different methods of adding the gpg key, so always check their website for instructions first.

---

### Post by CidBahamut on 2007-11-23
```

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper multiverse universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security multiverse universe

deb [http://flomertens.free.fr/ubuntu/](http://flomertens.free.fr/ubuntu/) dapper main main-all
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) dapper main main-all
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) dapper main main-all

```

Well, there they are. I think my friend added a couple at the end when we were trying to get ntfs-config running, but other than that I've only opened up the ones I found out about on the ubutntu tutorials.



> **Paulmd said:**
> What that refers to is that the repositories that those packages are from haven't been signed by gpg.

It's easier to show than to explain. Here is a fairly typical example:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

If you forget the part about adding the gpg key, when adding a package to your list, the update manager will whine that your packages can't be authenticated. (you can tell it to go to hell and update anyway, but it's better to authenticate all your repositories)

Different repositories sometimes have different methods of adding the gpg key, so always check their website for instructions first.

Not sure I entirely understand the gpg keys. They're essentially files that let Ubuntu know that the repositories I'm downloading from are legit? If so that might explain why it's crying foul. New repositories my friend added for the ntfs-config didn't get authenticated from what it sounds like. Then Ubuntu tries to update HAL, presumably to deal with filesystem compatiblilty?

Or I could just be completely out of my gourd, which is why I'm here in the first place.

---

### Post by Paulmd on 2007-11-23
> **CidBahamut said:**
> ```

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper multiverse universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security multiverse universe

deb [http://flomertens.free.fr/ubuntu/](http://flomertens.free.fr/ubuntu/) dapper main main-all
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) dapper main main-all
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) dapper main main-all

```



Well, there they are. I think my friend added a couple at the end when we were trying to get ntfs-config running, but other than that I've only opened up the ones I found out about on the ubutntu tutorials.

Yes, the last 3 are what Ubuntu's complaining about. Presumably your friend forgot about the gpg keys (or never heard of gpgs in the first place) . What I do to find out how to install them  for a particular website:

For example, in your browser address bar, type:

```
http://flomertens.free.fr/ubuntu/

```

The page there explains how edit sources.list, which your friend did. Then it goes on how to add the gpg keys, which your friend didn't do (or didn't do for each of  the repos he added):

```
wget http://flomertens.keo.in/ubuntu/givre_key.asc -O- | sudo apt-key add -

```

It also mentions that [deb http://givre.cabspace.com/ubuntu/](deb http://givre.cabspace.com/ubuntu/), [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/), and
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) are mirror sites, ant to only add ONE of the list. Also

[http://flomertens.free.fr/ubuntu/ ](http://flomertens.free.fr/ubuntu/ ), isn't one of them.



Instead of those last 3 repositories, therefor, you should have ONE. I'm picking 
```
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) dapper main main-all
``` for no particular reason. 

> Not sure I entirely understand the gpg keys. They're essentially files that let Ubuntu know that the repositories I'm downloading from are legit? 

Yes.

>If so that might explain why it's crying foul. New repositories my friend added for the ntfs-config didn't get authenticated from what it sounds like. 

Yes.


>Then Ubuntu tries to update HAL, presumably to deal with filesystem compatiblilty?


It's trying to update HAL because the versions at one of these sites is newer than the one currently installed.


>Or I could just be completely out of my gourd, which is why I'm here in the first place

No, this is not trivial stuff. It's one of the many things that need further streamlining in Ubuntu.

---

