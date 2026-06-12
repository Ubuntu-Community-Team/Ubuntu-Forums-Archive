---
title: "[SOLVED] Title bars missing upon startup"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2007-05-10
Every time I boot into Ubuntu the title bars are missing.  I can bring them back by going to Desktop Effects -> Enable Desktop Effects -> Use Previous Settings.  However I need to do this every startup . . .

---

### Post by jkblacker on 2007-05-10
Are you running Beryl?

---

### Post by gohanssjn on 2007-05-10
> **AncientPC said:**
> Every time I boot into Ubuntu the title bars are missing.  I can bring them back by going to Desktop Effects -> Enable Desktop Effects -> Use Previous Settings.  However I need to do this every startup . . .

I had this issue.

I believe I went to /lib/usr/compiz or similar and ran mediacity.so.

Just search for that file and double click it!

---

### Post by AncientPC on 2007-05-10
> **jkblacker said:**
> Are you running Beryl?

Nope, never had it installed.  I tried out desktop effects, didn't work, turned it off and now my title bars are missing upon startup.

> **gohanssjn said:**
> I had this issue.

I believe I went to /lib/usr/compiz or similar and ran mediacity.so.

Just search for that file and double click it!

That directory doesn't exist for me.

---

### Post by gohanssjn on 2007-05-10
That's ok, I am doing this away from my Ubuntu box.

Just search for Mediacity.so.  As long as it's in a usr folder somewhere, run it and save your session.

---

### Post by AncientPC on 2007-05-10
> **gohanssjn said:**
> That's ok, I am doing this away from my Ubuntu box.

Just search for Mediacity.so.  As long as it's in a usr folder somewhere, run it and save your session.
That file doesn't exist anywhere on my system.

---

### Post by gohanssjn on 2007-05-10
That's becasue I am an idiot.

I think it's actually metacity.so

Can anyone confirm that that is the filename?

---

### Post by jkblacker on 2007-05-10
> **gohanssjn said:**
> That's becasue I am an idiot.

I think it's actually metacity.so

Can anyone confirm that that is the filename?

Yes I have one of those on my system.

---

### Post by gohanssjn on 2007-05-10
There you go then!   double clicked that last night and got all my title bars back when they were gone on restarts.  Good luck!

---

### Post by AncientPC on 2007-05-11
Is metacity.so a file that came with compiz / beryl?  Because I don't have the two installed and I still can't find a file called metacity.so.

---

### Post by AncientPC on 2007-05-30
I found it at these two locations but oddly enough Ubuntu isn't missing my titlebars anymore.
/usr/lib/python2.4/site-packages/gtk-2.0/metacity.so
/usr/lib/python2.5/site-packages/gtk-2.0/metacity.so

---

