---
title: "What does this mean??"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by ubdai on 2006-12-30
I'm all new to this and have muddled thru so far. But Now I've got this

'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. '

It seems to prevent any other progs from being installed!!

I run the command then get 
'dpkg: requested operation requires superuser privilege'

I've just done the auto install from cd for edgy and don't recall any superuser request to be setup. How does one get to a superuser?

What does it mean.?

tia
ubdai

---

### Post by taurus on 2006-12-30
Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by ubdai on 2006-12-30
Thanks Taurus.

That seems to have cleared the problem.
What does it all mean though.?

tia
ubdai

And is there a decent Ubuntu linux book that you could recommend for some background reading.:)

---

### Post by taurus on 2006-12-30
The first command is to fix the problem that you are having.  The second is to update the list; and the last one to upgrade packages if there are any.

I haven't seen this (reading it in person) but heard some good reviews about it...

[http://www.amazon.com/Official-Ubuntu-Book-Benjamin-Mako/dp/0132435942/sr=1-1/qid=1167498969/ref=pd_bbs_sr_1/102-6588274-8180128?ie=UTF8&s=books](http://www.amazon.com/Official-Ubuntu-Book-Benjamin-Mako/dp/0132435942/sr=1-1/qid=1167498969/ref=pd_bbs_sr_1/102-6588274-8180128?ie=UTF8&s=books)

---

