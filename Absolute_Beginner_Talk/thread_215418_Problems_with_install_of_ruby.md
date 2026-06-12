---
title: "Problems with install of ruby"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by cjnkns on 2006-07-13
Hi all...

I recently installed ruby using the synaptic package manger and I am still unable to run a simple ruby program. I found where the manager installed my ruby dir /usr/lib/ruby/rub1.9 but when I attempt to locate it using "which ruby" i get nothing. Or when I try to run a ruby program all i get is another command prompt. 

Has anyone else had a similar issue?

---

### Post by oldmanstan on 2006-07-13
which package did you install? if you only installed the ruby1.9 package then you have to run ruby1.9 not just ruby.

there is a package called simply "ruby" in the repository. it will let you run the interpreter my just typing "ruby".

also, you may want to remove version 1.9 and switch to 1.8 (which is what the "ruby" package is) since (as i recall) the odd numbered version of ruby are the experimental versions. i might be wrong on that though.

---

