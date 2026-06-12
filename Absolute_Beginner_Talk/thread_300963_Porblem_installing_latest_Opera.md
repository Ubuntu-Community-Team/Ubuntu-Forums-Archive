---
title: "Porblem installing latest Opera"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by Oki on 2006-11-16
I want to install latest Opera. Therefore I added deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free to my repository list. 

When typing “Opera browser” in synaptic it finds the latest Opera(9.02).When checking it for installation it also marks two other application - but the I get the error:

opera:
 Depends: libqt3c102-mt (>=3:3.2.1) but it is not installable


What do I do – thanks for your help:-)

---

### Post by ciscosurfer on 2006-11-16
Try replacing that repo with this one:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
Then do```
sudo aptitude update && sudo aptitude install opera
```

---

### Post by Oki on 2006-11-16
Thanks for answering! 

I have used Opera from canonical – but that version is buggy(and not the latest version), so therefore I wanted to try the other (and latest) version.

---

### Post by ciscosurfer on 2006-11-16
Well, you can [always go here]("http://www.opera.com/download/") and try using the Dapper version.

---

