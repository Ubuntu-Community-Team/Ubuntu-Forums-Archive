---
title: "Problem with dependencies while installing easytag"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by fidolip on 2007-02-15
Aloha!

First of all, want to thank you all! I have been using ubuntu for few weeks now, and, thanks to you, I was able to find solutions to almost all problems I encountered during that time.:-)

However, now I am struggling with something I couldn't find an answer to. Here it goes:

I am using Exaile as my music player. It works quite alright - have a lot of troubles with my mpc files and them not being seen (or seen improperly) in database. I think it's the problem with ID3 tags, so I decided to upgrade tags of the files that are problematic. Search on the forum gave me an answer - easytag. So I tried to install it and got a dependency problem - it's missing libid3-3.8.3. Nothing special, I download the file and try to install it. But this gives me another error:

dpkg: regarding .../libid3-3.8.3_3.8.3-4.1-i386.deb containing libid3-3.8.3:
libid3-3.8.3c2a conflicts with libid3-3.8.3
 libid3-3.8.3 (version 3.8.3-4.1) is to be installed
dpkg: error processing /home/fidolip/Desktop/libid3-3.8.3_3.8.3-4.1-i386.deb (--
install):
conflicting packages - not installing libid3-3.8.3

So I figured - hey, I'm just gonna remove libid3-3.8.3c2a, install the other one and problem solved. I tried it and got this message:

fidolip@laptop:~$ sudo aptitude remove libid3-3.8.3c2a
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
The following packages are BROKEN:
  python2.4-id3lib
The following packages have been kept back:
  cdrdao dvd+rw-tools lame liblame0 libmodplug0c2 libmpcdec3
The following packages will be REMOVED:
  libid3-3.8.3c2a
0 packages upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
Need to get 0B of archives. After unpacking 356kB will be freed.
The following packages have unmet dependencies:
  python2.4-id3lib: Depends: libid3-3.8.3c2a but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
python-id3lib
python2.4-id3lib
ubuntu-desktop

Score is -1003

Accept this solution? [Y/n/q/?]

And now a question to you guys - is it safe to remove these packages? I am programming in python and would prefer not to lose it. Also - removing 'ubuntu-desktop' sounds a little scary to me..

Thanks in advance!

Oh, almost forgot - my ubuntu version is dapper.

---

### Post by dbbolton on 2007-02-15
did you try installing it from synaptic

---

### Post by fidolip on 2007-02-15
Geez.. I feel sooooo stupid.. Yeah, I tried it now and it installed without any problems.

Thx dbbolton!

---

