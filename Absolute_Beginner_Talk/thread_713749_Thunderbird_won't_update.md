---
title: "Thunderbird won't update"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by von Stalhein on 2008-03-03
Hello all,
I had the "update" icon come up, and (according to the results) installed Thunderbird 2.0.0.12

However, the menu in Thunderbird displays 2.0.0.6

I tried to re-install thru the package manager, which tells me it's successful but still no result. I have restarted Thunderbird, and also rebooted.

Ubuntu 7.10 btw.

TIA for any hints.

---

### Post by oakgrove on 2008-03-03
Is it possible that you have two executables for Thunderbird in two different places?  Maybe if you do a "whereis thunderbird" in your terminal, you could check and see if that is the case.  If you do have more than one and you are using different ways to start the program, e.g. an icon on the desktop and one in your menu each pointing to a different executable, that could be what is causing your problem.  Note that it is quite possible for multiple installs to use the same profile in your /home/user/.mozilla-thunderbird/ directory also.

If that is the case, then you will have something to go on to figure out what you want to do about it.  Be it to modify your shortcuts or delete the duplicate executables or both.

---

### Post by von Stalhein on 2008-03-03
Thanks.
 Did that, I get 
```
thunderbird: /usr/bin/thunderbird /etc/thunderbird /usr/lib/thunderbird /usr/share/thunderbird /usr/share/man/man1/thunderbird.1.gz
```

As far as starting it, I use the toolbar icon exclusively.

---

### Post by oakgrove on 2008-03-03
Well, at least you know that that's not your problem.  You are definitely only using the one executable in /usr/bin/thunderbird.  I'm stumped at this point and although I could recommend some drastic measures like purging thunderbird completely from your system with "sudo apt-get purge thunderbird" and then reinstalling really from scratch and importing your profile back in, I'll leave that up to your best judgement.  Maybe someone else can chime in that has had this problem before and found an easier solution.

---

### Post by kellemes on 2008-03-03
Another check.. just to add to the confusion I'm sure ;-)
```
thunderbird --version
```

---

### Post by von Stalhein on 2008-03-03
I'll try that - I see your cunning plan - to see whether the >help>about dialogue is telling porkies.

I'll do it when I get home from work and report back.

---

### Post by von Stalhein on 2008-03-04
Oh yes, kellemes, you've hit the nail on the head with your suspicious mind :)

```
thunderbird --version
 Thunderbird 2.0.0.12, Copyright (c) 1998-2008 mozilla.org

```

So, for some reason teh wrong program version is being reported in the >help>about

---

