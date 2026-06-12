---
title: "Installation files on drive... can I mount that dir as CDROM?"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by midngiht_jazz on 2007-12-10
Hi everyone,

I have a laptop with a CDROM that doesn't work.  I did some searching around and decided to try an installation of Ubuntu via my USB drive.  I was able to get it installed and I'm starting to learn the system.  I've never tried linux beyond a few short-lived glances, so I need a bit of help.

Here's the problem: I'm trying to do some updates (such as CODEC updates so I can play my MP3s), but the updates require the installation CD.  Is there a way that I can takeh te files from my USB drive and copy them to my main drive, then mount that directory as CDROM?  I don't plan on keeping the installation files on the USB drive so this would be helpful in times where the files were needed.

Thanks,

-Mike

---

### Post by flamelab on 2007-12-10
You don't need your installation cd .
Since you tell us that you are about to install codecs , you have succesfully installed Ubuntu .
If apt constantly tells you to use CD , run System -->Administration --> Software sources .
Then , enter your password . After that , press all "ticks" that you see there BUT press the "tick" on the bottom that is referring to the CD so that it is blank now .
After that , go to the second tab and remove the CD repository ( it tells you what to do ).

After that , in console press 

```
sudo -s -H
```
that helps you not to write sudo sudo sudo all the time 
and then 

```
apt-get update

apt-get upgrade
```

. Report after that , please !

---

### Post by midngiht_jazz on 2007-12-10
Thanks, I'll try that as soon as I get home!

---

### Post by midngiht_jazz on 2007-12-12
Thant worked... thanks!

---

### Post by flamelab on 2007-12-12
> **midngiht_jazz said:**
> Thant worked... thanks!

[img]http://www.adslgr.com/forum/images/smilies/wink.gif[/img]&#925;&#959; problem !

---

