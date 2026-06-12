---
title: "Wine and Feisty"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Harkainos on 2007-04-21
Would I install Wine in 7.04 the same way as in 6.10? What issues should I look for?

---

### Post by Theimon on 2007-04-21
> **Harkainos said:**
> Would I install Wine in 7.04 the same way as in 6.10? What issues should I look for?

sudo aptitude install wine


That should do fine.

---

### Post by Harkainos on 2007-04-21
Do I need to add the Repository? I am at work now.... I will get it working regardless. I am just curious

---

### Post by Theimon on 2007-04-21
As far as I know, you don't need to add any repo, just enable them all. I'm not quite sure in which one wine resides so check your sources.list, take out the comments so universe multiverse etc. are enabled and it should work like a charm :)

---

### Post by Campingman on 2007-04-21
You do not need to add anything.  Just sudo aptitude update and sudo aptitude install wine worked for me.

---

### Post by sunexplodes on 2007-04-21
With all that said, is there an easy way to roll back to Wine v 0.9.25?

 0.9.33 has a few deal-breaker problems for me, but 9.25 isn't in the Feisty repo.

---

### Post by Theimon on 2007-04-21
> **sunexplodes said:**
> With all that said, is there an easy way to roll back to Wine v 0.9.25?

 0.9.33 has a few deal-breaker problems for me, but 9.25 isn't in the Feisty repo.

You could always compile from source....

---

### Post by sunexplodes on 2007-04-21
Is there an alternative for somebody who values their time?

---

### Post by Theimon on 2007-04-21
> **sunexplodes said:**
> Is there an alternative for somebody who values their time?

Compiling Wine doesn't take that long....it's just Wine :)

But I found this at he Winehq site: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) All versions there including your 0.9.25 :)

---

### Post by sunexplodes on 2007-04-21
ahhhh, perfect.. thank you.

---

