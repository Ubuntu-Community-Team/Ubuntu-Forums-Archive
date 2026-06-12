---
title: "random folder names - samba"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by huggy77 on 2007-10-24
My folders are getting renamed randomly when pushing data to a directory.

Occasionally when i push a folder into a directory via samba, the folder name get renamed to a totally random name.  It happens on appletalk too...  Any thoughts...  The folder is on an ext3 partition. This issue is making me a crazy person

---

### Post by hyper_ch on 2007-10-24
can you give examples?

---

### Post by huggy77 on 2007-10-24
it has not happend in about a week - but last time it happened i pushed a folder full of large raw images from a mac to my linux box via a samba share.   THe client who is this happening frequently uses spaces in his folder names.  Characteristically the folders names are long and have spaces...  An example would be **FOO BAR - photos of the 125 main street office.**...

that will in turn lead to a folder named KFSIWOFKSNWOOWO or something of that nature...  And it is totally random - i cant reproduce it when it happens...

i am running edgy on the offending machine....

I have tried apple talk as well and occasionally it happens with that protocol as well...

thanks for the interest

---

### Post by huggy77 on 2007-10-24
any ideas as to what logs to check when this happens next time?

---

### Post by Dr Small on 2007-10-24
> **huggy77 said:**
> it has not happend in about a week - but last time it happened i pushed a folder full of large raw images from a mac to my linux box via a samba share.   THe client who is this happening frequently uses spaces in his folder names.  Characteristically the folders names are long and have spaces...  An example would be **FOO BAR - photos of the 125 main street office.**...

that will in turn lead to a folder named KFSIWOFKSNWOOWO or something of that nature...  And it is totally random - i cant reproduce it when it happens...

i am running edgy on the offending machine....

I have tried apple talk as well and occasionally it happens with that protocol as well...

thanks for the interest
Why use samba ?
Why not try sftp, scp or ftp ?

---

### Post by huggy77 on 2007-10-24
because i am a bit of a a newbie and i dont think out of the box...   I asked one of our photographers and he said that this has happened to him as well via FTP....

i really think it has something to so with the spaces in the filenames but my client refuses to abandon this practice....

i really appreciate everyone trying to help...

---

### Post by huggy77 on 2007-10-24
This appears to be a samba issue.

when i view a folder via samba it looks like:
2FW8II~5

when i ssh into the directory it looks like:
2007 10 : 01 camera raw finished

colons will do that to you!

---

