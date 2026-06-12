---
title: "Will Beryl updates break my beryl?"
date: 2007-04-26
forum: Apple Intel Users
---

### Post by rscow on 2007-04-26
I have sucessfully installed Beryl, and it is running fine.  I got the code from ubuntu.beryl-project.org feisty.

The HOWTO I followed indicated that the Beryl in the universe repo was not compatible with ATI and the Macbook Pro in general.  So, it suggested that the updates offered by Ubuntu Update Manager NOT be installed.  Because it would break the current installation.

Is this still true?  This HOWTO was written for installation on Edgy, and not Feisty.  So, that data may not be true at this point.  

Anyone have any experience with these updates, or should I leave well enough alone.  I don't want to mess up a good thing.

Thanks,

Roger

Macbook Pro with core duo (first gen)
Feisty Fawn user

---

### Post by sklarsky on 2007-04-26
i believe so.  i got beryl running on my intel imac only after downgrading to 0.2.0.  i know aiglx won't work with the ati cards, but im almost positive xgl + beryl 0.2.1 didn't work which is what the ubuntu repository has.

-j

---

### Post by rscow on 2007-04-26
Just the info I wanted.  Thanks.

I will not upgrade Beryl until info comes out that it is safe.

Roger

---

### Post by ronocdh on 2007-04-27
> **rscow said:**
> Just the info I wanted.  Thanks.

I will not upgrade Beryl until info comes out that it is safe.

Roger
In the meantime, so the Update Manager doesn't nag you, you can use the command **sudo aptitude hold beryl** and that should prevent UM from offering you updates. To remove this later, use **aptitude unhold beryl**.

---

### Post by qpwoeiruty on 2007-04-29
> **ronocdh said:**
> In the meantime, so the Update Manager doesn't nag you, you can use the command **sudo apt-get hold beryl** and that should prevent UM from offering you updates. To remove this later, use **apt-get unhold beryl**.

apt-get doesn't know hold. Try **sudo aptitude hold beryl**

---

### Post by ronocdh on 2007-04-29
> **qpwoeiruty said:**
> apt-get doesn't know hold. Try **sudo aptitude hold beryl**
What a careless mistake! Thank you; the post is revised. =)

---

### Post by S.Peterman on 2007-08-29
When I do sudo aptitude hold beryl it says that the following packages will be held back, but the notification is still there to have them upgraded. Any way around this?

---

### Post by Wittiga on 2007-08-29
Beryl is now called compiz fusion, and thats what you should install.

---

