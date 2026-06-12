---
title: "My slave hard-drive... And a few other questions."
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by Raavea on 2006-04-27
Okay, so three days ago I installed Ubuntu. I'm getting used to how it works, and I've decided to check on my hard-drives.

 Upon installation, I told Ubuntu to wipe my Master Hard-drive and replace the XP installation that was on it.

 When running on windows, I had a slave hd installled. It didn't have windows on it, it was just used for me to install games on. (Master is 7gb, slave is 20gb - go figure) The relationship ran perfectly in windows.. But, **how on earth do I access my slave hard-drive now? I want to wipe it clean and use it as my pit again.**..

 Another question: I am the head computer in my home network, which is still working, but they can no longer access my shared folder. That makes sense, as it was on windows, and thus no longer exists. I can still access their shared docs, so **how do I make a new shared docs for the network? **We swap files back and forth, though they are still on XP so the type is now limited.

 And one last thing:** What do I install to be able to unrar .rar'd files?**



 Edit: Ark didn't work for my rars, it wanted unrar in my path, or something.. o..O I also found a few things to do with shared folders and the hard-drive, but I don't want to fiddle about with something until I know what I'm doing: Can anyone help?

---

### Post by jazzmuzik on 2006-04-27
[QUOTE=Raavea]Okay, so three days ago I installed Ubuntu. I'm getting used to how it works, and I've decided to check on my hard-drives.

 Upon installation, I told Ubuntu to wipe my Master Hard-drive and replace the XP installation that was on it.

 When running on windows, I had a slave hd installled. It didn't have windows on it, it was just used for me to install games on. (Master is 7gb, slave is 20gb - go figure) The relationship ran perfectly in windows.. But, **how on earth do I access my slave hard-drive now? I want to wipe it clean and use it as my pit again.**..[/quote]

You need to partition and format your second drive. There are instructions to do this on the command line. I'm wondering if it's possible to do with via the GUI...

> Another question: I am the head computer in my home network, which is still working, but they can no longer access my shared folder. That makes sense, as it was on windows, and thus no longer exists. I can still access their shared docs, so **how do I make a new shared docs for the network? **We swap files back and forth, though they are still on XP so the type is now limited.

Use Samba to create/manage windows shares.

> And one last thing:** What do I install to be able to unrar .rar'd files?**

You can install the rar and/or unrar packages via Synaptic. With rar you can create and extract rar archives. For example, to extract: 'rar -e filename.rar' or use 'unrar filename.rar'

---

### Post by Raavea on 2006-04-27
I've looked, searched, searched, and looked again.

 I can't find anything in synaptic called rar or unrar.
Searching archive brings up the same stuff, and the only thing I can see that would work is **Ark,** which didn't work last time I tried it.


 (NB: I did manage to fix whatever I did to the network, so I can access their computer's shared docs again. However, they can't seem to access mine.. o.o It's fine as my hd is the smallest anyhow. ^_^

 I've also managed to format and access the slave. Thanks!)

---

### Post by confused57 on 2006-04-27
Have you enabled Universe & Multiverse repositories?:

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-installing-applications](http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-installing-applications)

If this doesn't help, you can try out Automatix, which will install RAR for you.

---

### Post by Raavea on 2006-04-27
Did that just a moment ago and found it. Thanks so much everyone!

---

### Post by jazzmuzik on 2006-04-27
I can never remember which repository needs to be enabled. From day one I enabled all the repositores and on day two I installed Automatix.

---

