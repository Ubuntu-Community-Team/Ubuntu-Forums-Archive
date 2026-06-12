---
title: "what does /var/cache/debconf/config.dat contain?"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by ronly on 2006-04-20
I did something very stupid so once you stop laughing you can hopefully tell me how important /var/cache/debconf/config.dat is since I deleted it - apt-get said that it was locked by another process and I knew that I had recently killed dpkg-reconfigure and thought that it was just a lock file (I typed rm and cut'n pasted the filename in konsole without thinking...). So I'd like to know how important that file is? Did it contain something crucial that will only become apparent when I upgrade some packages? I haven't noticed anything yet but since I have only spent 5-6 hours on configuring my system I'd rather start from scratch now than have some (probably hard to figure out) difficulties in the future. Thanks in advance!

---

### Post by htinn on 2006-04-20
I'm not sure, but I think most everything in /var/cache is expendable. I'm not saying it's okay to delete it, but it might not actually do anything bad (other than make you wait while it gets rebuilt at some point).

---

### Post by meborc on 2006-04-20
[QUOTE=ronly]... apt-get said that it was locked by another process ...[/QUOTE]
apt-get says that when synaptic is open... since synaptic is a gui of apt-get you can only use one or the other at the same time... so... the Q is, were you using both at the same time? if so, there is no problem... just close one, update and continue with your work... if not, then i don't know :)

---

