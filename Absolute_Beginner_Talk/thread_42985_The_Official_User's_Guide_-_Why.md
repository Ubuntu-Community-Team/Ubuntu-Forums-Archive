---
title: "The Official User's Guide - Why?"
date: 2005-06-20
forum: Absolute Beginner Talk
---

### Post by jsimmons on 2005-06-20
It seems that a lot of basic stuff is included in the guide that could be included with the distro as scripts (like adding repositories, downloading the mscore fonts, and other such stuff).

Wouldn't it be a lot simpler just to add what can be added to the distro, and let the user still pick and choose what to run?  Just a thought...

---

### Post by az on 2005-06-20
Well, if you mean adding repositories, you can do that easily with synaptic.  

If you mean adding unofficial repositories, well, they are unofficial, so you cannot add them to the distribution.

For example, you can enable the multiverse repository and install msttcorefonts.  It will install them automatically.

As far as all the non-free stuff, it cannot be distributed with ubuntu.  Like mp3 support:  there is a licence involved.  Users can get away with installing free implementations for mp3 support, but when a distribution does it, they must but licences from the owners of the mp3 licence.

Linspire does this, but it is a proprietary and commercial distribution.

Other packages prohibit their distribution in some ways.  For example, Java.  there are free implementation of jave.  The official Sun version of java prohibits you from shipping java with your distribution if you offer other alternatives to it.  (Sun is not a shining example of free and open source software!)

Is this what you mean?

---

### Post by DJ_Max on 2005-06-20
To add to what azz said, there are literally thousands of software libraries, applications, etc.. Including all of them with the distribution would be a pain, cause huge ISO image downloads, would use too much disk space, and take time to remove most of the things people don't use.

---

### Post by sapo on 2005-06-20
We are trying to find a solution for this here:

[http://ubuntuforums.org/showthread.php?t=42553](http://ubuntuforums.org/showthread.php?t=42553)

---

### Post by jsimmons on 2005-06-20
[QUOTE=sapo]We are trying to find a solution for this here:

[http://ubuntuforums.org/showthread.php?t=42553](http://ubuntuforums.org/showthread.php?t=42553)[/QUOTE]


*THAT* is precisely what I was talking about.

I think a collection of ten scripts that do common post-install things would be great.  The difficulty would be picking the ten most common things that a new install would need.

Repositories
MS core fonts
Video codecs
DVD playback
CD/DVD record
Install BitTorrent 
Mounting Windows fat32/ntfs partitions (as read-only?)
Setting Ubuntu-related bookmarks in the web browser(s)

Finally, have a GUI app that puts all of these scripts into a list and let the user select which one(s) to do, and put an icon on the desktop that lets them run the app.

The only downsides to this idea are:

1) These scripts have to be reviewed, changed, and tested with each release of Ubuntu.

2) Invariably, someone is going to complain that they think the list should contain one or more different scripts.

---

### Post by poofyhairguy on 2005-06-20
[QUOTE=jsimmons]
The only downsides to this idea are:

1) These scripts have to be reviewed, changed, and tested with each release of Ubuntu.

2) Invariably, someone is going to complain that they think the list should contain one or more different scripts.[/QUOTE]

3. Some of those scripts might leave Ubuntu in a legally vulnerable position. Its great if the community does it though.

---

### Post by jsimmons on 2005-06-20
[QUOTE=poofyhairguy]3. Some of those scripts might leave Ubuntu in a legally vulnerable position. Its great if the community does it though.[/QUOTE]

If they're just scripts that do the downloading and installing, there is no legal position to be concerned with.  Afterall, the user would have to run the scripts themselves.

BTW, where in Texas are you?  I'm in San Antonio.

---

### Post by poofyhairguy on 2005-06-20
[QUOTE=jsimmons]If they're just scripts that do the downloading and installing, there is no legal position to be concerned with.  Afterall, the user would have to run the scripts themselves.

True. Luckily when backports is finished becoming official, maybe this sort of this can be added. As it is, I don't see an ubuntu dev.s including a script to install software from an uncontrollable third party repo.

[QUOTE=jsimmons]BTW, where in Texas are you?  I'm in San Antonio.[/QUOTE]

College Station. But I spend many of my weekends in Marble Falls.

---

