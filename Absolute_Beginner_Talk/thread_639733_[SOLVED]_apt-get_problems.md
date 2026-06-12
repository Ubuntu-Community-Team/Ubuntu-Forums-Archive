---
title: "[SOLVED] apt-get problems"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Jet8225 on 2007-12-13
Since I'm new at using linux I posted it here. Every time I use sudo apt-get update I get this: 

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems 

Can somebody please tell me what these means and what can I do to fix it?

Oh, and every time i try to install a package it says it couldn't be found.

---

### Post by Jet8225 on 2007-12-13
anyone?

---

### Post by flamelab on 2007-12-13
Some repositories need a key for access to their programs . If you search in Google for its key you will be able to add it in this way 
 (the example here is medibuntu.org)

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

You will be able to add their key in a similar way .
 Do these 

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

sudo apt-get update
```

And you have finished !

P.S.This key is found in [http://wine.budgetdedicated.com/apt/]("http://wine.budgetdedicated.com/apt/") . You will do the same thing ( **[COLOR="Red"]wget-q <url>.<xxxxxxx.gpg> -O- | sudo apt-key add -[/COLOR]**) for every repository you find and can't add their key.

---

### Post by Jet8225 on 2007-12-13
Even if it does the same thing for every program I try to download? And what about when I do the update?

---

### Post by flamelab on 2007-12-13
I just updated my answer :) above .
You follow the instructions and do these 

1)You add the repo
2)You go to the site and see the name of the .gpg file
3)You add the URL and the name of the .gpg file in the command above

:lolflag:

---

### Post by Jet8225 on 2007-12-13
forget it, it already worked, Thanks guys!

---

### Post by haggus on 2007-12-13
you should mark this thread solved from thread tools that way others can benefit from the solution

---

### Post by Jet8225 on 2007-12-13
Thanks for telling, I didn't know about that function. I'm a complete newbie here.

---

