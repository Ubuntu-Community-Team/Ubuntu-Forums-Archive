---
title: "Unnecesary files"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by nebu on 2008-02-11
i have a crunch on my comps hdd space evr since my 160gig external hdd stopped workin......

is there a way i can free space like in windows by removing temp files.... temp internet files..... defrag etc on my primary hdd???

---

### Post by jan quark on 2008-02-11
I would only suggest
```

sudo apt-get autoremove
```

---

### Post by hyper_ch on 2008-02-11
defrag does not free space - and it's not needed in linux filesystems

you could clean the downloaded files from the repositories... that should free some space...

temp itnernet files --> alter the settings of the browser you use... I think default in firefox is 5mb (not sure)

and other temp files are to be found in /temp --> have a look in there.

---

### Post by hyperair on 2008-02-11
To purge the no longer needed debs from /var/cache/apt/archives, 
```
sudo apt-get autoclean
```

or if you want to purge all:
```
sudo apt-get clean
```

---

