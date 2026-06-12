---
title: "[SOLVED] Change language in Gimp 2.6"
date: 2008-10-15
forum: Art &amp; Design
---

### Post by sennep on 2008-10-15
Does anyone know how to set the language in Gimp 2.6 to English? I would prefer Gimp to be in English rather than my native language, but I can't seem to find any way of doing this?

Any help is appreciated:)

---

### Post by smartboyathome on 2008-10-15
I think you'd have to adopt English as the native, I don't think it allows custom languages.

---

### Post by sennep on 2008-10-16
I finally figured it out after some trial and error.
In case somebody else wants to know:

In Ubuntu, go to System->Preferences->Main Menu.
Find Gimp (under Graphics), rightclick on it and select properties,
where it says **Command**, change ```
gimp-2.6 %U
```
to ```
env LANGUAGE=en gimp-2.6 %U
```
If you want a different language than English simply change **en** to something else like **fr** or **de**.

---

### Post by brzeti on 2009-02-01
> **sennep said:**
> 
env LANGUAGE=en gimp-2.6 %U

Thanks sennep. That's exactly what I was looking for.

---

### Post by enginuysal on 2009-02-21
thanks

---

### Post by FranJPR on 2009-12-02
what about kubuntu 9.10???

Thank you!

---

### Post by rakiem on 2010-01-31
Thanks, fantastic work!

---

### Post by QMech on 2010-02-17
Thank you for your post.  Your solution worked just now on GIMP 2.6 and Ubuntu 9.10.  It was spot on.

---

### Post by JohnHeikkila on 2010-09-07
Sorry for bumping, but what if I want to change the GIMP language for more than just the main menu launcher?

---

### Post by monet.hart on 2010-09-08
Is it also possible to have any other language in the world

---

### Post by micronetic on 2011-01-14
Thank you very much, this did help me. I don't know why but I can't work in german programs although I am from germany :D

---

### Post by xyzt on 2011-04-25
sennep, thanks a bunch! The local translation is so creatively awful I didn't even understand the thing.

---

### Post by that_is_lg on 2012-11-29
> **sennep said:**
> I finally figured it out after some trial and error.
In case somebody else wants to know:

In Ubuntu, go to System->Preferences->Main Menu.
Find Gimp (under Graphics), rightclick on it and select properties,
where it says **Command**, change ```
gimp-2.6 %U
```
to ```
env LANGUAGE=en gimp-2.6 %U
```
If you want a different language than English simply change **en** to something else like **fr** or **de**.

I followed your guide. But when i clicked on properties." Nothings happen". 
I'm using u 12.04 with MATE UI. 
Can you help me? 
Thanks

---

### Post by overdrank on 2012-11-29
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

