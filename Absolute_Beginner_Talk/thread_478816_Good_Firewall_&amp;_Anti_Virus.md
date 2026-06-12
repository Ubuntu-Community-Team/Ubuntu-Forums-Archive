---
title: "Good Firewall &amp; Anti Virus"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by FAS786 on 2007-06-19
Hiya Does anone know
a good Firewall and Antivirus that are freeware
Preferable of the same company e.g Panda etc
Dont matter if you dont just what gd ones do you know???
Thanx for your help)

---

### Post by floke on 2007-06-19
For ubuntu?
Relax, you don't need them unless you're sharing files with other Windows boxes.

---

### Post by oilchangeguy on 2007-06-19
> **FAS786 said:**
> Hiya Does anone know
a good Firewall and Antivirus that are freeware
Preferable of the same company e.g Panda etc
Dont matter if you dont just what gd ones do you know???
Thanx for your help)

ubuntu has a built in firewall, iptables. and as for anti-virus software. it's not needed.

---

### Post by Crafty Kisses on 2007-06-19
> **FAS786 said:**
> Hiya Does anone know
a good Firewall and Antivirus that are freeware
Preferable of the same company e.g Panda etc
Dont matter if you dont just what gd ones do you know???
Thanx for your help)

If you really need Anti-Virus there's always AVG.

---

### Post by bodhi.zazen on 2007-06-19
Linux security is different from Windows.

At any rate, 

Firewall : Look at guarddog or firestarter

Antivirus : Too many false +, but :

[http://doc.gwos.org/index.php/How_to_ClamAV](http://doc.gwos.org/index.php/How_to_ClamAV)

For some real information, look at this book (I found a copy at the local library) :

[http://www.apress.com/book/bookDisplay.html?bID=395](http://www.apress.com/book/bookDisplay.html?bID=395)

Or this :

[http://www.google.com/search?q=Linux+Security&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=Linux+Security&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by floke on 2007-06-19
Isn't firestarter just a GUI frontend for IPtables that are inbuilt?

---

### Post by wormser on 2007-06-19
ClamAV is a popular antivirus software.

```
sudo apt-get install clamav avscan
```

Avscan is the gui front end.

For managing the firewall use Firestarter.

```
sudo apt-get install firestarter
```

---

### Post by bodhi.zazen on 2007-06-19
> **Steve.K said:**
> Isn't firestarter just a GUI frontend for IPtables that are inbuilt?


The are all gui front ends for IP tables. Not many know how to write IP table rules.

---

