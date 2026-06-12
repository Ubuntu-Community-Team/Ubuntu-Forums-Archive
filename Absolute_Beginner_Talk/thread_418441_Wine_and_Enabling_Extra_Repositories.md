---
title: "Wine and Enabling Extra Repositories"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Carwyn on 2007-04-22
Running Feisty and I've been using this guide here to try and get Wine running, it said I needed some extra repositories first and that I should do what it says here:

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

So I do that, follow it to the letter, and get this;

[PHP]carwyn@Yuri:~$ sudo aptitude update
Segmentation fault (core dumped)
[/PHP]

So then I try and do what it says to trouble shoot, but I end up having to "sudo aptitude update" again and get exactly the same message as before, "(core dump)".

I'm a complete noob at Linux (like 99%) so any help would be great.

---

### Post by SOULRiDER on 2007-04-22
You must ahve screwed up your sources list. If you have a backup try recovering it. If you dont have one, you can use the source'o matic to create a list from scratch.

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by Carwyn on 2007-04-22
If I had a back up where could i find it?

And what do i do with this 'source-o-matic' thing? I got a big chunk of text at the end, where do i put it?

---

### Post by SOULRiDER on 2007-04-22
If you have a backup you would know.

What source'o matic creates is a new sources list. What you have to do is edit your sources.list file and replace everything with what source'o matic made.

For Ubuntu:
```
gksu gedit /etc/apt/sources.list
```

For Kubuntu:
```
kdesu kate /etc/apt/sources.list
```

After you replace all the text, just run these two commands:
```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by Seisen on 2007-04-22
Post your source list and maybe we can clean it up for you to get it to work.

---

### Post by Carwyn on 2007-04-22
I've done what you've said SOULRiDER, replaced the sources list with the one source-o-matic created for me, but when it comes time to:

carwyn@Yuri:~$ sudo aptitude update
Segmentation fault (core dumped)

This still happens.

I'm not sure if something went wrong somewhere else. This all happened as a result of the tutorial posted in the first link. Then trying to "Troubleshoot" it, then trying to do it again. I also sudo apt-get update" once.

---

