---
title: "system backup (snapshots)"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by vinceZZZZ on 2007-06-15
Hello all

i have recently been reading about how to back-up my entire Linux system...it is not too complicated.... as it only involves a couple of command line entries...

however, can anybody tell me..... is true to say that you need equal amounts of spare un-used disk space..to do an entire back-up of the used disk space that ubuntu takes?

and also, how long does a full back-up take?

what i am trying to do is a kind of system restore feature.... like winXP....where your machine can take a SNAPSHOT of the entire system before you start tinkering around....then if your tinkering around makes a mess of the system...you can at least restore the old snapshot back....

does anybody know how easy this snapshotting is?

V

---

### Post by nylecoj813 on 2007-06-15
I can give you a little bit of help (and worse comes to worse, a free bump ;) )

> 
however, can anybody tell me..... is true to say that you need equal amounts of spare un-used disk space..to do an entire back-up of the used disk space that ubuntu takes?


Yes, I believe this is true. I have used this method: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) and you will need enough free space to hold the backup. Someone correct me if I'm wrong!

> 
and also, how long does a full back-up take?


This depends on how large your system is. I have used maybe 6-7gb and although I didn't really keep track of how long it took (just did other things while it was going), it definitely wasn't more than an hour if I recall correctly. Sorry I can't be more specific!

> 
what i am trying to do is a kind of system restore feature.... like winXP....where your machine can take a SNAPSHOT of the entire system before you start tinkering around....then if your tinkering around makes a mess of the system...you can at least restore the old snapshot back....

does anybody know how easy this snapshotting is?


Can't say I know much about this, but I've heard of this program mentioned elsewhere: [http://www.rsnapshot.org/](http://www.rsnapshot.org/)

And the guide above says restoring the backup is just as easy as creating it, but I've never had to restore my backup. 

Anyways, good luck!

---

### Post by bren on 2007-06-15
i think it is also possible to use Ghost for linux to take a snapshot of entire partitions

i didnt use it yet but played with the liveCD and it allows for non or slightly or highly compressed according to the speed you want.

download ghost iso is first step....


Edit: partimage is another popular one...

more on both here [http://linuxappfinder.com/backupandrecovery/driveimaging](http://linuxappfinder.com/backupandrecovery/driveimaging)

---

