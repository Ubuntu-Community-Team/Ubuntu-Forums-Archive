---
title: "Updates - can I refuse?"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by jnorris235 on 2007-12-03
Because when I installed Ubuntu, and partitioned, it wouldn't recognise my whole disc (80gb), and just cos I want to anyway - I keep on my installation only those things I use.

So, is there any way to stop Apt reminding me constantly about updates that I don't want - such as all these current language updates in forty three languages (just the english one will do nicely). And also Evolution and others which I don't use?

The question is about the Aptsolutely marvellous update system - can it be adapted to ones needs and wants?

---

### Post by Vadi on 2007-12-03
Of course. System - Administration - Software Sources, click on the updates tab, and select what's best for you :)

---

### Post by lamalex on 2007-12-03
I think what you're looking for is in synaptic. Find the packages you don't want to update, then go to
Package > Lock version for each one, and it will not update unless you explicitly tell it to. Hope that answers your question.

---

### Post by jnorris235 on 2008-03-02
Very belatedly saw this - thank you!!
I have completely uninstalled Evolution and have locked it then at that.

Hopefully now I will get no more updates (no offence - I just use Gmail online).

I then tried to delete all the Evolution packages that are listed after it, but it warned me that it would then delete Ubuntu-desktop.
Talk about sulking!! 

I can also do this with all those Open Office langauage packs that I have no need for.
Thanks.

---

### Post by julian67 on 2008-03-02
> **jnorris235 said:**
> Very belatedly saw this - thank you!!
I have completely uninstalled Evolution and have locked it then at that.

Hopefully now I will get no more updates (no offence - I just use Gmail online).

I then tried to delete all the Evolution packages that are listed after it, but it warned me that it would then delete Ubuntu-desktop.
Talk about sulking!! 

I can also do this with all those Open Office langauage packs that I have no need for.
Thanks.

ubuntu-desktop is only a meta-package and can be safely removed. No applications will be affected.

---

