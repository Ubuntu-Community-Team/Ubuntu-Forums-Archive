---
title: "[SOLVED] Purging residual config"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by baracuda68 on 2008-03-23
Hi.
I have a long list of residual config files( alot of KDE4 stuff that I don't use) that I wish to delete.

[B]Is there a way to, in synaptic, to select all, then check all config files at once, instead of tediously checking each one for removal at a time.
[/B]
I have tried apt-get autoremove with no avail.
                    apt-get autoclean     with no avail.
                    apt-get purge           with no avail.

I looked in Adept, but didn't see any option.

What'd you think?

---

### Post by mikeyphi on 2008-03-23
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

That might be what you are looking for!

---

### Post by baracuda68 on 2008-03-23
Thanks, Mikeyphi, though informative, that page really didn't help,unless I overlooked something. I guess the issue here is how to mass-select **all **of the residual conf files in Synaptic instead of selecting one at a time.
 or another alternative.

---

### Post by forestpixie on 2008-03-23
do you not have the status tab in synaptic - where those all those with residual configs are grouped together

---

### Post by baracuda68 on 2008-03-23
Yes I do, but I can't select the whole group at once.
I have to check each item to "completely remove". When you have alot of items to remove, it is tedious and time consuming.I tried to select more than 1 item, but it only highlights 1 at a time.

---

### Post by mocoloco on 2008-03-23
I can select the first item, scroll to the bottom, then hold SHIFT and select the last item, that highlights them all.  Then right-click any item and click "Mark for complete removal".  If there are a lot of packages in the list it takes a bit but it will mark them all and then you can apply the change.

---

### Post by baracuda68 on 2008-03-23
> **mocoloco said:**
> I can select the first item, scroll to the bottom, then hold SHIFT and select the last item, that highlights them all.  Then right-click any item and click "Mark for complete removal".  If there are a lot of packages in the list it takes a bit but it will mark them all and then you can apply the change.

Yes this worked. Thanks! I tried this before, but I guess I was impatient and it did not respond as quickly as I thought, so I gave up.
But it did work.

[SOLVED]!

---

