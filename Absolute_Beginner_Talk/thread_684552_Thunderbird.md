---
title: "Thunderbird"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by T.R.E. on 2008-02-01
I've installed thunderbird from repositories but it's 2.0.0.6 version. I'm using gutsy and i want to install thunderbird 2.0.0.9. I've downloaded the tar.gz package from Mozilla website but don't know how to install it. I wonder if someone could tell me in absolute beginner talk.

---

### Post by hyper_ch on 2008-02-01
what is better in 2.0.0.9?

---

### Post by philinux on 2008-02-01
2.0.0.9 is mainly a security fix for windows machines and a bug fix to do with crashing. TB has never crashed on me. I'd wait till an update appears in the repo.

---

### Post by jan quark on 2008-02-01
if you cant wait

navigate in the terminal to the extracted folder
and run these commands
one after the other
```

./configure
```
```
make
```
```
sudo make install
```

post the error messages here :)

---

### Post by T.R.E. on 2008-02-01
you know, lightning 0.7 is incompatible with current version of thunderbird in repos. and i realy havnt found the lightning in repos convenient. cause i used lightning 0.7 previously in windows.

---

### Post by T.R.E. on 2008-02-01
i did what you said and here's the error:

soheil@NB:~/Programs/thunderbird$ ./configure
bash: ./configure: No such file or directory

---

### Post by philinux on 2008-02-01
> **T.R.E. said:**
> you know, lightning 0.7 is incompatible with current version of thunderbird in repos. and i realy havnt found the lightning in repos convenient. cause i used lightning 0.7 previously in windows.


That's odd as I'm running 2.0.0.6 from repo with the 0.7 lightning addon from mozilla. No crashes or errors of any kind.

To the OP, if you want the latest and greatest then a better idea would be to use this;

[http://ubuntuzilla.wiki.sourceforge.net](http://ubuntuzilla.wiki.sourceforge.net)

this way is doesn't mess with synaptic.

---

### Post by T.R.E. on 2008-02-01
thank you philinux i'll check it out.

---

### Post by T.R.E. on 2008-02-01
i found out wat the problem is. mozilla website provides only 32-bit applications. but my ubuntu is 64-bit. so i canot integrate lightning 7.0 with the thunderbird i've install from repos. is there any way i can use it wit my currently installed thunderbird?

---

### Post by Golem XIV on 2008-02-01
> **T.R.E. said:**
> i found out wat the problem is. mozilla website provides only 32-bit applications. but my ubuntu is 64-bit. so i canot integrate lightning 7.0 with the thunderbird i've install from repos. is there any way i can use it wit my currently installed thunderbird?

Did you try [this]("http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.7/contrib/linux-x86-64/")?

---

