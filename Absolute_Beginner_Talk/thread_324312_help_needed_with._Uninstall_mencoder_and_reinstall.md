---
title: "help needed with. Uninstall mencoder and reinstall newest version."
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by stoer on 2006-12-23
Hi all.
I've been working on a film segment using mencoder, ran into some problems and got the following advice.

"  [I]1. You are using MEncoder 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team however I'm using MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team. 
 So, I think you could try the following:
 
 1. Remove mencoder and install the one in the Ubuntu repos, (Avoiding the third party ones), if you have third party repos, maybe you could remove it first, replace mencoder, and then put the third party repos back.
 -> Step: Remove third party repos which you have added.
 -> Remove mencoder
 -> Reload repos (Synaptic) or apt-get update
 -> Install mencoder (from the ubuntu repos)
 -> Put back the third party repos (however, do not update mencoder to the one provided by the third party repos)[/I] "


I've tried uninstalling using synaptic, and reinstalling it, again using synaptic.
The problem is i still get the same version installed, MEncoder 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team .
What 3rd party repo's might be influencing this? And how do i check this?

Really appreciate your help here.

---

### Post by jvc26 on 2006-12-23
The third party repos - you could go to your sources.list and comment out (put a # in front of the line) any third party repos you have in there, then 
```

sudo apt-get update

```
and try to install it again that may well stop the 3rd party version installing.

Then you can go back to your sources.list and remove the #s from in front of the entries.

Editing the sources.list (if you havent done it before) is covered here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Hope that helps.
Il

---

### Post by stoer on 2006-12-24
Thanks very much for the reply,
I'll give it a try when i get home tonight, working at the moment. 

I guess it should also be possible to use the original sources list in place of any modified one made since installation, 
(why didn't i think of that....](*,) )

Happy xmas. :)

---

### Post by stoer on 2006-12-24
I've tried this, first substituting my original sources.list(back up) for my current sources list.
I've also tried reading through it, i don't see any 3rd party repos.

But when i then unistall mencoder and then reinstall, (using synaptic) i can only see the older version available for download (the one i already have).

MEncoder 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team is what i get when searching using synaptic. I can't find 

 mencoder 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team.
Tried following the link [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources), but even after this i'm getting the same thing....

(Anybody that can tell me if mencoder 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team. is the official latest 6.06 repo version?)

This leaves me a little bit confused](*,) ](*,) ](*,) 
Any ideas? Anybody? Please!

Sources.list Old backup. ( now replaced with the list in psychocats link )

```
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted
# deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

# deb http://www.beerorkid.com/automatix/apt dapper main
```

---

