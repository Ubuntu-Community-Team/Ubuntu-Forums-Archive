---
title: "sudo command to empty trash ?"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2007-01-03
i was wondering if there was a sudo command to empty the trash can..

i have 1 file (breezy 5.10 iso) that i apparently do not own so i cant delete it from my trash can...:-k 

     thanks

---

### Post by taurus on 2007-01-03
Applications -> Accessories -> Terminal
```
sudo rm **filename**
```

---

### Post by MkfIbK7a on 2007-01-03
do 
gksudo nautalis /home/<yourname>/.Trash
delete from there

---

### Post by STREETURCHINE on 2007-01-03
thanks  taurus ,that worked

wert613,thanks for the reply i shall file that one for future referance..

---

### Post by MkfIbK7a on 2007-01-03
no problem:D

---

### Post by taurus on 2007-01-03
> **STREETURCHINE said:**
> 
wert613,thanks for the reply i shall file that one for future referance..

Just so you have the right command, it should be

```
gksudo **nautilus**
```

---

### Post by MkfIbK7a on 2007-01-03
yah sorry i dont acctually use natilus:?

---

### Post by mk04 on 2007-01-09
Is there a command to empty the whole trash instead of a specific file? 

I changed the directory to /home/<username>/.Trash and typed sudo rm libmtp-0.0.2/ and I get this error:
rm: cannot remove `libmtp-0.0.2/': Is a directory

---

### Post by taurus on 2007-01-09
```
cd ~/.Trash
rm -rf *
```

---

### Post by rbhigday on 2007-01-09
how do you get the resolved in the title?

---

### Post by areayetee on 2008-01-12
> **taurus said:**
> ```
cd ~/.Trash
rm -rf *
```

tried it worked like a charm, thanks :guitar:

---

### Post by nhandler on 2008-01-12
You can use this command to empty the entire trash:
```
rm -rf ~/.Trash
```
You can add sudo to the front of it to have it delete ALL files (even the ones you normally wouldn't be able to delete).

---

