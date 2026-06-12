---
title: "and encrypt Backup to FTP server"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by quaddrophonic on 2006-07-31
hi!

I'm not able to find a program to help me with this: i need to backup local files (text files) to my ftp server. They should be encrypted for security reasons you know... tried unison (did't work), keep (didn't work) and sbackup (guess what.. didn't work)

except for sbackup I don't thing any of the programms I tried can help me with that... sbackup never got files copied, but did also not give me any error message... please help...

---

### Post by jordilin on 2006-07-31
Try rsync or rdiff-backup. These apps are very powerful to perform backups.

---

### Post by quaddrophonic on 2006-07-31
Thanks, but sorry: I should have mentionned that I'm new to linux. 

As far as I understood rsync it needs to habe a rsync server programm running on the backup server ... I can't do that since it's just an ftp server ... also I didn't read anything about encryption... 

rdiff-backup seams to be easyer, I will try that :-) but still nothing with encryption...

afaik I have to encrypt it before sending it -> does that make it more complicated?

---

### Post by quaddrophonic on 2006-07-31
okay, can't use rdiff-backup, Fatal Error: Unable to create directory ftp:/username:password@fdomain.de:port/remotedir

:confused:

ps: the simleys aren't smileys in reality...

---

### Post by it.henrik on 2006-07-31
Im sorry if I missunderstood something here

but what it seems like you want to do is to encrypt text-files before ftp:ing them to a server.

gpg+ftp=problem solved

if you dont care about that high encryption then you can just use rar with password or something like that and then ftp the files where you want them :)

---

### Post by quaddrophonic on 2006-07-31
no you don't get me wrong. Thats pretty much what I want to do. encrypt and upload. But it should go automated and, if possible with a nice gui for linux newbees (hehe) like me... but I will read about that gpg encrypt thing you wrote :D

---

### Post by quaddrophonic on 2006-07-31
the new thing is: encryption seems to work... but manually uploading my files  is what I was able to do before. any way of automating it?

---

### Post by it.henrik on 2006-07-31
[http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html)

sorry for the non-gui part .. maybe you can find some nice gui for it if you search in synaptics or google

---

### Post by quaddrophonic on 2006-08-01
at the end it doesn't really matter if it has a gui.;-)  The important thing is that it works. And doing it with cron should do it, (if I will ever get that running :p )

 THANKS

---

