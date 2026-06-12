---
title: "my anti-virus has picked up a virus......"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-06-18
hello.
im using fiesty and im running avg as an anti virus.
ive set avg up to do a scheduled test everyday, but for the last 3 days its said its found a virus, but when ive scanned the system manually it doesnt find anything, im presuming its because avg has already cleaned the infected file/files
does anybody know where avg keeps the virus vault under linux ? ive looked for it and im stuffed if i can find it, the reason i want to find it is because it may give me information as to where the virus came from, or which files it infected first, the the results dont give me any information at all, it just says it found a virus.
cheers in advanced for any help.
cheers

---

### Post by v8YKxgHe on 2007-06-18
Do you have a Windows partition anywhere? It may be scanning that partition as well, and picking up any viruses on that.

Also, how come your running AVG on Linux to start with?

---

### Post by techno-mole on 2007-06-18
i dont have a windows partition as such, i have a second sata drive with xp on it, avg isnt scanning it though, i think it may be something to do with the scheduler settings, if i start avg manually (from the launcher i created) i have to put my password in, but if avg is set to scan at a set time im presuming it'll do it on its own, but maybe the virus event is caused by it trying to access a restricted set of files or some such.
i dont get the virus event if i run a manual scan, so maybe its a permissions thing ?
as for running avg on linux (the avg version for linux, not through wine etc) i know technically i dont need an anti-virus of firewall, but this machine is networked with 2 other pc's both of which are running xp, so im just making sure nothing nasty comes over the network.
cheers

---

### Post by Chayak on 2007-06-18
The only reason I have AV on my linux box is because that's the machine I download everything with and the files get scrubbed before they go to my windows machine.

There is the question of exactly what virus it's picking up?  If it's a windows virus which it most likely is then don't worry about it.   It's not going to magically come to life and eat your machine.  Though I did read an article a while back on someone using wine to try and run windows virii and apparently hardly any of them ran, or did anything if they did run.

---

### Post by Regel on 2007-06-18
Do you mean this article?
[http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

---

### Post by dannyboy79 on 2007-06-18
> **techno-mole said:**
> hello.
im using fiesty and im running avg as an anti virus.
ive set avg up to do a scheduled test everyday, but for the last 3 days its said its found a virus, but when ive scanned the system manually it doesnt find anything, im presuming its because avg has already cleaned the infected file/files
does anybody know where avg keeps the virus vault under linux ? ive looked for it and im stuffed if i can find it, the reason i want to find it is because it may give me information as to where the virus came from, or which files it infected first, the the results dont give me any information at all, it just says it found a virus.
cheers in advanced for any help.
cheers

have you checked out /var/log/syslog? almost everything is logged there. or do a search for anything with avg in it? I can't believe that it would tell you it found a virus and then not tell you anything about it, doesn't make any sense. also, I don't know how it's being run, but if it's NOT setuid as root, and you get dfferent results when running it as sudo, than I am guessing that's a problem. have you read the AVG forums?

---

### Post by techno-mole on 2007-06-18
ive done a search for all things avg, and turned up nothing, i checked the system logs aswell nothing there either.
but looking at the times of the scans they are all at times when i havent started avg, which means that if its tried to do things its done them with out the password being entered (which it needs to run properly) so with that in mind it must be permissions that have thrown up the error, eg - if it cant access some files it my consider them to be hostile, not knowing how viruses work im presuming that if its found locked files it my consider them viruses ?
ill have alook on the avg forums though as it may give me some pointers as to how to let it have the right permissions.
cheers

---

### Post by techno-mole on 2007-06-18
its a permissions thing.
and on another note - ive downloaded the latest avg free editon and installed it from the .deb file, i had to create a launcher as one didnt appear, this was easy enough.
go to --> system --> preferences --> main menu --> new item --> and in the box that opens (launcher properties) type in the "name" field "avg anti virus" (or what ever you want) in the command field type sudo avggui and then you can choose an icon, theres an avg one in pixmaps and type what ever comment you want and that should be that.
when you click on the icon you created it should also let you update with out any trouble aswell.
this may not seem very useful to some people but for a while ive been using an older version of avg because i couldnt get the latest to run.
cheers.

---

