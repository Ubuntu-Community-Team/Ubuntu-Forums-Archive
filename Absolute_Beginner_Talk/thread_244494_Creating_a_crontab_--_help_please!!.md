---
title: "Creating a crontab -- help please!!"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by p.i.m.p on 2006-08-26
hi... i have a dsl connection that i leave on to download at night.. however my line quality is very bad and i am planning to have someone check it for me.. in the meantime i have put the following lines in my crontab to dial the  connection on the first minute of every hour.. basically to disconnect and dial again so in case the connection is dropped it will redial in an hour.. will the following lines do the trick? am i making any mistake? help please!! :)

my crontab:- 

# m h  dom mon dow   command
1 * * * * poff dsl-provider
1 * * * * pon dsl-provider

---

### Post by derred on 2006-08-26
I use gnome-schedule becase it's easier(for me at least) to fix my errors in a GUI, so I can only recomend you try the same. 
If you use are using Kubuntu there are KAlarm and KCron as frontends to the at and/or cron commands.
Hope this helps.:D

---

### Post by true_friend on 2006-08-26
same the suggession of mine.

---

### Post by p.i.m.p on 2006-08-26
thanks for the replies! im gonna check whether my crontab entry works and if it doesnt im gonna use the gui.. peace out

---

### Post by steve.horsley on 2006-08-26
I think this will be unreliable. You are launching both poff and pon at the same time. I would suggest launching a single script that goes something like this:
> #!/bin/sh
poff dsl-provider
sleep 3
pon dsl-provider

---

### Post by p.i.m.p on 2006-08-26
hey thanks a lot that didnt occur to me :rolleyes: other than that is the crontab file allrite? i mean it should launch after each hour right? thanks!

---

