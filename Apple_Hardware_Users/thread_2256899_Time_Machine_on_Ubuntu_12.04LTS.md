---
title: "Time Machine on Ubuntu 12.04LTS"
date: 2014-12-15
forum: Apple Hardware Users
---

### Post by orsome1 on 2014-12-15
First must say I am a complete Noob to Ubuntu so my knowledge here is very limited

Have Ubuntu server set up as my HTPC. Current Drives formated ext3 and shared via Samba.
My Mac can see these drives no problem - read and write
I have now added a new Internal Drive and formatted it to hfs+ with 3 partitions using GParted
Set up mount point as /TimeMachine and then mounted the partitions as /TimeMachine/Data1, /TimeMachine/Data2 and /TimeMachine/Data3 - and mounted all 3 partitions on that drive accordingly in the FSTAB

The goal is to set this internal Drive as my Time Machine volume for backups.
I have followed the setup at   [https://kremalicious.com/ubuntu-as-mac-file-server-and-time-machine-volume/](https://kremalicious.com/ubuntu-as-mac-file-server-and-time-machine-volume/)

However like much of my experience with Ubuntu it has not quite worked out that easily. My Mac cannot see the TimeMachine volumes I have set up - again can see all the Samba shared volumes no problem.
Have installed Netatalk and set up AppleVolumes.default as follows:

*# The line below sets some DEFAULT, starting with Netatalk 2.1.*
*:DEFAULT: options:upriv,usedots,tm*

*# By default all users have access to their home directories.*
*~/TimeMachine			"TimeMachine"*
*~/TimeMachine/Data1 "Backup for Melissa" allow:alan cnidscheme:dbd options:usedots,upriv,tm*
[I]~/TimeMachine/Data2 "Backup for Melissa" allow:alan cnidscheme:dbd options:used$
[/I]~/TimeMachine/Data3 "Backup for Melissa" allow:alan cnidscheme:dbd options:used$Then set up Avahi

after doing everything as per kremalicious I am still no closer to getting this right and I am sure its in my settings somewhere - but not knowing enough about Ubuntu I just cant find it
Would most appreciate some assistance in getting this right

---

### Post by este.el.paz on 2014-12-15
> **orsome1 said:**
> First must say I am a complete Noob to Ubuntu so my knowledge here is very limited

Have Ubuntu server set up as my HTPC. Current Drives formated ext3 and shared via Samba.
My Mac can see these drives no problem - read and write


I spent a couple minutes reading thru your link of instructions . . . and I have had some experiences with the problems of connecting two Macs together using AFP . . . there are numerous little things that can make that "complicated" . . . .  But, first thing, those instructions were from '08 . . . which might be a tad "old" . . . among other things, these days "ext4" is the recommended formatting . . . .  Also, from down in the instructions:

> So you should try a minimal way: On my Ubuntu boxes I have no other file  sharing protocol like samba or NFS enabled (even not installed) so the  samba hostname and the AFP hostname can’t interfere with each other.  Also I’ve left the Workgroup field blank under System >  Administration > Network > General tab.

Seems like the easier way would be to just have an external HD set up by firewire for Time Machine backups . . . ????

e.e.p.

---

### Post by orsome1 on 2014-12-18
they may be old but there are various links I have looked at and all follow similar lines.
to use an external HD does not suit my purposes. Have the internal drive so just need to fine the small break in the chain to get it all to connect

---

