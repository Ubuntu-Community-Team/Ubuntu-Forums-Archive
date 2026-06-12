---
title: "Auto-Spell-Check in Kile ?"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-02-02
Hi,

Is there a auto-spell-check in kile so that whenever you type a mistake it gets highlited at that point, as in the case in openoffice.

thanks,
Ulas

---

### Post by findik1 on 2007-02-07
apparently there is that function yet

---

### Post by der_vegi on 2007-02-14
yeah, there is a function. but it always says that I(A)Spell couldn't be startet. at least for me, having xubuntu 6.10.

i've read, that you have to change the spell-checker settings for kde in the kcontrolcenter. but i don't use kde and don't want to install it just to change some settings for kile.

does anybody know about another solution?

---

### Post by findik1 on 2007-02-15
ok, let me try that, and be back

---

### Post by Toufik on 2007-02-16
> **der_vegi said:**
> i've read, that you have to change the spell-checker settings for kde in the kcontrolcenter. but i don't use kde and don't want to install it just to change some settings for kile.

If you install kcontrolcenter, you won't install KDE, just some k-libraries (like when you installed kile or amarok)

---

### Post by findik1 on 2007-02-16
I installed kcontrolcenter. How does autospell turn on in Kile?

---

### Post by ecoxmit on 2007-03-03
kile does not have an inline spell checker, see:

[http://sourceforge.net/mailarchive/message.php?msg_id=37888197](http://sourceforge.net/mailarchive/message.php?msg_id=37888197)

but probably will do in KDE4.0

---

### Post by ramos on 2007-12-08
I am trying to apply spell check in kile but I cannot. 

I tried to activate the spell checker in kde control center, as in forum "http://ubuntuforums.org/newreply.php?do=newreply&p=3711103" 
but it didn't work in kile.  

I tried to specify a path to the dictionary in kile but I don't know where is the dictionary. 
Anyone know how to fix this problem?

Thanks,
Ramos

---

### Post by nenjordi on 2007-12-15
Hi there,
I think i solved problem.
I installed this components:
kwrite or/and kate (If you install kate automaically install kwrite)
aspell (something related with spelling)
ispell, iamerican and ispanish (each language you need)
Now it works, it's not as good as i spected but works.
Hope it's useful for you :D

---

### Post by marrabld on 2008-01-16
you just need ispell.  

```
sudo apt-get install ispell 
```

---

