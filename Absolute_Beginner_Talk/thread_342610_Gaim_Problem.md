---
title: "Gaim Problem"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-01-20
I am trying to signin via gaim on msn hotmail account, using 6.06LTS and as soon as it logs in, it crashes...

---

### Post by ComplexNumber on 2007-01-20
> **shoaibi said:**
> I am trying to signin via gaim on msn hotmail account, using 6.06LTS and as soon as it logs in, it crashes...
what version of gaim are you using? i'm using version 2.0.0beta3.1 with msn, and i have no problem. then again, my setup differs to yours in that i'm using ubuntu 6.10(ie edgy)

---

### Post by Duppy on 2007-01-20
I had this, does it just close without warning? If so...
remove gaim:

type this into terminal

```
sudo apt-get remove gaim
```

then type this to make sure everything is updated

```
sudo apt-get update
```

then this

```
sudo apt-get upgrade
```

then re-install GAIM:

```
sudo apt-get install gaim
```

Hope that helps you.

---

### Post by shoaibi on 2007-01-20
idont wona upgrade to edgy eft it has so many bugs in it

---

### Post by Duppy on 2007-01-20
Its not upgrading to edgy eft...

either do what i said or dont, your choice.

---

### Post by shoaibi on 2007-01-20
how uch bandwith wll it cost?

---

### Post by shoaibi on 2007-01-21
have done that, cost 147MB bandwidth, still no use, still Gaim crashes, and if i install Edgy Eft i.e. downlaoded iso, that hangs or stops to respond after every 2 minutes...

---

### Post by david_kt on 2007-01-21
> **shoaibi said:**
> I am trying to signin via gaim on msn hotmail account, using 6.06LTS and as soon as it logs in, it crashes...

Why don't you try AMSN ? It is develope special for MSN meseenger.

[INDENT]sudo apt-get install amsn[/INDENT]

Regards,
DK

---

