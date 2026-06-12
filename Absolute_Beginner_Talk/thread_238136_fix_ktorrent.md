---
title: "fix ktorrent"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by mlie on 2006-08-17
my ktorrent crashes and I tried to uninstall and remove it, and I get the error message below after I reinstalled it and ran it again.
Failed to open device
terminate called after throwing an instance of 'bt::Error'
KCrash: Application 'ktorrent' crashing...
DCOP aborting (delayed) call from 'anonymous-7815' to 'ktorrent'
ERROR: Communication problem with ktorrent, it probably crashed.

---

### Post by GarethMB on 2006-08-17
Which version of kKorrent are you using?

I think i had this problem once when i rename some of the files it was trying to load.

---

### Post by mlie on 2006-08-17
I can't even see the version of the Ktorrent because before I can do anything it crashes. I think it should be the latest one since I have tried to remove and reinstalled it using apt-get update ktorrent

---

### Post by GarethMB on 2006-08-17
In a terminal type:

```
ktorrent -v
```

By the sounds of it you're running ktorrent 1.2 (just a guess as 2.0 isn't in the repos) Head over to [www.ktorrent.org](www.ktorrent.org) if thats the case and grab 2.0, if you get the i386 binary i compiled you might have to use 

```
dpkg -i --force-all name_of_file.deb
```
to install it as i did not compile it to replace the ktorrent in the repos.

Once you're sure that you're using the latest ktorrent, we'll go from there.

May I ask what torrent you are trying to open? And whether you have altered the saved data for it at all?

---

### Post by Divide By Zero on 2006-09-05
I got about as far as mlie, with the same result.  I recognize that this is -K-torrent, and I'm trying to run it in -G-NOME, but I really liked it when I gave kubuntu a spin, and couldn't find a GNOME equivalent, so I thought I'd give it a shot.  Anyhow, the crash notice follows:

dbzero@ubuntu:~/Desktop$ ktorrent &
[1] 13436
dbzero@ubuntu:~/Desktop$ kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
DCOP aborting call from 'anonymous-13436' to 'ktorrent'
ERROR: Communication problem with ktorrent, it probably crashed.

Any way around it?

---

