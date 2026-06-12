---
title: "Open Office becoming unstable?"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2007-06-01
Hi, I'm wondering if anyone else is having trouble with OpenOffice crashing?

Over the last few weeks I've noticed it gradually crashing more often. I often copy pages from the net straight into OO.
Today, in the space of an hour it crashed 5 times, 4 times it restarted and recovered the files, but the last time it froze the entire machine. Mouse worked but nothing else, no buttons working.

I had to power down and restart. I don't get any error messages.

It's also slowed down for scrolling and saving, which, btw,  is when these crashes occur.

Is it just me or is it happening across the board?
I've not seen any other posts re this.

---

### Post by hellmet on 2007-06-01
I don't use Office much, but the only problem I find with OOo is that it takes helluva time to load .. Other than that.. its been nice tho.

---

### Post by Rui Pais on 2007-06-01
hi,
whats you version? 2.0.4, 2.2, older? dapper, edgy or feisty?

If that started to happen after it worked ok for a while you may have a corrupted config file. 
Try:
```
mv .openoffice.org2 .openoffice.org2_BACKUP
```
and restart oo

do a:
```
 sudo aptitude reinstall openoffice.org
``` 
wouldn't hurt too...

good luck

---

### Post by carloslosgrande on 2007-06-02
Hi Rui Pais, thanks for the help. I'm just wondering if this is related to the problems associated with kernel version 16?
Right now I'm on version 16 but I'm going to go back to version 15 until the fix comes in and see if that does the trick.

---

### Post by Rui Pais on 2007-06-02
Don't know... how would a specific kernel (that essentially deals with hardware) could interfere with OO a data oriented app... but who knows. 

Have you tried to mv away the .openoffice.org2?

Try too, to disable java at options... sometimes its a source of mysterious problems-

If you have Edgy and 2.0.4 or 2.0.3 that version, besides old, is very buggy. Try to upgrade if not the all Ubuntu at least your OO to 2.2 (you can do it using the Openoffice site software or downloading Feisty packages).

---

### Post by carloslosgrande on 2007-06-02
I dont know either.
Sorry I wasn't more specific. I'm running feisty and the latest OO 2.2.
I'll give your fix a try.

Well, just completed it and checked one of the problem files, seems to be working well, even scrolls thru
Thanks man!

---

### Post by Rui Pais on 2007-06-02
good :)

lets hope it was just a broken config file and problem is definitely solved.

have fun.

---

### Post by blue_shift on 2007-06-02
When I was using 2.0.x it used to take ages to copy data from the internet onto a page using the clipboard, almost as if it was downloading the data again not using the clipboard (is this the case?). Anyhow, since 2.2.0 there's not been much of an issue.

---

### Post by Rui Pais on 2007-06-02
> **blue_shift said:**
> When I was using 2.0.x it used to take ages to copy data from the internet onto a page using the clipboard, almost as if it was downloading the data again not using the clipboard (is this the case?). Anyhow, since 2.2.0 there's not been much of an issue.

That was a knowing issue (theres plenty of threads on that) with 2.0.x. 
A lot of people even report a complete brake or a frozen unless they copy page as text (and not as html).

I, among others, had problems with inserting eps made with huge files of data. Insert them as png made the details not legible and useless, i rebooted to dapper every time i need to work with OO :(

Lets say that the 2.0 will not left much fans around ;)

---

