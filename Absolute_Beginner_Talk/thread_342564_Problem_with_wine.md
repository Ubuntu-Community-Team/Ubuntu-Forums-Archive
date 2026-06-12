---
title: "Problem with wine"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by T4tav on 2007-01-20
Ive just installed Ubuntu 6.0.6 and i have added wine to the Synaptic package manager , but i keep getting this error message 

```
W: GPG error: http://wine.budgetdedicated.com dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

```

---

### Post by divague on 2007-01-20
in a terminal:

$wget [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg)
$gpg --import 387EE263.gpg
$sudo apt-key add 387EE263.gpg

---

### Post by T4tav on 2007-01-20
Thx ,Works fine

---

### Post by apps4apps on 2007-01-21
I had the same issue with Edgy and this seemed to fix it also. Thanks :) . Out of curiosity, where can I find more info on this? I was a bit surprised that this info wasn't listed on the WineHQ site or in an easy to find FAQ.

---

### Post by jvc26 on 2007-01-21
This is because the repository is protected by a key. I checked out the wineHQ and was surprised that the info for this wasnt shown on their site. The commands you have been given are those to download the key from the site and to store it on your computer so that when you try to download from the repo it can.
Il

---

