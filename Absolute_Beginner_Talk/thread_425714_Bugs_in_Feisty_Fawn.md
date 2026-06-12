---
title: "Bugs in Feisty Fawn"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by rogerduncan100 on 2007-04-27
I hope you (including those of you who actually write the code) will find my recent experience interesting. I will certainly try to reply to any questions anyone may have. My experience has been as follows:
I have been using Ubuntu since last September and have thought it was great! Last week I updated to Feisty Fawn from Edgy Eft and immediately had no internet access! I therefore re-loaded Edgy Eft and took all the 167 updates and installed ktorrent, which had been working perfectly for many months. Not now! It shuts off by itself after an hour or so.

Now I have just finished re-loading Edgy Eft again and ktorrent but have not taken any of the 167 available updates. It seems to me that not only does Feisty Fawn have a serious bug but so did the last of the updates for Edgy Eft. I thought of downloading all of the updates up to a week or so ago but alas, the updates are not dated.

I don't know much but it seems the Ubuntu team has rushed out version 7.04 to keep the new version every six months commitment. I think there are bugs in 7.04 AND in the most recent 6.10 updates. Any comments?

---

### Post by Najand on 2007-04-27
Unfortunately, most of developers doesn't read things here. Try to talk about it with on of Ubuntu Forum Embassadors. Or just file a bug in the bugzilla.

---

### Post by AlexDe on 2007-04-27
Have you looked at the KTorrent logs to see if theres anything interesting in there?

After it crashes try the following and see what it says:

```

tail ~/.kde/share/apps/ktorrent/log

```

---

### Post by Maxtine on 2007-04-27
rogerduncan100 unlike you I am new here, however in reading through the post one thing is becoming clear and that is that people are having real problems with the update method.
My suggestion to you is to backup your data and do a clean install

---

### Post by rogerduncan100 on 2007-04-28
I am stiill very pleased with Linux! I have indeed reloaded Edgy Eft and am running without updates. I must add that the updates worked fine until just the other day... I will log a bug report at Bugzilla. It seems that in the software world there is constant change....

---

### Post by rogerduncan100 on 2007-04-28
I checked the ktorrent logs. It says there is an authentication failure several times with different numbers. It's trying to connect but can't.

---

### Post by kittyhawk63 on 2007-04-28
```
 It seems that in the software world there is constant change....
```That is especially true in WinWorld. Change means money. It doesn't necessarily mean improvement. Vista is a great testimony for that. Feisty is very stable on my computer. I spent a week trying to get my ATI video card to work. Once I found the solution, it has shown itself worthy of being my OS of choice.
kh

---

### Post by orb9220 on 2007-04-28
There is a new version of ktorrent at the kde site that fixes the problems which were hapening to me too. It is version 2.1.4

Sorry don't have the link.

---

### Post by gijsbrecht on 2007-05-01
> **orb9220 said:**
> There is a new version of ktorrent at the kde site that fixes the problems which were hapening to me too. It is version 2.1.4

Sorry don't have the link.
The ktorrent website has ubuntu packages: [http://ktorrent.org/index.php?page=downloads](http://ktorrent.org/index.php?page=downloads)

---

### Post by rogerduncan100 on 2007-05-03
Thanks for the tip about updated ktorrent. I will give it a try if I have more trouble, but for the last week it has been fine. I just make sure I don't use DHT and I have no limits on uploading and downloading.

---

### Post by louieb on 2007-05-03
> **rogerduncan100 said:**
> I hope you (including those of you who actually write the code) will find my recent experience interesting....
Maybe someone has already reported it maybe not.  But the coders certainly are not looking at forum post to find bugs. If you want to make a difference and help get bugs fixed check  [Bugs in Ubuntu]("https://bugs.launchpad.net/ubuntu") you can report it there.

---

