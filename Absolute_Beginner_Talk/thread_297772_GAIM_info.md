---
title: "GAIM info"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by Hranj on 2006-11-11
i know in windows there is an area where gaim and aim keeps your info which is an HTML file. just curious where that is in ubuntu. thanks.

---

### Post by ner0tic on 2006-11-11
in gaim 2.0 it's found in /home/<username>/.gaim/accounts.xml

scan through and you'll find <userinfo></userinfo> with your profile in side the tags.

---

### Post by strabes on 2006-11-11
All your user-customized stuff like preferences etc is in ~/.gaim/ which is a hidden directory in your home directory. Press ctrl + H inside nautilus to see hidden files.

Your aim profile that others can see is located in ~/.gaim/accounts.xml if that's what you mean by info

---

