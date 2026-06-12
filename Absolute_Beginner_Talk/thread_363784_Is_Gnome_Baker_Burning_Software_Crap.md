---
title: "Is Gnome Baker Burning Software Crap?"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by ielliott on 2007-02-17
I've tried to burn a couple dvds using it, and every time it has failed.

When i used to have Windows XP on this PC the burner worked fine.

I don't really have any reason why it could be failing.

I just don't want to be wasting a bunch of DVDs until i get it right.

---

### Post by taurus on 2007-02-17
Then why not use another program to burn your DVD!  Nautilus can do the burning and so does k3b.

---

### Post by ielliott on 2007-02-17
> **taurus said:**
> Then why not use another program to burn your DVD!  Nautilus can do the burning and so does k3b.

I'm not very familiar with Linux cd burnings, that is why i was asking if it wasn't good or if i was just possibley doing something wrong.

Thank you though.

---

### Post by TeraDyne on 2007-02-17
I honestly recommend K3B over Gnome Baker, as GB has given me nothing but trouble in the past. Nautilus is ok for burning, but I think K3B just does it better.

---

### Post by ielliott on 2007-02-17
> **TeraDyne said:**
> I honestly recommend K3B over Gnome Baker, as GB has given me nothing but trouble in the past. Nautilus is ok for burning, but I think K3B just does it better.

Is K3B. KDE only or can you run it using Gnome?

---

### Post by TeraDyne on 2007-02-17
K3B can be run in GNOME. Any KDE app can be run in GNOME, and vice versa.

---

### Post by taurus on 2007-02-17
Yes, k3b is KDE app but you can run it in Gnome just fine.  I use it to do all my burning in Gnome & XFce4.

```
sudo aptitude update
sudo aptitude install k3b
```

---

### Post by aidanr on 2007-02-17
i'd try out brasero first,  it's very k3b like but it's gtk2 so you don't have to install the kde libs

---

### Post by mcduck on 2007-02-17
Gnomebaker has never failed in my use. But if it doesn't work for you, K3B is good (just a bit ugly in Gnome)

---

### Post by keithweddell on 2007-02-17
I have to say that I gave up trying to get gnomebaker et al to burn CDs.  Now I just use cdrecord from a terminal.  It's the backend for most of these programmes anyway.  And it's not too difficult to work out the required settings from the man page or from googling for a howto.  Not really got into burning dvds yet.

Keith

---

### Post by meng on 2007-02-17
As others have mentioned, there are many choices including the in-built CD/DVD burning function in Nautilus.

What sort of failure is occurring? Are you getting an error message or the end result corrupted?

---

### Post by ielliott on 2007-02-17
> **meng said:**
> As others have mentioned, there are many choices including the in-built CD/DVD burning function in Nautilus.

What sort of failure is occurring? Are you getting an error message or the end result corrupted?

Just seems like a failure in the middle,

maybe i'll try to burn later and post again.

Is there any way to easier search for posts by yourself in this forum?

---

### Post by jvc26 on 2007-02-17
Search for posts by yourself? As in ones you've posted? If so, search->find all my posts, if just a general search then the link in my sig should help. I use k3b (on the topic) as I preferred it to Gnomebaker.
Il

---

### Post by ielliott on 2007-02-17
CDRW successful.

Maybe it was just what i was burning.

I can't find my stack of dvds though.

---

### Post by BlaineM on 2007-02-24
I like how gnome baker looks, but not how it burns, and k3b how it burns, but I think it is ugly as hell in gnome.  Im up for other options... command line cdrecord seems to run well and fast.  also dvdrw-tools ( I think thats how it is spelled) package.  I dont know if it is in the repos, I have used it at work with centOS.

Im looking for another gnome based program to burn cds, and dvds.  any great suggestions would be appreciated.

---

### Post by klein de usa on 2007-02-24
hi 
does any one use xcdroast?

---

### Post by crapapelada on 2007-02-26
I just installed K3b but not tested yet.
Just wanted to say that to me it doesn't look that ugly in Gnome; do you really think it does?
:guitar:

---

### Post by mcduck on 2007-02-26
> **crapapelada said:**
> I just installed K3b but not tested yet.
Just wanted to say that to me it doesn't look that ugly in Gnome; do you really think it does?
:guitar:
It depends on what kind of theme you are using in Gnome. I have black&red theme, and all KDE apps are light grey & blue so they don't really fit with the rest of my desktop..

---

### Post by igknighted on 2007-02-26
Does gnome not have the ability to theme KDE apps?  I know KDE can theme GTK apps.

---

### Post by Atrio05 on 2007-03-04
Hey just want to throw in my 2 cents and tell all of you that gnome baker is a really decent app you just have to open like this :

[I]first hit ctrl + F2

then in the prompt box type gksudo gnomebaker 

then hit enter and type in your password[/I] 

that way gnomebaker gets full access to the burner.

I think that should fix your problems if not I'm sorry!

and if you already knew this again I'm sorry!

---

