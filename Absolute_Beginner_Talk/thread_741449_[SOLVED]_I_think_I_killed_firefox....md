---
title: "[SOLVED] I think I killed firefox..."
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by joethesupercow on 2008-03-31
I'm recently running Ubuntu 7.10 and haven't had a problem up until now. 

I'd installed dansguardian, firehol, and tinyproxy through synaptic but had trouble getting them configured. I then did a full uninstall of each of these programs (including config files) from synaptic. Firefox stopped working right afterwards. It still launches but can't reach any page. Originally pidgin and other programs still worked, but after a restart these have failed to.

I've tried a quick reinstall of firefox but it didn't seem to help

Any help is appreciated!

---

### Post by abhiroopb on 2008-03-31
ok could you give some more information please:

1. What do these programs do exactly?
2. When you say full uninstall did you use the --purge command?
3. Am I correct in assuming that firefox opens, you get a blank/grey page and then it doesn't go to any page?
4. Which other programs have failed? - is it a major system wide problem or is it simply your internet related programs?

I think what may have happened is that there were common config files or something strange like that. Usually you don't want to do a complete uninstall (including config files). There isn't any real reason to do so.

---

### Post by y-lee on 2008-03-31
abhiroopb i don't really know how to help but joethesupercow has most likely messed up his firewall.

---

### Post by abhiroopb on 2008-03-31
y-lee, initially that was my thought but it is unclear what "other programs have failed to" means. So if it is all internet related its most likely some config issue with the firewall. I guess easiest thing to try would be to just re-install all the applications see if it works. If not install Lokkit to re-configure your firewall (its a simple GUI tool).

---

### Post by joethesupercow on 2008-03-31
hey sorry, Ya, I mean other internet related programs aren't working now. When I try to reach a site in firefox I get a Problem loading page screen, you know, the ones with the yellow exclamation marks.

I used this guide to setup dansguardian so you can see all the .conf files I modified [http://ubuntuforums.org/showthread.php?t=207008](http://ubuntuforums.org/showthread.php?t=207008)

as far as the other questions go...

1. Dansguardian is an internet content filter. Firehol is a firewall application, and tinyproxy is a HTTP proxy server daemon for POSIX operating systems (definition courtesy of wikipedia).

2. I did the full uninstall from synaptic. Just clicked the programs and used the "full uninstall (including config files)" option.

3. Hope I clarified the firefox thing. It opens, just has a problem loading any pages.

4. It's not a system wide problem, just programs that connect to the internet.

Oddly enough the last I checked, I could still ping google.

I agree that I must have inadvertently modified or deleted common internet files. Not a chance there's some kind of system restore is there? :)

---

### Post by joethesupercow on 2008-04-01
Well it appears that the internet... well... started working again! solved I guess? I'll keep you updated...

---

### Post by abhiroopb on 2008-04-01
Good thing it works, just be careful with config files. Always safer to just leave them unless there is a specific reason you want to uninstall them.

---

