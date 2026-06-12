---
title: "The ideal file system and partition layout: please share your insights! :)"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by adma on 2006-12-21
I used Windows for many years before switching to Ubuntu and partition layout was really a no-brainer: one drive for the system, one drive for documents, music, etc. This was the way to go for simple day to day use.

Given all the potential of the Linux file system, I haven't quite figured out what will be the ideal setup. I suppose a single partition is out of the question.

Should I have one partition for / and another (mounted on e.g. /home/username/mystuff) to put the documents? Or should I just mount this second partition as /home?

Mounting as /home sounds promising but raises a question: if one day I want to wipe my system and say install a different version of Ubuntu, how likely is it that the settings stored on all the hidden folders on /home/username will be compatible with this new version of Ubuntu?

What is the ideal setup, after all? Please provide your insights! :)

---

### Post by Sef on 2006-12-21
How often do you back up your data?  If you back up all frequently, then a home partition is not really necessary.  However, if you don't back up that much then you should have a home partition.

Generally, you need two partitions, root (/) and swap.  If you have a gb of ram or more then you really don't need a swap partition, unless you are heavily into gaming or movie editing.

---

### Post by jvc26 on 2006-12-21
I just run a / and swap partition. I have a second drive mounted at /backup for running things onto should I need to format/make major changes which might break the system. But other than that have a fairly simplistic setup as it is.
Il

---

### Post by scrooge_74 on 2006-12-21
have / partition and swap on laptop.  My other machine has a seperate /home folder on another drive.  But that machine is for backing up my laptop

---

### Post by Azakus on 2006-12-21
I dual boot Windows and Ubuntu on my desktop (because I'm too hooked on DirectX 9 games), and I have Windows, Swap, Ubuntu(all data).
On my fileserver, I separate my OS and my Samba stuff like this:
Swap, Root, Samba files

---

### Post by adma on 2006-12-21
Thanks everyone for the replies!

I do see a pattern emerging of one single partition for / , but I'm still worried about moving all my data around whenever I need to do an upgrade or a clean install... Do you usually just install new versions of Ubuntu on top of older ones?

I guess I might give it a shot and see how it works for me! ;)

---

### Post by Drevan on 2006-12-21
for everyday use a /home and a / partition are enough for me

---

### Post by scrooge_74 on 2006-12-21
> **adma said:**
> Thanks everyone for the replies!

I do see a pattern emerging of one single partition for / , but I'm still worried about moving all my data around whenever I need to do an upgrade or a clean install... Do you usually just install new versions of Ubuntu on top of older ones?

I guess I might give it a shot and see how it works for me! ;)

If you put home in another partition then if you need to reinstall you don't have to wipe out/loose your information

---

