---
title: "SETUID on AVScan"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by girard on 2007-07-17
Hi. I tried looking into the forums but did not find anything that gave a specific answer.... so probably this very trivial, I dunno really.

I cannot update my ClamAV via AVScan. it says that I don't own it or something. Has something to do with SETUID. I tried mixing up the command frm gksudo, gksu, sudo avscan, but it seems avscan is all that would work for the shortcut button.

so how do I update AVScan?

EDIT:
here's the prompt I get. 


[IMG]http://www4.webng.com/girard/screenshot-virus%20database%20update%20warning.png[/IMG]

---

### Post by girard on 2007-07-19
no replies yet.. hmmm... am i the only one having this kind of problem?

did my own googling, but i haven't found an answer. can anyone at least point me towards the right direction?

thanks.

---

### Post by girard on 2007-07-19
ok... i did this 

```
chmod 0711 /usr/bin/freshclam
```

but that window still appears whenever I try to test the update.

---

### Post by PaulFr on 2007-07-19
You need (a) freshclam to be owned by clamav user, and (b) freshclam to be setuid to that user. So, ```
sudo chown clamav /usr/bin/freshclam
sudo chmod u=rws,go=rx /usr/bin/freshclam
``` should work. Since freshclam is usually run by root, it does not need setuid rights.

---

