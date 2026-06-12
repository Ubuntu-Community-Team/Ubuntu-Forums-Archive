---
title: "While updating and removing Programs"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2008-04-10
I came across this error: /var/lib/scrollkeeper/fr/scrollkeeper_cl.xml:792: parser error : Extra content at the end of the document
"SystemServicesPrinting">

Any ideas? Was trying to install Hardy But I didnt want to reinstall the whole desktop, and while trying to cancel it out, I got that error

---

### Post by Martje_001 on 2008-04-13
Well, it is a beta version.. but does this error stop you from updating?

---

### Post by kellemes on 2008-04-13
Get root and move the broken file somewhere safe..
```
mv /var/lib/scrollkeeper/fr/scrollkeeper_cl.xml /root
```

Reconfiguring Scrollkeeper and regenerate the file..
```
dpkg-reconfigure scrollkeeper
```

---

### Post by sports fan Matt on 2008-04-13
I really must keep track of my old posts, since this im running Hardy Fine, the only thing im refusing to run is the sudo aptitude autoclean in my brain to remove and clean these old posts that I seem to forget about...:)

---

