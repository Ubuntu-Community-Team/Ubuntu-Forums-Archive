---
title: "IDE for c/c++"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by deepank on 2006-08-03
I want to ask if there is any IDE available in ubuntu for c/c++ like turbo in windows? If it is there please tell me about it.

---

### Post by carlosqueso on 2006-08-03
Never used turbo...but anjuta is a good IDE.  just ```
sudo apt-get install anjuta
``` and you're set.

---

### Post by Lord Illidan on 2006-08-03
First get c++ compiler by:

```
sudo apt-get install build-essential
```

Then you have a large choice of IDEs.
My fav is anjuta :

```
sudo apt-get install anjuta
```

---

### Post by deepank on 2006-08-03
When i start downloading anjuta, the terminal gets stuck at 

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe anjuta-common 1.2.4a-2ubuntu2
  Could not connect to archive.ubuntu.com:80 (82.211.81.182), connection timed out
0% [Connecting to archive.ubuntu.com (82.211.81.182)]


even though my internet connection is up and fine.

---

### Post by Lord Illidan on 2006-08-03
Can you give us your /etc/apt/sources.list please?

---

### Post by deepank on 2006-08-03
The contents of the file are : 

[I][I]# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
[/I][/I]

---

### Post by Faint on 2006-08-04
i got the compiler to install but when i try to install the anjuta with that link it comes up with this:
```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package anjuta

```

---

### Post by moma on 2006-08-04
My recommendations are

FLDev
[http://www.hardl.de/fldev/screenshots.php]("http://www.hardl.de/fldev/screenshots.php")

OpenLDev
[http://www.openldev.org/]("http://www.openldev.org/")

And maybe  XWPE
[http://www.identicalsoftware.com/xwpe/]("http://www.identicalsoftware.com/xwpe/")

Geany (quite a newbie)
[http://geany.uvena.de/]("http://geany.uvena.de/")

---

### Post by cstudent on 2006-08-04
I use one called Code::Blocks. 

Check out the website here:
[http://www.codeblocks.org](http://www.codeblocks.org)


Download the most recent .deb from svn here:
[http://forums.codeblocks.org/index.php?board=20.0](http://forums.codeblocks.org/index.php?board=20.0)

You'll still need to install build-essential using Synaptic, apt-get or aptitude, whatever you prefer. You'll also need to install some additional packages like wx-common. All additional packages can be obtained from the Ubuntu repositories. See my signature for a link to more information.

---

### Post by cstudent on 2006-08-04
> **deepank said:**
> The contents of the file are : 

[I][I]# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
[/I][/I]


Is this the complete contents of your sources.list?

---

