---
title: "Basic Linux Questions"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by csaunier on 2008-04-09
Seeing how most of us newbees got here by fleeing windows, I have a few real basic questions.  First, are viruses something to be concerned with in linux systems?  I just assumed that was a windows problem, but what are the facts?  Next, what about such disk maintenance tasks as defraging.  Is there any linux equivalent or isn't it necessary?

---

### Post by y-lee on 2008-04-09
No real virus threats and usually no need to defrag. Search the forums here for more info. lots of people ask that.

---

### Post by lackofcreativity on 2008-04-09
First, viruses. You know how you have to put your password in every time you want to do something that changes the system files? A virus would have to find your password. As long as you don't enter your password into every window that pops up, it's safe. Linux uses a security protocol to encrypt its passwords that, as of now, hasn't been cracked. Now for the defragging. Say your hard drive looks like this:
```

0 0 0 0 0 0 0 0 0 0
0 0 0 0 0 0 0 0 0 0
0 0 0 0 0 0 0 0 0 0
0 0 0 0 0 0 0 0 0 0

```
Obviously this is very small, but it's for demonstrative purposes only. Now. If your were using a FAT or NTFS partition, which is what Windows uses, files are saved close together, like this:
```

F I L E 0 0 0 F I L
E 0 0 0 0 F I L E 0
0 0 0 0 0 0 0 0 0 0
0 0 0 0 0 0 0 0 0 0

```
If you make any one of those files bigger, just a little, it has to be split up. One part goes in the first place, the other, newer part is written near the last file on the drive. This is what causes fragmentation. Ubuntu uses the ext3 file system, which saves things like this:
```

F I L E 0 0 0 0 0 0
F I L E 0 0 0 0 0 0
0 0 0 0 0 0 0 0 0 0
F I L E 0 0 0 0 0 0

```
So if you change each file a little, it's still all in one piece. Eventually fragmentation might come into play, but only if your hard drive actually *is* this small ;)
So really, none of that is a problem now that you have seen the light :KS.

---

### Post by gsmanners on 2008-04-09
The threat of viruses is mostly countered by the fact that nearly every application comes from a repository. Official package maintainers are authenticated, so if a piece of malware does appear in the repo, we know exactly who's to blame.

---

### Post by unutbu on 2008-04-09
Welcome to Ubuntu, csaunier! For an introduction to security under Ubuntu, check these out:

[http://ubuntuforums.org/showthread.php?t=694198](http://ubuntuforums.org/showthread.php?t=694198)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

However, may I make a suggestion? After you read enough to achieve a basic understanding of security, don't worry about security too much. Worry about making good backups regularly.

If you are like most users, you'll want to download some software from unofficial sources. Doing so compromises your system. Not doing so compromises the reason you bought a computer.

I'd rather have great backups than great security. Backups will help you in many situations which arise more often than getting hacked: such as hardware failure, borked MBR/GRUB after repartitioning or installing/uninstalling OS's. (Actually, there is usually a way to fix grub problems without backups, but backups are a good safety net anyway.)

Understanding security at an advanced level is time consuming and quite technical. The marginal return on investment of time and effort gets quite small for normal Ubuntu users running behind a router. On the other hand, everyone can learn how to make backups quite easily. That's a much better return for your time and effort.

---

### Post by csaunier on 2008-04-19
Back again after enjoying a few days of great weather!  Thank you all for your answers.  I now have a better understanding of Ubuntu.

---

