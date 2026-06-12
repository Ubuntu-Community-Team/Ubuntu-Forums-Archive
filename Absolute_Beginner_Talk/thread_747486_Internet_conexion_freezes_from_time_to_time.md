---
title: "Internet conexion freezes from time to time"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by Saardox on 2008-04-06
Hello again and thanks for all the help provided. After reading like hell, I'm finally working my way through Ubuntu/Linux :guitar: Still, there is on more thing I cant figure out:Internet (only in browser) keeps freezing from time to time and just wont connect to other sites. It stays like that for about 30 secs,  then starts working again normaly. Whats funny is that I can chat with aMsn while the browser connection is down. 

Firefox (latest version)
Dell XPS M1210

Thanks for the help
-Saardox

---

### Post by InfinityCircuit on 2008-04-06
Have you tried disabling ipv6?

Go to about:config and search for ipv6 and disable it.  Then go to /etc/modprobe.d/aliases and change the line from:

alias net-pf-10 ipv6

to:

alias net-pf-10 ipv6 off
alias net-pf-10 off

---

### Post by Saardox on 2008-04-06
My most sincere thanks. Fixed the problem instantly!=D>

---

### Post by Saardox on 2008-04-09
Hello again...
     It seems that the problem wasn't completely fixed. I can browse normally for about an hour, after an hour it doesn't make connections with new servers. For example, it can keep downloading a torrent but It would not ping Google. Amsn and limewire still work.

Thanks
-Saardox

---

### Post by Saardox on 2008-04-10
Is there any command I can write in the terminal to see whats going on?

---

