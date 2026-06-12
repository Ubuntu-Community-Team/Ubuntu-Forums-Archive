---
title: "&quot;wget -c&quot; Question"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-31
Whenever the wiki suggests to use the command "wget -c", for example in the restricted formats page: ```
wget -c ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.4_i386.deb 
``` where does that deb get saved?  Just wondering...

---

### Post by rooreleased on 2006-05-31
It gets saved in whatever directory you're in.

---

### Post by user1397 on 2006-05-31
Ah! Well that explains it.  I guess it basically always gets saved in my home folder then, since that's the folder you're in when u open the terminal.  Thanks for the info!

---

### Post by linuchsan on 2006-05-31
you can use the -P option
wget -P ~/ ftp.whatever....

---

### Post by user1397 on 2006-05-31
[quote=linuchsan]you can use the -P option
wget -P ~/ ftp.whatever....[/quote]For what use?

---

### Post by linuchsan on 2006-05-31
Your downloads go to you home dir.

---

