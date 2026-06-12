---
title: "External Hard Drive"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by MrBluesummers on 2007-09-04
First of all, I just want to say how much I love this OS.

Being a die-hard Windows user, I was skeptical.  I didn't (and still don't, really) know much about Linux, and the words "command line" struck terror into my heart.
But when I mentioned wanting to reformat my laptop since I got my self-built PC (for gaming) up and running, to a friend, he suggested Ubuntu.
I just downloaded, burned, and installed this on my laptop though (Late 2004 Sony Vaio PCG K-23) and I was completely proven wrong.
I installed Wine just fine on here and so far, doing things in the terminal hasn't given me a whole lot of problems.


This of course is a total newbie question, but I use a Hammer 80gig external hard drive alongside my other computers.

Will I be able to plug this in, format it to use Ubuntu and transfer things like my pictures, mp3's and such?

I really only want the laptop to provide:
Music
Movies
Internet
Word Processing (for college, since I got the laptop as a high school grad gift in July 04)


I'd assume if not Ubuntu had the tools, Wine would have the tools to make things like mp3's, avi's, etc work?

---

### Post by wolfen69 on 2007-09-04
yes, you can use it(external drive) just like you would in windows.

people wouldnt be using ubuntu if it couldnt play mp3's, vids, etc. it can do everything windows can do. and more. just ask us if you dont know.

---

### Post by jombeewoof on 2007-09-04
you do not need to format the external drive if you already have data on it.
just connect it, ubuntu will see it and load it on /media/disk
maybe disk1 or disk2, but it will automatically load it.
You will have to change the ownership of it though.
```

chown -R username:username /media/disk

```


for mp3's and such, check out the thread about multimedia, or google ubuntu win32codec and it will tell you what to do.

---

### Post by MrBluesummers on 2007-09-04
That is just amazing.  Thanks a lot folks.  =)

I'm sure the more I learn about this, I may end up asking my friend to help me configure the gaming PC to duel boot into Windows or Ubuntu.

And most definitely I'll explore further into Linux and learn how to use it as if it were as easy as Microsoft.

Can't just let it go to waste as a giant media player, can I?  =P

---

### Post by wolfen69 on 2007-09-04
i havnt touched a windows machine since april and dont miss it one bit. and i'm what you might consider a moderate power user. you won't regret learning linux. have fun.

---

