---
title: "[SOLVED] How to set K3b as default app for blank CD/DVD?"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by Prodromoi on 2007-12-23
At the moment when I insert a blank disk, the default Nautilus burner app pops up.  I'm had only limited success with this, but am very impressed by K3b which I find much more reliable.

How can I change my default so that K3b is the preferred application for blank CD/DVDs?

Thanks in anticipation.

---

### Post by LaRoza on 2007-12-23
System->Preferences->Removable Drives and Media Preferences

---

### Post by Prodromoi on 2007-12-23
> **LaRoza said:**
> System->Preferences->Removable Drives and Media Preferences

Ah, that was my first thought.  However when I looked there I wasn't able to work out where to browse to or what to put in the field for the program.  (Just a newbie here, don't forget!)

---

### Post by LaRoza on 2007-12-23
> **Prodromoi said:**
> Ah, that was my first thought.  However when I looked there I wasn't able to work out where to browse to or what to put in the field for the program.  (Just a newbie here, don't forget!)

Under Storage, Blank CD and DVD Disks, put in the field for Data CD's:

```

k3b --datacd 

```

For Audio CD's:

```

k3b --audiocd

```

You might want to record the current settings if this is not what you want.

(I just read the man pages for the above)

---

### Post by Prodromoi on 2007-12-23
Thanks, that's exactly what I needed.  Works perfectly.

Having just read the man page, I understand what's going on.  However without your suggestion I don't think I would have worked out the answer from just looking at the man page myself.

'Tis a learning process!

---

### Post by LaRoza on 2007-12-23
> **Prodromoi said:**
> Thanks, that's exactly what I needed.  Works perfectly.

Having just read the man page, I understand what's going on.  However without your suggestion I don't think I would have worked out the answer from just looking at the man page myself.

'Tis a learning process!

No problem! (Mark the thread as solved, under "Thread Tools")

The man pages take a little getting used to, so I don't expect people to understand them without a little experience. I ran the commands to see what they would do first, before posting them.

Have fun learning! I certainly do.

---

### Post by Prodromoi on 2007-12-23
> **LaRoza said:**
> No problem! (Mark the thread as solved, under "Thread Tools")

Aha, beat you to it.  That bit I've already learned!

---

### Post by LaRoza on 2007-12-23
> **Prodromoi said:**
> Aha, beat you to it.  That bit I've already learned!

Now send the required free (20 USC) to my PayPal account, I assume you learned that by now.

(jk)

---

### Post by Prodromoi on 2007-12-23
> **LaRoza said:**
> I assume you learned that by now.

(jk)

And what not to do, too!

(Although to be honest, that would be a very reasonable fee!)

---

### Post by LaRoza on 2007-12-23
> **Prodromoi said:**
> 
(Although to be honest, that would be a very reasonable fee!)

No it wouldn't be.

I like doing this (helping people), and getting paid would ruin it.

Just pass on what you receive!

---

