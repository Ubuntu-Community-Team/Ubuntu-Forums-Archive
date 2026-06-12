---
title: "no disk space"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by lex1 on 2007-08-17
i have got unbuntu on 13 gigs of heard drive the download sofwate has downloded a file while processing the diffrent parts it has an error message not enough on disk? the file size is 4.7gigs this is a frsh install
I found out that at the moment there is 6gigs free


lex1

---

### Post by Cypher on 2007-08-17
Open a terminal and show us the output of the following commands
```

sudo fdisk -l
mount
df -h

```

---

### Post by mikeyphi on 2007-08-17
When you open your 'Home' folder - How much free space is listed in the bottom left corner?
If this shows no/little free space - use the Gnome partition editor to confirm that you have the expected 13gigs actually available.

---

