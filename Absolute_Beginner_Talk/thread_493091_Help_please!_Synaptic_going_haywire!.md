---
title: "Help please! Synaptic going haywire!"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Hellofriends on 2007-07-05
I just got online with dialup! yay! but this keeps coming up when I try to use Synaptic!

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
Every time I try to update or install Gstreamer :( :( :( Any Ideas?

---

### Post by Hellofriends on 2007-07-05
[IMG]http://i16.tinypic.com/6byezad.png[/IMG]
It gets to 41 of 42 then shows this picture.

---

### Post by overdrank on 2007-07-05
Hi that site maybe down but if you like you can comment out of your repos, use this command in the terminal
[HTML]gksudo gedit /etc/apt/sources.list
[/HTML]
then just comment out that link #
And later you can try it again by removing the comment.
Hope this helps and good luck!:popcorn:

---

### Post by Hellofriends on 2007-07-05
Thanks for the reply. If I copy and paste the link into firefox it starts loading odd characters, so I don't think the link is down. My apt database is incredibly old since it won't update :( I know because I have Ubuntu on my laptop and it has an update to date database. 
Ugh.
Why isn't this working?

---

### Post by wastedfluid on 2007-07-05
> **Hellofriends said:**
> Thanks for the reply. If I copy and paste the link into firefox it starts loading odd characters, so I don't think the link is down. My apt database is incredibly old since it won't update :( I know because I have Ubuntu on my laptop and it has an update to date database. 
Ugh.
Why isn't this working?


Comment out that source.  Then run your updates.  Occasionally, I get the same errors.  You can always enable it in the future by removing the #.

---

### Post by Hellofriends on 2007-07-05
> **wastedfluid said:**
> Comment out that source.  Then run your updates.  Occasionally, I get the same errors.  You can always enable it in the future by removing the #.
I tried that and it brings the error still and doesn't work. After I edited the file I was getting an error about duplicates as well? Here is what my list looks like, which should I try commenting out?
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
 deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
 deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
```

---

### Post by overdrank on 2007-07-05
Ok try and go to synaptic manager and fix broken packages, its under edit.Also after you do that look under setting, filters and select broken and search. Hopefully these tow methods will solve the issue.

---

### Post by Hellofriends on 2007-07-05
> **overdrank said:**
> Ok try and go to synaptic manager and fix broken packages, its under edit.Also after you do that look under setting, filters and select broken and search. Hopefully these tow methods will solve the issue.

Thanks for the reply. The error I got after editing the list file popped up again about there being a duplicate :/. I went into edit and fix broken packages then I went to the broken tab in the filters section and unclicked it, is that what you wanted me to do? that didn't work though.
Thanks again for the help

---

### Post by Hellofriends on 2007-07-06
Now it is doing it with a security package instead:( 
Someone have any ideas?

---

