---
title: "Question about Abiword"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by ron999 on 2006-11-12
Hi
When using Abiword, if I use Help, it opens up in Opera browser.
How can I change this so that it opens up in Swiftfox (or Firefox) instead?
:-k

---

### Post by bulldog on 2006-11-12
Well there's something like System-->Preferences-->Default Applications.

Maybe you should take a look in there?

---

### Post by ron999 on 2006-11-12
Hi Bulldog
It's System->Preferences->Preferred Applications.
I've already checked that, it's set at /opt/swiftfox/swiftfox "%s"
There must be something else to set.

Edit
Do you know what this means:-[http://www.abisource.com/twiki/bin/view/Abiword/UnixFaqDefaultBrowser]("http://www.abisource.com/twiki/bin/view/Abiword/UnixFaqDefaultBrowser")

---

### Post by bulldog on 2006-11-12
LOL, well I believe you if you say so,Preferred instead of Default.

Well seems to me you just dump all the browsers exept swiftfox,:D 

But seriously,I haven't a clough.

Don't use abi-word so can't really say anything about it.

---

### Post by ajgreeny on 2006-11-12
If you have any other desktop environments installed, eg xfce or KDE, make sure their preferences also point to firefox.

---

### Post by ron999 on 2006-11-12
ajgreeny
How do I find out if I have any other desktop environments installed?

---

### Post by ajgreeny on 2006-11-12
You will have to have installed them yourself, or just possible if you installed from the multi DE version on Linux Format Magazine #83 that you already have both KDE and xfce installed as default.

---

### Post by ron999 on 2006-11-12
ajgreeny
I haven't installed any environments myself and I didn't use Linux Format Magazine CD.
Any more ideas?

---

### Post by Arisna on 2006-11-12
That wiki page might be a clue.  Try opening a terminal and entering the following.  Post the output here.

```
echo $BROWSER
```

---

### Post by ron999 on 2006-11-12
No output from that command Arisna
ron@ron-desktop:~$ echo $BROWSER

ron@ron-desktop:~$

---

