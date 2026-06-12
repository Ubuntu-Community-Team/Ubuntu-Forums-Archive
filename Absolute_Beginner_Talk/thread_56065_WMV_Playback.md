---
title: "WMV Playback"
date: 2005-08-11
forum: Absolute Beginner Talk
---

### Post by lavarock09 on 2005-08-11
Hey All,

Is It possible To Play WMV's and If so How?

Lavarock09

---

### Post by nocturn on 2005-08-11
[QUOTE=lavarock09]Hey All,

Is It possible To Play WMV's and If so How?

Lavarock09[/QUOTE]

Yes, check the Ubuntuguide.org, it has more information about this.
Basicly, you need a player (mplayer, xine, vlc) and the w32codecs.

---

### Post by lavarock09 on 2005-08-11
Whenever I run this,

> sudo apt-get update 

it stops at 36%

why?

---

### Post by nocturn on 2005-08-11
[QUOTE=lavarock09]Whenever I run this,

 

it stops at 36%

why?[/QUOTE]

Can you post the complete output so we can see where it stops?

---

### Post by lavarock09 on 2005-08-11
ok,

> chris@ubuntu:~$ sudo apt-get update
36% [Connecting to us.archive.ubuntu.com (82.211.81.138)] [Connecting to security.ubuntu.com (82.211.81.151)] [Connecting to^
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg
  Could not connect to archive.ubuntu.com:80 (82.211.81.138), connection timed out [IP: 82.211.81.138 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (82.211.81.151), connection timed out [IP: 82.211.81.151 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out [IP: 82.211.81.138 80]
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204), connection timed out


---

### Post by nocturn on 2005-08-11
[QUOTE=lavarock09]ok,[/QUOTE]

The mirrormax site is quite slow, check the backports project, they have newer and faster mirrors.

I'm surprised at the us.archives.ubuntu.com though... is your internet connection slow on other sites?

---

### Post by lavarock09 on 2005-08-11
> check the backports project 

What do you mean?

and the internet connection isn't slow on other sites

---

### Post by Lord Illidan on 2005-08-11
Check out your /etc/apt/sources.list and take off the us part of the link.. maybe that is wrong, because I remember having a similar problem. In which part of the globe do you live?

---

### Post by lavarock09 on 2005-08-11
Uk

I can access the sites in Firefox

---

### Post by Lord Illidan on 2005-08-11
Then change the links in your sources.list from

[http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) 

to

[http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com)

Also, it might be wise not to use the mirrormax backports, as they are very slow!

---

### Post by nocturn on 2005-08-11
[QUOTE=lavarock09]What do you mean?

and the internet connection isn't slow on other sites[/QUOTE]

The backports project is providing the hoary-extras.  They used to have only the mirrormax server, but it was too slow and couldn't handle the load, so you are better of using another server.

The backports project has its own part on this forum:
[http://ubuntuforums.org/forumdisplay.php?f=47](http://ubuntuforums.org/forumdisplay.php?f=47)

I suggest using this server in apt sources:
deb [http://mirror.brianpuccio.net/ubunt...rts-repository/](http://mirror.brianpuccio.net/ubunt...rts-repository/) hoary-extras

---

### Post by lavarock09 on 2005-08-11
I have changed them all to Uk and it stidd does this

> chris@ubuntu:~$ sudo apt-get update
36% [Connecting to uk.archive.ubuntu.com (82.211.81.138)] [Connecting to security.ubuntu.com (82.211.81.138)] [Connecting to
 

and then freezes,

and how do I do that thing with the backports

EDIT: It Does This

> chris@ubuntu:~$ sudo apt-get update
36% [Connecting to uk.archive.ubuntu.com (82.211.81.138)] [Connecting to security.ubuntu.com (82.211.81.138)] [Connecting to^Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.151), connection timed out [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg
  Could not connect to archive.ubuntu.com:80 (82.211.81.138), connection timed out [IP: 82.211.81.138 80]
Err [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) hoary Release.gpg
  Could not connect to uk.archive.ubuntu.com:80 (82.211.81.151), connection timed out [IP: 82.211.81.151 80]
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204), connection timed out


---

### Post by lavarock09 on 2005-08-11
I'm Very Confused,

@Nocturn - What is that link you said, 

deb [http://mirror.brianpuccio.net/ubunt...rts-repository/](http://mirror.brianpuccio.net/ubunt...rts-repository/) hoary-extras

what is inbetween the dots (...)

And Where In Sources.list do I put it?

@Lord Illidan - > Also, it might be wise not to use the mirrormax backports, as they are very slow! 

What do I change?

---

### Post by nocturn on 2005-08-11
Ok, can you post the contents of /etc/apt/sources.list here?

Then we can see what is wrong.

---

### Post by lavarock09 on 2005-08-11
Ok,

> deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted


---

### Post by nocturn on 2005-08-16
[QUOTE=lavarock09]Ok,[/QUOTE]

Change these lines: 
```

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

```

deb http://mirror.brianpuccio.net/ubuntu-backports-repository/ hoary-backports main universe multiverse restricted
deb http://mirror.brianpuccio.net/ubuntu-backports-repository/ hoary-extras main universe multiverse restricted

```

I did have problems with the Ubuntu mirrors this morning, so if it does not work, try again later today.

---

### Post by ShagzModo on 2005-08-18
[QUOTE=lavarock09]Hey All,

Is It possible To Play WMV's and If so How?

Lavarock09[/QUOTE]

I installed vlc and all vlc plugins, it also plays wmv files.
You probably have to have your sources.list edited correctly with the right repositories to be able to install these packages...

regards, 

ShagzModo

---

