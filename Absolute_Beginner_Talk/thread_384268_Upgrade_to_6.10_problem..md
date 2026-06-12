---
title: "Upgrade to 6.10 problem."
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by RandyOldgeek on 2007-03-14
I upgraded to Ubuntu 6.10 from 6.06 and now when I open Kontact and click on the News, to open the Newsreader I get:

Cannot load part for News. Library files for "libknodepart.la" not found in paths.

Any idea of what I can do to fix this?

Thanks

---

### Post by dannyboy79 on 2007-03-14
gogle is a great resource for ALL questions when you can't find it in the search function within this forum. here ya go:
[https://launchpad.net/ubuntu/+source/kdepim/+bug/64448](https://launchpad.net/ubuntu/+source/kdepim/+bug/64448)
it's a bug and there is a fix. see the link.

---

### Post by RandyOldgeek on 2007-03-14
> **dannyboy79 said:**
> gogle is a great resource for ALL questions when you can't find it in the search function within this forum. here ya go:
[https://launchpad.net/ubuntu/+source/kdepim/+bug/64448](https://launchpad.net/ubuntu/+source/kdepim/+bug/64448)
it's a bug and there is a fix. see the link.

Thanks a bunch.

I never thought about googleing to find the answer.....duhhhhhhh](*,) 

I should have thought of that first...ha.

---

### Post by RandyOldgeek on 2007-03-14
You know I read the bug report and it makes no sense to me.  Here is what they say to do to fix this problem:

"Imho there are two options to fix this. Knode should be added to main and to the dependencies of Kontact or the News part has to be removed from Kontact."

How do you add Knode to the main.....and what it the main?

How do you remove the News part from Kontact?

Thanks  for any help on this.

---

### Post by dannyboy79 on 2007-03-14
apparently you're not reading far enough! the solution that is written is the overall solution so that this doesn't happen in the future. this is the solution for the developers. your solution would be to do 

sudo aptitude update && aptitude install knode

according to the solution just below what you read. if this doesn't work, than I don't know as I don't use kde. i simply like helping people out, i read their problem, I gogle it and present the solution, that's it. good luck

---

### Post by RandyOldgeek on 2007-03-14
Hey Thanks

I looked right at that and didn't know what it meant....jeeze. 

I did run it and it didn't work.  It says:

" Package knode is not available, but is referred to by another package.......and it goes on and on. 

Well thanks anyway. 

Linux is fun.....when it isn't so darned frustrating....ha!!

---

### Post by dannyboy79 on 2007-03-14
and have you enabled the universe and other repos??? use gogle to find out how to do this if you don't know

---

### Post by RandyOldgeek on 2007-03-14
Hey that did it.....once I figured out what a Universe and Repo was....ha. 

Then tried the install again and it worked....

Thanks for your help and making me a google user for searching out solutions for Linux problems.

---

### Post by dannyboy79 on 2007-03-14
glad you got it. chalk up another user helped.

---

### Post by synesthesia on 2007-03-21
Hi, I'm running Edgy 6.10 and switched to KDE hoping to get the news reader on Kontact working. I also downloaded the Knode package successfully, but I still get that same error message

Library files for "libknodepart.la" not found in paths

Any ideas to get my news working???

---

### Post by dannyboy79 on 2007-03-21
I can't help if you already installed the KNode package. If you haven't done much, I would simply actually install Kubuntu. This might be the problem since you installed Gnome first but then tried to install KDE dependent app. Did you install per this ([http://www.psychocats.net/ubuntu/kde)?](http://www.psychocats.net/ubuntu/kde)?)

---

