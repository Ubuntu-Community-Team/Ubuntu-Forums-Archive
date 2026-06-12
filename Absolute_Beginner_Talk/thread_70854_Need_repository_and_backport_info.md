---
title: "Need repository and backport info"
date: 2005-10-01
forum: Absolute Beginner Talk
---

### Post by bk452 on 2005-10-01
I've been gone for a few months and I went to update Hoary and now I have a complete disaster on my hands.  I have to reinstall but I was thinking maybe I should go with the Breezy thing that's out until the official version is ready.

So I need the repository and backport info since whatever I did with the present info took down the OS.

---

### Post by DJ_Max on 2005-10-01
The hoary backports are 
```
deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse
```
This is to be used with Hoary only. There will be Breezy backports when DD is started.

If you want breezy, I would grab a colony or preview CD of Breezy, because if you current os is working, I don't think a upgrade will work.

BTW, the breezy repos, just change everything "hoary" to "breezy".

---

### Post by bk452 on 2005-10-01
[QUOTE=DJ_Max]The hoary backports are 
```
deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse
```
This is to be used with Hoary only. There will be Breezy backports when DD is started.

If you want breezy, I would grab a colony or preview CD of Breezy, because if you current os is working, I don't think a upgrade will work.

BTW, the breezy repos, just change everything "hoary" to "breezy".[/QUOTE]


My current Hoary is a mess.  I think I'll go for Breezy and give it a try.  Thanks for the repo info.  I was  still a little shaky where they were concerned.  Thanks.

---

### Post by DJ_Max on 2005-10-01
No problem. Also, if I may ask, what does your current sources.list look like. Maybe I can figure out what went wrong, so it won't happen again.

BTW, when you do ```
sudo apt-get -f install
``` what do you get.

---

### Post by Ruddigger on 2005-10-01
Sorry to post this here, but why are the backports such a big deal? I'm new to Ubuntu, and haven't really figured out what the backports repositories are.

More in subject with the topic, it is allways useful to do aptitude (or apt-get) dist-upgrade, instead of just upgrade, because it solves depencenies better, specially if you don't upgrade in a while

---

### Post by bk452 on 2005-10-04
[QUOTE=DJ_Max]No problem. Also, if I may ask, what does your current sources.list look like. Maybe I can figure out what went wrong, so it won't happen again.

BTW, when you do ```
sudo apt-get -f install
``` what do you get.[/QUOTE]

Sorry for the late replay. I lost my hardrive yesterday and I just got back up.  I think the problem is that I'm still kind of new and I thought I knew what I was doing.  At least just enough to make me dangerous.

---

