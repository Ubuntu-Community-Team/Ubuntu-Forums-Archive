---
title: "Synaptic Errors"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by Jaygo333 on 2006-01-19
I get the following errors when trying to download from synaptic. 
How do I rectify without removing. I was trying to install some extra packages for beep media player.

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/x/xmms-jack/beep-media-player-jack_0.14-3ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/x/xmms-jack/beep-media-player-jack_0.14-3ubuntu5_i386.deb)
  404 Not Found
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/x/xmms-scrobbler/beep-media-player-scrobbler_0.3.8.1-2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/x/xmms-scrobbler/beep-media-player-scrobbler_0.3.8.1-2_i386.deb)
  404 Not Found
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/b/bmp-musepack/bmp-musepack_1.2-RC1-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/b/bmp-musepack/bmp-musepack_1.2-RC1-0ubuntu2_i386.deb)
  404 Not Found
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/libd/libdaemon/libdaemon0_0.8-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libd/libdaemon/libdaemon0_0.8-1_i386.deb)
  404 Not Found
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/i/ifplugd/ifplugd_0.26-2ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/i/ifplugd/ifplugd_0.26-2ubuntu1_i386.deb)
  404 Not Found

---

### Post by aysiu on 2006-01-19
Sounds as if your repositories list is messed up.
See the first link of my signature.

---

### Post by Razorback on 2006-01-20
Is it normal to have to reload the repositories?  I have found that I get an error when opening synaptic that certain repositories cannot be found.  It is a real pain to have to do this when you are on dial-up.  Is there some work around to not get this error and have synaptic remember the last reload?

---

### Post by jon_z on 2006-01-20
synaptic should remember the last reload, the reload is when you have (1) Added a repository to install a specific progam (2) a new version of a program has come out and your looking to upgrade..  if you are trying to install a specific package name..try in a terminal this:

```
sudo apt-get -f packagename
```
after sudo your password (you wont see it typed)
change the packagename to the package you are trying to install
i.e.  sudo apt-get -f beep

Anything I missed Aysiu?

---

### Post by bulldogzerofive on 2006-01-20
I got this when the following conditions occur:

1.  I am not connected to the internet.
2.  I start synaptic for the first time in a long while.


I think in most cases this happens either because:

1.  The automatic update tool tried to check for updates but the computer is not connected to the internet, so it cannot stat the sources.
2.  Synaptic itself is trying to update its sources but has no connectivity.  

In either case apt assumes the source it cannot stat is empty and so you get a very short list of available programs from the CD.

This went away when I turned off the automatic update tool.

---

### Post by dueY on 2006-01-20
[QUOTE=bulldogzerofive]I got this when the following conditions occur:

1.  I am not connected to the internet.
2.  I start synaptic for the first time in a long while.
[/QUOTE]

1.  This is obvious since you need the internet to use Synaptic.  How are you supposed to download the programs without being connected to the internet?
2.  New versions of programs come out somewhat frequently.  Repositories can also go down on occasion.  You have to refresh your list once in a while to see the latest programs and make sure the repository is still there!

---

### Post by Razorback on 2006-01-20
I agree.  But being on dial-up, I am not always on the internet.  It would be nice to look through the repository and see what is available without being connected.  Unfortunately, I have a really bad connect rate and having to update the repository alot can be a real inconvenience.

---

### Post by bulldogzerofive on 2006-01-21
[QUOTE=dueY]1.  This is obvious since you need the internet to use Synaptic.  How are you supposed to download the programs without being connected to the internet?
2.  New versions of programs come out somewhat frequently.  Repositories can also go down on occasion.  You have to refresh your list once in a while to see the latest programs and make sure the repository is still there![/QUOTE]


I was trying to offer the op a solution that worked for me and a little explanation of what I think is going on while trying not to sound like I think I am an expert (which I am not).

Why?  Because I want to browse packages without using one of the 30 hours a month of internet access that I have, or look at the properties of a file I might install.  I do not mind using an old list because, while new versions of programs do appear every once in a while, totem-xine (for example) will always be there.  This also appears to be what the op may want, so I told him/her how make the error go away and keep the old list:  turn auto-updates off.  You do not need the internet just to use synaptic, anyway, only while reloading your list or downloading something. 

I suppose I should have mentioned that s/he will need to update the list "manually" every once in a while.

---

