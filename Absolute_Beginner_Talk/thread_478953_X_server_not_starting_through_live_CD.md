---
title: "X server not starting through live CD"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2007-06-19
My buddy is trying to get the Feisty live CD running but it is complaining about the X server not being able to start.  I looked around and found out he needs the intel driver but I don't know how to get the driver onto his system using a live CD session.

He is running a Dell D630...

Any ideas?

btw he has no internet.

---

### Post by Happy_Man on 2007-06-19
> btw he has no internet 

Until there, I had a fix. Now, none. 

I would suggest the alternate install. That's your only option at this piont. Use herman's site for a tutorial.  [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by charles.g.moore on 2007-06-19
> **Happy_Man said:**
> Until there, I had a fix. Now, none. 

I would suggest the alternate install. That's your only option at this piont. Use herman's site for a tutorial.  [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Yeah I know,
I was trying to figure out a way for him to do it without d-loading the alternate...
Thanks anyways, it seems the forums are saying that is the only way (get the system on then you can do all the necessary changes to the X server....)

---

### Post by p_quarles on 2007-06-19
The live CD doesn't depend on the internet at all, so that's not the problem.

The issue could be either a) his memory is too low (<256 MB) to support the live CD, or b) he has a widescreen monitor. Either way, he should use the alternate CD. He can fix any problems later.

---

### Post by p_quarles on 2007-06-19
> **charles.g.moore said:**
> Yeah I know,
I was trying to figure out a way for him to do it without d-loading the alternate...
Thanks anyways, it seems the forums are saying that is the only way (get the system on then you can do all the necessary changes to the X server....)
Ouch. For the record, I posted my last message before I saw this reply. 

Still, the alternate CD actually *does *work better than the live CD. :-)

---

### Post by charles.g.moore on 2007-06-19
> **p_quarles said:**
> Ouch. For the record, I posted my last message before I saw this reply. 

Still, the alternate CD actually *does *work better than the live CD. :-)

Yeah, I just suggested that he d-load the alternate.  

He wanted to know if he could d-load the driver, then mount his NTFS drive and see if he could get it that way.

I figured out early on that it is so much easier to go the route people have proven rather keep beating your head against the wall to muscle linux into submission...

---

### Post by Happy_Man on 2007-06-20
> **charles.g.moore said:**
> 
I figured out early on that it is so much easier to go the route people have proven rather keep beating your head against the wall to muscle linux into submission...

Yes, Linux is a good pet, but a stubborn one when it wants to be. If you have a problem it doesn't want to solve, well, let's just say that's the point when most newbies go back to Windows. Good to see you're keeping at it.

---

### Post by atria on 2007-06-20
Does the failsafe boot option work? It works here with my intel card. 

You might want to give it a try

---

### Post by charles.g.moore on 2007-06-20
> **atria said:**
> Does the failsafe boot option work? It works here with my intel card. 

You might want to give it a try

Failsafe boot option???

How would i go about using that option?

---

### Post by Happy_Man on 2007-06-20
When you get to the login screen, down in the corner it says Options. Choose that, Sessions, and then there should be an option for Failsafe GNOME. Try that.....

---

