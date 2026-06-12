---
title: "questions about crontab"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by Nebel on 2007-03-07
i need to run some script daily. And so I
 
$crontab -e
and entered this line(every hour,minute)

* * * * * echo "hello"

but nothing comes out :confused: 
what is wrong here?

---

### Post by mattmole on 2007-03-07
Hi, 

I presume it is because cron doesn't know where to echo to. Try 

* * * * * echo "hello" >> /home/USERNAME/crontest.txt

That way, everytime it runs it will append hello to the end of the file.

Matt

---

### Post by Nebel on 2007-03-07
I typed as i was said, but nothing happened with the file crontest.txt. I even created an empty file with that name ir specified directory.

---

### Post by Bachstelze on 2007-03-07
Weird, it works fine here... Make sure you didn't do a typo in the file path ;) You might also want to use ~ instead of /home/username

---

### Post by Nebel on 2007-03-08
i have entry when crontab -l (copypasted) : 
** * * * * echo "blet" >> /home/virgius/crontest.txt*
i cant see any mistake here.

I also tried this:
made file with entry 
[I]#!/bin/bash
tcpdump -c 10 arp|grep arp > a_txt[/I]
and placed this file in /etc/cron.hourly
but this doesnt work too. When executing this script works fine.

---

### Post by Mr. C. on 2007-03-08
Cron's output does not go to your terminal.  It would clutter your terminal as you worked, if it did.  It is delivered via mail.  Type:

mail

and you will see a mailbox full of your output (q quits).

The system crontab (root's) requires a username after the time specifications.  What username are you when you run crontab -e ?

MrC

---

### Post by Nebel on 2007-03-08
I'm working as root.

I changed line to:
* * * * * root echo "halo" >> /home/virgius/crontest

still no news ir dir /home/virgius/

---

### Post by Nebel on 2007-03-08
partially solved my problem running script hourly by copying script file to /etc/cron.hourly

#!/bin/bash
tcpdump -c 10 arp|grep arp > /home/virgius/arp_hourly&

thats ok
thanks for all :)

---

### Post by Mr. C. on 2007-03-08
> **Nebel said:**
> I'm working as root.

I changed line to:
* * * * * root echo "halo" >> /home/virgius/crontest

still no news ir dir /home/virgius/

Did you edit /etc/crontab manually with an editor, or invoke it via crontab -e ?

If you did the former, you need to either reload the cron service (or send cron a signal).

/etc/init.d/cron restart

MrC

---

