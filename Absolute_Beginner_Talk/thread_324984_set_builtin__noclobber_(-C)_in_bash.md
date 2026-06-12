---
title: "set builtin:  noclobber (-C) in bash"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by beauty on 2006-12-24
I'm trying to "set -C" which is a 'noclobber' option in bash (noclobber is so outputs of commands, when re-directed to files, don't automatically over-write an existiing file).  I found plenty of material with google and such, but here's what I can't find in black and white:

How exactly do you implement the set builtin?  I tried it from bash, and I tried to add it to the 'command' line of my bash launcher, but it doesn't work.

---

### Post by po0f on 2006-12-25
beauty,

According to [ABS](http://tldp.org/LDP/abs/html/), you can turn on noclobber with a `set -o noclobber`, which you would probably put in either ~/.bashrc or ~/.bash_profile.  To use it on a script by script basis, use this as the she-bang line:
```
[FONT="Courier New"]#!/bin/bash -C[/FONT]
```

---

### Post by beauty on 2006-12-25
> **po0f said:**
> According to [ABS](http://tldp.org/LDP/abs/html/), you can turn on noclobber with a `set -o noclobber`, which you would probably put in either ~/.bashrc or ~/.bash_profile.  

Thanks, po0f goes my problem (ha).  Good link above.  

Since I wanted to apply it system wide, I placed `set -o noclobber` in /etc/bash.bashrc.  This works (I claimed I tried that, but I guess I goofed somewhere.)

I'm going to change the subject, because I need a vehicle to report sth strange on my system.  It all started when the `primary` user on the system (me) couldn't play sound.  I call `me` primary because that was the first user during the distro install, and a few applications have asked me to identify `primary user.`

Anyway, root-cause was `me` was not included in relevant lines in /etc/group, for example
```
audio:x:29:user1,user2,user3
```
There were a half dozen lines similar to this so I added `me` in all cases, and several strange behaviors in the GUI disappeared at once.
```
audio:x:29:user1,user2,user3,me
```
I have been tracking this trail forever.  Difficult to search it out with keywords ...

I think I had better create a new user and migrate `me` to `newuser` to make a clean get-away.

---

### Post by po0f on 2006-12-25
beauty,

Oh yes, I find ABS to be absolute must-have documentation for any serious scripter.  :)

The output I get from running `groups` (which will tell you what groups you belongs to, intuitive, eh?) follows:
```
[FONT="Courier New"]$ groups
brett adm dialout cdrom floppy audio dip www-data video
plugdev lpadmin scanner admin postgres[/FONT]
```
Besides the 'www-data' and 'postgres' groups, I haven't explicitly added myself to any other groups, so it might be safe to say that the above are the defaults for the 'primary' user (sans what I added).

---

