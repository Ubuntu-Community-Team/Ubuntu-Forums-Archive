---
title: "Help with moving &quot;programcatalog&quot;"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by Dantu on 2006-08-24
Before I installed Ubuntu I read about how to partition the HD on Psychocats webpage. He recommended like this (in my case with dualboot):

Partitions.
Windows (NTFS)
Ubuntu system (Ext3)
Files and /HOME
Swap

I also have a NTFS partition for "My documents" and such.

What I didn't know was that the "programcatalog" (or what's it called, bin or user...) would end up on the Ubuntu system partition, which in my case is only 8gb!
Hmm, not much space for additional programs...

How do I move the catalog(s)?

Secondly, I'm wondering if someone could explain in Newbie-tongue how the programinstalling works and where they go? 'Cause I'm not really sure about any of that.

regards
Dantu

---

### Post by TrendyDark on 2006-08-24
Programs install to various places, from what I understand, depending on if they are for that user or globally available.

I have a question for you though, did you make the File/home folder partition rather large?

---

### Post by Dantu on 2006-08-24
the file/home is 20 gb

---

### Post by Marsolin on 2006-08-24
8GB for your main partition should be plenty if /home is on a 20GB one. Most of the applications you install will primarily end up in /usr, but files will be spread over many different directories.

To understand where a package is being installed you can use Synaptic to find out. Once you open Synaptic, select a package, the Properties button, and then installed files.

Typically core executable system files go in the /bin directory, with other application executables in /usr/bin. A program's default configuration files typically go in /etc, but any changes you make would be stored under /home/username, with username being whatever you log in as.

I hope this helps. It's not a complete explanation, but I think it covers the key points.

---

### Post by Dantu on 2006-08-24
A thought just hit me *Ouch*

Is it so that I don't really need to know where the files for a certain program are "physically"?
Because I should use "Add & Remove"?

But how do I install other programs than those in the "Add" list?

And how do i practically use Synapsis?

Sorry for all the quests...

---

### Post by Dantu on 2006-08-25
*Bump*

---

