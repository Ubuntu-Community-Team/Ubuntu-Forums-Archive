---
title: "Repo error:  &quot;Sub-process gzip returned an error code (1)&quot;"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Phrawm48 on 2007-03-31
Sigh...  Yet again, my *sources.list* seems to be pointing to the wrong place...(?)

If I use Synaptic to reload my list of repos, I receive the following error (line break added to enable display of entire message):

> [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:")[:]("http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:")
 Sub-process gzip returned an error code (1)
Here's the current contents of my *etc/apt/sources.list*:

> ## Uncomment the following two lines to fetch updated software from the network
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

## Add Wine repository.  RB, 2007-03-27
deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/I've also tried using the information on the following page to "reset" my repos and start over:

**[ Enabling Extra Repositories]("http://www.psychocats.net/ubuntu/sources")**

I sure wish I could learn how to fix these myself.  In the meantime, can anybody please help me clear my existing **error code (1)**?

Cheers & thanks,
Ric
SFO

---

### Post by zvacet on 2007-03-31
```
sudo aptitude update
```
```
sudo aptitude upgrade
```

---

### Post by Phrawm48 on 2007-03-31
Thanks.  Received and error, per the following (line breaks and formatting added for readability):

> 
[B]ric@ric-desktop:~$ sudo aptitude update
Password:

[/B]Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://]("http://archive.ubuntu.com")[COLOR=black][archive.ubuntu.com]("http://archive.ubuntu.com") dapper-updates[/COLOR] Release.gpg [191B]

...[list of packages deleted from quoted list to improve readability]...

Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources

[COLOR=Red][B] Ign [http://]("http://archive.ubuntu.com")[COLOR=black][archive.ubuntu.com]("http://archive.ubuntu.com") dapper-updates[/COLOR]/main Packages
[/B][/COLOR]
Hit [http://]("http://archive.ubuntu.com")[COLOR=black][archive.ubuntu.com]("http://archive.ubuntu.com") dapper-updates[/COLOR]/restricted Packages

...[list of packages deleted from quoted list to improve readability]...

Get:6 [http://]("http://archive.ubuntu.com")[COLOR=black][archive.ubuntu.com]("http://archive.ubuntu.com") dapper-updates[/COLOR]/main Packages [177kB]
99% [6 Packages gzip 0]

[COLOR=Red][B]gzip: stdin: not in gzip format
Err [http://]("http://archive.ubuntu.com")[COLOR=black][archive.ubuntu.com]("http://archive.ubuntu.com") dapper-updates[/COLOR]/main Packages
  Sub-process gzip returned an error code (1)[/B][/COLOR]
Fetched 6B in 4s (1B/s)
Reading package lists... Done
I guess the question is where the **[COLOR=black]archive.ubuntu.com dapper-updates[/COLOR]/main Packages** piece is coming from.

Note, too, that the following URL leads a repository-looking(?) page:

[URL="http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz"]**http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz**
[/URL]
So I'm still receiving the error.  Can you please make any additional suggestions?

Cheers & thanks,
Ric
SFO

---

