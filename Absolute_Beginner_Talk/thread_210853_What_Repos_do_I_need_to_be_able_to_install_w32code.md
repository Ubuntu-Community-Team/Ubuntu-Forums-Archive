---
title: "What Repos do I need to be able to install w32codecs &amp; flashplayer-mozilla?"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-07-07
I would like to install w32codecs &flashplayer-mozilla.

What Repos should I activate?

Thanks.

---

### Post by digby on 2006-07-07
> **dvarsam said:**
> I would like to install w32codecs &flashplayer-mozilla.

What Repos should I activate?

Thanks.
You need the universe and multiverse repositories.  See [here]("http://ubuntuguide.org/wiki/Dapper#Repositories") for instructions on how to enable them.

---

### Post by FredB on 2006-07-07
Both repositories, universe and multiverse.

But for win32 codecs, you'll have to add it from another repository, can't remember the name of. Just to a little search on the forums ;)

---

### Post by angkor on 2006-07-07
Add these repos to your /etc/apt/sources.list for w32codecs:

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

---

### Post by PriceChild on 2006-07-07
As well as win32codecs, I STRONGLY suggest that you follow this link on the wiki:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Its a very good tutorial for getting all of the media formats to work. Also, automatix or easyubuntu may easily help you get this working, (although the latter two won't let you understand how it works)

Please make sure you don't break any of your countries laws though :)

---

### Post by hajk on 2006-07-07
I recommend following the instructions on the RestrictedFormats page of the Ubuntu wiki -- this will supplement and complete the codecs and multimedia players that already came with Dapper.

---

### Post by dvarsam on 2006-07-07
Dear Angkor,

Thanks for your reply!

> **angkor said:**
> Add these repos to your /etc/apt/sources.list for w32codecs:

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

Adding the above 2 lines in my "fstab" file, helped me locate & install the "w32codecs" package.

Thank you very much!

P.S.> However, I _still _ seem to be having problem in finding  what line I nave to add to my "sources.list" file for the "flashplayer-mozilla" package. Any ideas?

---

### Post by aysiu on 2006-07-07
It's the multiverse repositories you need.
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) will set you up with that.

---

### Post by crystal on 2006-07-07
> However, I still  seem to be having problem in finding what line I nave to add to my "sources.list" file for the "flashplayer-mozilla" package. Any ideas?
Did you add "universe" and "multiverse" to the lines in /etc/apt/sources.list?

What I did (it may not be correct) was to follow the instructions of Firefox when I chanced upon a webpage requiring Flash.

---

### Post by SimzI on 2006-07-07
Just use Automatix tbh.

---

