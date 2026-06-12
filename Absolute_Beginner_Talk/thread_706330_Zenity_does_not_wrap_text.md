---
title: "Zenity does not wrap text"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Martje_001 on 2008-02-24
Hi,
Like the title says: zenity does not wrap my text :(. This is in a bash script:
```
text="Op de eerste regel voert u in hoe snel de rar-bestanden opgesplitst dienen te worden (in megabytes). Op de tweede geeft u de compressie aan (0=Niet, snelst 5=Hoogst, langzaamst). Op de derde regel kunt u eventueel een wachtwoord aangeven (let op: zonder wachtwoord is het niet meer mogelijk de archieven te openen, omdat er encryptie wordt toegepast). 

Er zijn standaardwaarden voor u ingevuld."

zenity --entry --text="$text" --entry-text="0 10"
```

and I get this (see attachment).

Anyone knows what's going on?

---

### Post by Martje_001 on 2008-02-24
Btw: Maby it is because I'm running Ubuntu Hardy Heron. Maby someone can run the following script in Gutsy / Feisty / Edgy ?:
```
#!/bin/bash
text="Op de eerste regel voert u in hoe snel de rar-bestanden opgesplitst dienen te worden (in megabytes). Op de tweede geeft u de compressie aan (0=Niet, snelst 5=Hoogst, langzaamst). Op de derde regel kunt u eventueel een wachtwoord aangeven (let op: zonder wachtwoord is het niet meer mogelijk de archieven te openen, omdat er encryptie wordt toegepast). 

Er zijn standaardwaarden voor u ingevuld."

zenity --entry --text="$text" --entry-text="0 10"
```

---

### Post by glennric on 2008-02-24
It does the same thing in gutsy.  I don't think zenity wraps text.  You have to tell it where to put line breaks.

---

### Post by Martje_001 on 2008-02-24
That's not an option, because I want to write it in serveral languages. Is there a program (similair to zenity) which wraps?

---

### Post by glennric on 2008-02-24
Hmm, look at the man page of zenity.  It seems there is an option --no-wrap to disable text wrapping, but there isn't an option to enable it.  That must mean that wrapping text is the default, but I don't know why yours is not wrapping.

---

### Post by Martje_001 on 2008-02-24
Yes, everything except 'entry-box' get wrapped :(.

---

