---
title: "Password changed itself - weird problem!"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Kristian9K on 2006-09-03
Hi,
After a system crash while running Automatic Update I no longer have access to administrative tasks from the graphical interface. I can, however still do these things from terminal.

Here's what I get when trying to use Synaptic or Update Manager:
"Enter the administrative password"
-OK, I do....
then "Error when running /usr/bin/update-manager as user root: Wrong password"

Can anybody help?

Kristian

PS: I'm on Ubuntu 6.06

---

### Post by Klaidas on 2006-09-03
Maybe CAPS LOCK is on? :)

---

### Post by whizbaby on 2006-09-03
> **Kristian9K said:**
> Hi,
system crash while running Automatic Update

What happened (*system crash* is not so detailed, look in /var/log/syslog* ('*' as a wildcard))?
Did you do 
[b]sudo apt-get update
sudo apt-get upgrade[/b]
after it?

Do **sudo synaptic** in a terminal. What is the error message(s)?

---

### Post by Kristian9K on 2006-09-03
Hi,
Thanks for all these responses. 

Of the syslog files, this seems to be the newest:
Sep  3 11:39:36 kristian-desktop syslogd 1.4.1#17ubuntu7: restart.
Sep  3 11:39:36 kristian-desktop anacron[4567]: Job `cron.daily' terminated
Sep  3 11:39:36 kristian-desktop anacron[4567]: Normal exit (1 job run)
Sep  3 11:59:39 kristian-desktop -- MARK --
Sep  3 12:17:01 kristian-desktop /USR/SBIN/CRON[6361]: (root) CMD (   run-parts --report /etc/cron.hourly)

----does that clarify anything??

Is it safe to run:
sudo apt-get upgrade ?
I would really hate to mess up my system again - I feel like I'm experiencing Murphy's Law with this thing and have already reinstalled ten times or so!

When running:
sudo synaptic
I DO get an error message, but it's in danish so I doubt it will be of any help ("Lagersegmentfejl")... I can tell you that synaptic opens very shortly, then closes.

Kristian

---

### Post by whizbaby on 2006-09-03
In the syslog's you are supposed to track down the 'system crash'.

Actually it is safe to apt-get upgrade, this will finish (or danish, in your case:wink: ) the tasks stopped with the crash.

I don't speak danish but if my feeling for language doesn't fool me

'fejl' means error
('lager' perhaps similar to the german 'Lager' -- storage)

So you have a 'segmentation fault'. How old is your hard drive, older than two years? (I had synaptic starting to crash four weeks before my drive was gone (R.I.P.) in breezy)

---

### Post by &#12465;&#12452;&#12488; on 2006-09-03
How about running synaptic from a terminal? Could be gksu that's messing around, because I've got exactly the same problem now, after upgrading to edgy (though that's not exactly unexpected, alright).

---

### Post by Kristian9K on 2006-09-03
whizbaby, I'm impressed - "segmentation fault/error" makes sense. My HD is about four(!) years old and may soon have had its time... 

"In the syslog's you are supposed to track down the 'system crash'"
--- My syslog from the time of the crash should be attached - would somebody look at it as I have no idea what to look for myself?

apt-get upgrade gives me "segmentation error" message... :( 

Thanks, Kristian

---

### Post by Kristian9K on 2006-09-03
Sorry, here's the syslog file, zipped

---

### Post by whizbaby on 2006-09-03
Your hard drive doesn't have much time left ... (I believe the crash occured because of this, my machine started crashing wthout reason, too)

I assume you started synaptic from the menu and that this then happens

password asking - getting
program starts and fails immediately
gksu (or similar password-asker) reports 'wrong password'

(that actually doesn't mean that you have a password problem, only that a tool has only this error message for dealing with program-crash)


What was the exact time/date of the crash, and can you post your /var/log/messages covering this point in time?

---

### Post by Kristian9K on 2006-09-03
Yes, that's what happens with synaptic, but it doesn't seem to open at all.

Attached is what should be the log from the crash. Not entirely sure as I've had so many problems that their cronology tends to go into a blur...

How do I further diagnose my HD?

Thanks,
Kristian

PS: Upon installing Ubuntu I had major problems with my graphics card during the first many installs, but then they suddenly disappeared with install no. god-knows-what. Could this be related to a bad HD?

---

### Post by whizbaby on 2006-09-03
The only nasty thing in there I can see is:
Aug 31 21:36:06 kristian-desktop kernel: [4296825.141000] kernel BUG at mm/rmap.c:486!
Aug 31 21:36:06 kristian-desktop kernel: [4296825.141000] invalid operand: 0000 [#1]

cannot say anything about it spontaneously...
What is with the /var/log/messages of that time?

To your hard drive:
DON'T run any analysis tools or anything on it! 
FIRST thing to do is buy a new HD and save all your data. Until starting to save you should consider not even turning it on (if it's over it's over, then it will cos a LOT of money to get your data back)
Then you may analyse (not expecting to much of it, though)
(p.s. hardware problems can always lead to strange system-behaviour)

---

### Post by Kristian9K on 2006-09-03
These are my "messages" files. messages.0 is from thursday (perhaps the crash was there), the other is from today...

As for my HD, there isn't really much data to waste as I formatted it during install a few days ago. I remember being able to isolate bad sectors - can this still be done? That would be a fine solution til I get a new HD...

---

### Post by xhaan on 2006-09-03
Sorry to get off topic but..
Do hard drives really die that fast??
The one I'm using now is about 6 years old, and the one in my Debian box is probably around 8! 

Now you've got me worried that my drives will suddenly explode one day. 
The only problems I've had with hard drives were one catastrophic mechanical failure on a relatively new drive, and the first drive I bought to replace it was DOA, same brand. I exchanged it for a Maxtor drive and have used that drive ever since...

---

### Post by whizbaby on 2006-09-03
I can't find anything new in the logs (meanwhile, messages is a part of syslog, I forgot). 
A little HD talk:
'bad sectors': your HD (simplyfied) looks like this:
(---------place-for-you--------------)(--sector recovery---)
 if in place-for-you your harddrive encounters problems, it will mark this sector and link it to the HD recovery space, so your HD will not lose size for a while
(-------------R1------------R2-----)(-R1--R2---)
the day comes the extra space is used up
(--------------RRRRRRRRRRR---------)(RRRRRRRRRR)
and broken sectors cannot be linked away anymore. From that day on you HD will shrink with every broken sector. If you mark bad sectors manually ,you will get new ones and your HD-size is going away until hardware-error.

The lifetime of a HD depends on a lot of factors, basically hardware quality (you'll notice with the price mostly), temperature conditions, size,frequence of use, kind of use and a few rarely-important.
I too got a drive that is about 11 years old and still working, but this one is only 6GB and I use that computer mostly as a TV-replacement.
I also got access to more than 400 clients which are running 24 hours a day, and there I rarely see drives significantly older than the expire date of the warranty (two years). Even the drives I use at home (not 24/24) don't have much more lifetime (usually between two and three years).
A drive which is turned on for many years 24 hours a day can get broken by just shutting down the computer.
If you need data safety buy two HDs and use one ONLY for backup/syncing.
(seen enough people losing all their stuff in nearly frequent intervals)

---

### Post by Kristian9K on 2006-09-04
My next step will be checking my hard drive for errors. I'll see if I can find out how and start a new thread if not. Thanks to everyone who's read and posted here, especially whizbaby.

Kristian

---

### Post by TomG on 2006-09-04
Got such kind of problem today. Synaptic started to refuse my pwd then I decided to reboot. I was close to a heart attack when GDM login also refused my pwd... Fortunately root login on recovery session allowed me to change it... to his normal value ! 
I'm currently backing up everything... :)

---

