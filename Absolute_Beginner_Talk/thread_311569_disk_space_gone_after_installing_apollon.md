---
title: "disk space gone after installing apollon"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by karellen on 2006-12-03
hi everybody. I'm running ubuntu dapper drake for a month or so and works just fine, but today I installed apollon and when I launched it from the console it asked me if I wanted to make a share dir or something like that, I selected my usual download folder and suddenly or my free space is gone (1.7 giga)...I was very pissed of, uninstalled apollon, run sudo-apt autoclean and purge and other stuff but still I have no idea where all that disk space went. I'd be very thanksfull if somebody could help me, give me a hint, anything. It's a very annoying situatin, damn apollon...

---

### Post by sardion on 2006-12-03
Even after removing and autocleaning the disk space is still gone?

In terminal, cd to your "usual downloads folder" and do a 

du -sh .

that will tell you how much space that dir is using.  if it is big (like there are your 1.7G) then do

ls -alh

and see if there are hidden files (starting with .) that have the space.  the -alh means a=all files   l=list details    h=human readable form

also, in your home directory, do

ls -a

and look for something like .apollon
i don't use apollon at all but it may have such a thing
cd into that and look around and see if that has your space

---

### Post by karellen on 2006-12-03
thanks for the advice. anyway, I did it something else. I deleted from /home the hidden .gift directory(it contained a lot of stuff from /home indexed and stored there for I-have-no-idea reason)...Now my free space is back again :)

---

