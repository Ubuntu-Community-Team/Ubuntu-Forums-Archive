---
title: "Mono Apps in Edgy"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by j o e l on 2006-12-28
Hello.  I tried posting this in the Install Forum, but so far no responses.  Hoping someone might see it here...

I began using Edgy a few weeks ago and have had a difficult time trying to get a couple Mono apps working.  Both Banshee and F-spot crash during startup and seem to give to indicate there are missing libraries, despite the fact I've tried to build-dep both and manually install each library that I am aware of.  Basically, both seem to indicate gnome-sharp can't be found...
**_F-Spot_**
> joel@baseCamp2go:~$ f-spot

** (/usr/lib/f-spot/f-spot.exe:8023): WARNING **: The following assembly referenced from /usr/lib/f-spot/f-spot.exe could not be loaded:
     Assembly:   gnome-sharp    (assemblyref_index=9)
     Version:    2.16.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/f-spot).


** (/usr/lib/f-spot/f-spot.exe:8023): WARNING **: Could not load file or assembly 'gnome-sharp, Version=2.16.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.



Is there some way to list what packages/libraries you have to double-check?  I'm still fairly new to Linux, so I'm not always sure what to do in troubleshooting these kinds of things.

Thanks for any assistance you might be able to give...

---

### Post by angkor on 2006-12-28
The error message 'Could not load file or assembly 'gnome-sharp' gives a couple of similar problems when I googled it but none of the threads had any answers. It seems this is a relatively unknown problem. That is probably why your previous thread is still unanswered.

[http://www.google.nl/search?hl=nl&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=Jg3&q=Could+not+load+file+or+assembly+'gnome-sharp+ubuntu&btnG=Zoeken&meta=]("http://www.google.nl/search?hl=nl&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=Jg3&q=Could+not+load+file+or+assembly+'gnome-sharp+ubuntu&btnG=Zoeken&meta=")

You should wait a little longer than 23 hours to see if someone more knowledgeable (than me) comes along to help you.

---

### Post by j o e l on 2006-12-28
Thanks, angkor!  I appreciate the effort, and you're right.  I probably should wait more than 24 hrs for a reply.  I apologize.  I just know how great this community is about helping each other out, and I wasn't sure if I posted in the right forum or not.  I research these forums a lot but haven't posted much.

Thanks again.

---

### Post by angkor on 2006-12-28
Your welcome. No need to apologize, we all know what it's like when you want something to work and you don't know how to do it.

Sadly I still haven't got a clue what could be wrong. Did you upgrade from dapper to edgy or did you do a fresh install?

If no one has a fix for you, you could try reinstalling mono-common, since the error is mono related. 

Mark the mono-common package for complete removal in Synaptic. Remember (write down or take a screenshot) the names of all the packages that are going to be removed so you will be able to reinstall them all. Click Mark and then Apply.

After removing them you can mark all the removed packages for installation and apply to see if it does any good.

One of the packages that will be uninstalled will be the ubuntu-desktop package. Don't worry about that. It is a meta-package (it's just there for upgrade purposes) and you can reinstall it safely later.

It's a bit of a hassle and I don't know if it'll do any good so maybe it's wiser to wait a wile to see if somebody knows a fix.

---

### Post by j o e l on 2006-12-29
Thanks again, angkor.

I think I did that once, but I'm not sure.  I'll try it again.  I don't see how it would hurt since it's not working anyway, right?

To answer your earlier question, I did a fresh install with Edgy.   I had wanted to implement a new partition scheme on my HDD, so I just used the opportunity to perform a fresh install of Edgy.

I appreciate your help.

---

