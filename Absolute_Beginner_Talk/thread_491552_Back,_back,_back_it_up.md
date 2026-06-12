---
title: "Back, back, back it up?"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Protagonistics on 2007-07-03
I used to use Mozy Backup for Windows. Alas, it has not made the trip to Linux. What kind of remote backups are available for a user like me at home with no extra hard drives or routers linking him to his college network?

Are there any apps that can link to those commercial backup sites like mozy?

And no, I'm not going to use that Gmail backup thing. I have too many weird file extensions it doesn't like.

THanks.

---

### Post by Nekiruhs on 2007-07-03
PartImage is great. I used it until I bought TrueImage (I dual boot, so I use it in windows).

---

### Post by hyper_ch on 2007-07-04
Hmmm, I do backups to my second computer and to a third computer at my parents' place... that can easily be achieved... however with mozy - how do they transfer the files?

---

### Post by qpieus on 2007-07-04
If you want a gui, check out unison. I think it'll do what you are looking for.

[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)
[http://freshmeat.net/projects/unison/](http://freshmeat.net/projects/unison/)

If you want a command line solution you can use ssh and rsync together to provide an encrypted sync between your pc and the uni server. Google or search these forums for "ssh rsync" and you'll find tons of info/guides. I like the ssh/rsync method because I can put the commands to do the backup into a script and use cron to automatically execute the script t do the backup. It's a no-brainer, I don't even think about my backups anymore, they just happen.

Another gui option could be grsync:

[http://ubuntuforums.org/showthread.php?t=489216&highlight=ssh+rsync](http://ubuntuforums.org/showthread.php?t=489216&highlight=ssh+rsync)

---

### Post by onestep on 2007-07-27
> **Protagonistics said:**
> I used to use Mozy Backup for Windows. Alas, it has not made the trip to Linux. What kind of remote backups are available for a user like me at home 

I too used Mozy for Windows and was looking for the same solution as you. What I found that works well is Jungle Disk. It was easy for this nOOb to set up and configure. It works like Mozy but uses secure servers at Amazon .com for encrypted storage. The down side is that its a paid service... but it's dirt cheap. All you pay for is what you actually use;
[LIST]
[*]$0.15 per gigabyte-month of storage used
[*]$0.10/0.18 per gigabyte of data uploaded/downloaded.
[*]$0.01 per 1,000 upload or 10,000 download requests[/LIST]So far  my monthly bill is $0.37 :)

Onestep

---

