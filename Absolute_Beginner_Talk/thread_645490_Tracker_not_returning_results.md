---
title: "Tracker not returning results"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Confused-Dad on 2007-12-20
I've recently upgraded to the latest Ubuntu, and have found that Tracker does not seem to be working.

I have uninstalled Beagle, and reinstalled the Tracker, but it's still not returning any results.

Can anyone let me know what I can try to fix this?

Thanks

---

### Post by puccaso on 2007-12-21
remove the .config/tracker folder.

and force indexing (over night probaby) doing the following.

```
trackerd  -v 3 -t 0
```
as ur normal user.

does it work?

---

### Post by lubo on 2007-12-24
Hi Confused Dad! 
For more info about tracker read: [http://ubuntuforums.org/showthread.php?t=520853&highlight=tracker&page=4](http://ubuntuforums.org/showthread.php?t=520853&highlight=tracker&page=4)

Also open terminal and type: 
man trackerd

Tracker by default indexes only your home directory. To make it index your other direcotries you have to add them in the Sys->Pref->Indexing Preferences. 

To start indexing from scratch you have to:
1) Kill trackerd process (from Sys->Adm->System Monitor)
2) In terminal run:
trackerd -v 2 -R

parameter -v 2 means verbosity to 2.... to see what's it indexing at the moment.
parameter -R means reindex... to reindex everything again. 

In the link I gave you there is a problem described. In file ~/.config/tracker/tracker.cfg on line 63. It's written:
Dvision=4
While the author of the original post thinks (it looks the logical thing to me too) it should be:
Division=4 

Read the whole thread carefully. Read also the man help. I think that should be enough to fix this naughty misbehaviour... Right dad?!

;) Merry Christmas btw

---

### Post by lubo on 2007-12-24
Just to add... it worked perfectly for me :)

---

### Post by Confused-Dad on 2007-12-29
Thanks for your help and sorry for delay getting back to you. I tried your suggestion and it worked to an extent, i.e. it tracked Evolution files, but (unfortunately) not much else.

I've received another helpful reply, which has pointed out a spelling mistake in one of the set up files. This seems to be working and Tracker is currently ding its thing.

Thanks again.

Confused-Dad (still shaking, but less confused!!)

---

### Post by lubo on 2008-01-03
> **lubo said:**
>  ...

In the link I gave you there is a problem described. In file ~/.config/tracker/tracker.cfg on line 63. It's written:
Dvision=4
While the author of the original post thinks (it looks the logical thing to me too) it should be:
Division=4 

...


Do you mean this spelling mistake or there is another one?

I'm glad you've managed to solve your problem ;)

---

