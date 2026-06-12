---
title: "checking root file system at startup"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by Theo van Nee on 2006-07-25
Once every 30 (I guess) startup I get the following message during system boot:
checking root file system
	has been mounted 30 times without being checked
	check forced
Does this mean that I have to check something at startup?

---

### Post by philippe_carlo on 2006-07-25
Nope, this is just a sanity check done by the system to keep your file system in shape. No worries, just let it run.

---

### Post by Theo van Nee on 2006-07-25
Thank you,
Regards,
Theo

---

### Post by Bob Unitt on 2006-07-25
> **philippe_carlo said:**
> Nope, this is just a sanity check done by the system to keep your file system in shape. No worries, just let it run.
Can it be deferred ? - I got caught by this when I switched on my machine to receive an urgent e-mail, and had to wait quite a while before I could log-on to read it. IMHO it would be better if ubuntu *asked* before doing this, and gave the user the option to defer the check until the next boot-up instead.

---

### Post by hexion on 2006-08-17
Yes, you can cancel the check, but it's not recomended..

You can better manage the number of reboots to check a system, set that number...

Asuming your partition is hda3 (in example)

- To see the mount count:
> sudo dumpe2fs /dev/hda3|grep count

- To set the actual count to another number (i.e. zero):
> sudo tune2fs -C**0** /dev/hda3
(capital C)

- To set a new max. number of reboots without check (i.e. 40)
> sudo tune2fs -c**40** /dev/hda3

---

### Post by ÄlveKatt on 2006-09-26
I have a laptop that I use in the classroom. Thus I am interested in starting this thing manually. That way I can do it now and then at home, and be sure that I won't have to wait for the check to be done when I start up my laptop to do work in the classroom. 

That check is near enough catastrophic if it runs in class when you start the laptop because you have gotten a writing assignment to be made in ten minutes...

So, how do I run this check manually?

---

### Post by Toufik on 2006-09-26
You can always press CTRL+C to abort the check...

---

