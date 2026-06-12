---
title: "help... something happened."
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by obey43 on 2006-03-13
so the past couple days my wireless was very patchy because i was at my sisters where i could barely read her wireless, and thus websites would barely load.  i tried to use synatic while doing this and updated the repositories and it made it so i had no repositories.

now i am at a good wireless connection back home, but now certain websites won't load, for example google and another messageboard won't load. XIRC won't connect either, and the biggest deal, synaptic can't connect to the repositories even though i am completely on the internet, is ther something blocking places i tried to go while i was at my sisters??  i really would like to fix this.
please help

---

### Post by obey43 on 2006-03-13
i can also ping all these sites and get <60 m.s back

---

### Post by obey43 on 2006-03-13
it seems like it has a really hard time looking up adresses, but once it's looked up, it works? if that makes sense...

actually, it seems that if i ping it in the terminal, it will work, but unless it ping, it won't.

any ideas what would cause that?

---

### Post by Iowan on 2006-03-13
DNS server address got messed up?

---

### Post by obey43 on 2006-03-13
how would i look/fix that?

---

### Post by Iowan on 2006-03-13
I searched around my system, but found no files containing DNS server address.  Finally, I decided to look under System>Administration>Networking.  There's a tab for DNS and the Connections tab has a setting for Default gateway device.  I'm hardwired, so if wireless is different, all bets are off...

---

### Post by nalmeth on 2006-03-13
> repositories and it made it so i had no repositories.

in terminal:
sudo gedit /etc/apt/sources.list

is this file empty?? i picked this out of your post, and seems very weird, just want to confirm this is the case

---

### Post by obey43 on 2006-03-13
no i figured out my problem on xirc.

the problem was that my computer was using an old wi-fi connections DNS instead of the current one.

thanks though for your help

---

### Post by towsonu2003 on 2006-03-13
DNS servers go into /etc/resolv.conf as ```
nameserver 136.160.xxx.xxx
nameserver 136.160.xxx.xxx
search xxxx.xx.comcast.net.

```
but i don't know where to find a dns server. mine get written automatically as I connect using wvdial (dial up - modem). google should help...

---

