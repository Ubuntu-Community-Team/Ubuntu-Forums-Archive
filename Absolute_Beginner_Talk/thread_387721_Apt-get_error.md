---
title: "Apt-get error"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by maccawolf on 2007-03-18
I am new to Ubuntu. (less than a week now).
 WHen I finally got it loaded (took 6 attempts), I updated as per the auto update that said I had 139 program updates. Stupid me, didn't look at what was to be updated, and I just let it update everything. Now I get an error:
E: (Linux is in D drive, not E ) syntax error /etc/apt/apt.conf:2: extra junk at end of file

WHAT????? How can I either fix that, or roll back the updates and do them piecemeal til I find the erroring one?

---

### Post by dstew on 2007-03-18
The "E:" does not mean a drive. That is a tag on the beginning of an apt-get error message.

Maybe you can ignore the error. Did your packages install?

---

### Post by maccawolf on 2007-03-18
I think the origianl ones did update, but I am unable to get anything new. Every time I try to update or d/l something. all I get is that error.

---

### Post by maccawolf on 2007-03-18
for instance, A REALLY good friend uses ICQ and I'd like to install GnomeICU, but I can't.

---

### Post by bapoumba on 2007-03-18
> **maccawolf said:**
> 
E: (Linux is in D drive, not E ) syntax error /etc/apt/apt.conf:2: extra junk at end of file

Could you post this file ? Open a terminal (> Accessories > Terminal) and run:
```
cat /etc/apt/apt.conf
```
paste the complete output in here.

---

### Post by maccawolf on 2007-03-18
Apt: cache- limit 12582912

---

### Post by bapoumba on 2007-03-18
You're missing a**[COLOR="Red"] :[/COLOR]** and a**[COLOR="Red"] ;[/COLOR]**

Open the file with nano:
```
sudo nano -B /etc/apt/apt.conf
```
change it to look like this:
```
APT:**[COLOR="Red"]:[/COLOR]**Cache-Limit 12582912**[COLOR="Red"];[/COLOR]**
```
CTRL-O to save thefile (same name, hit <enter>)
CTRL-X to exit nano.
```
sudo aptitude update
```
Any more errors? If so, please paste them in here.

---

### Post by maccawolf on 2007-03-18
THANKS. second colon was there, (missed it) but semi colon was not, so I added it.
THANKS, it seems to have worked.

---

### Post by bapoumba on 2007-03-18
Glad to see you got it to work :)

---

