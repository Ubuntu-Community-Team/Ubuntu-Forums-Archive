---
title: "Lost mldonkey files"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Soulthiefuk2000 on 2007-08-30
Hi All,

    I've installed mldonkey using apt-get and it seems to be working OK but I can't seem to find the files it downloads. From what I've read it seems that they should be in $HOME/.mldonkey/incoming/files but the incoming directory doesn't exist. I assume that the directory to store the files in is specified in the downloads.ini file but that doesn't seem to exist anywhere either.

Help anyone ?

Thanks,

    Jon.

---

### Post by felicity on 2007-08-30
I don't use mldonkey but you can try

```
sudo updatedb
```

then

```
locate mldonkey
```

to try and find out where related files may be and infer which ones you're looking for from the output. If that doesn't show anything, try 

```
locate filename
```

where filename is the name of a file you've downloaded.

---

### Post by Soulthiefuk2000 on 2007-08-30
Hi Felicity,

    Thanks, that got it (updatedb and then locate mldonkey). They're in /var/lib/mldonkey/incoming files. I've found the ini files too now (/var/lib/mldonkey).

Thanks again,

    Jon

---

