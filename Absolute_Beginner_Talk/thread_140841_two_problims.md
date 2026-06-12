---
title: "two problims"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by montablac on 2006-03-07
ok,i want a program and a plug in

1st the program,i want to install realplayer,its in the repostorys under the multiverse,it tells me to download the files off the site,so i find only two files,a binary and an RPM,i tryed to use alien to install the RPM,dident work,the binary also returns erors

2nd,is there a shockwave plugin for linux?

help with eather would be great

---

### Post by Xian on 2006-03-07
Add these two lines to your /etc/apt/sources.list to get realplayer:

```
deb http://cameronbergh.com/mirror/ubuntu/plf/ breezy free non-free
deb-src http://cameronbergh.com/mirror/ubuntu/plf/ breezy free non-free
```

[QUOTE=montablac]2nd,is there a shockwave plugin for linux?
[/QUOTE]

Shockwave or Flash??

---

### Post by montablac on 2006-03-07
i mean shock wave,not flash,flash is working fine

but thx for that one

[EDIT]
those sources dident work,is there any other?

---

### Post by stalefries on 2006-03-07
Nope, no shockwave for Linux.

---

### Post by Xian on 2006-03-07
[QUOTE=montablac]
those sources dident work,is there any other?[/QUOTE]

Didn't work in what way?
As you see below the package is indeed there...

```
$ sudo apt-cache policy realplay
realplay:
  Installed: 10.0.6.776-1plf1
  Candidate: 10.0.6.776-1plf1
  Version table:
 *** 10.0.6.776-1plf1 0
        500 http://cameronbergh.com breezy/non-free Packages
        100 /var/lib/dpkg/status
```

---

### Post by montablac on 2006-03-07
to bad about shockwave

and i KNOW its there,i just cant get it off the sever,dono why tho,maby its cause im on dial up?

---

### Post by 3rdalbum on 2006-03-08
Try going here: [https://player.helixcommunity.org/2005/downloads/]("https://player.helixcommunity.org/2005/downloads/")

and downloading the RealPlayer installer.

---

### Post by Jucato on 2006-03-08
Just for reference, there's a deb file for Real Player 10 in the [wikis]("https://wiki.ubuntu.com/RestrictedFormats#head-848295cba1b3591a4b4a0dbea5844fd5d2894b6b")

---

