---
title: "unrar -e"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Frank_F on 2008-04-01
Hello


I try using this command and it says "bash unar command not found"

I tried to change my .profile, but I dont seem to have one.


Thanks

---

### Post by TeoBigusGeekus on 2008-04-01
Have you installed rar with synaptic?
If so, then just double click your rar archive and extract its contents through GUI.

---

### Post by t0p on 2008-04-01
**unrar** isn't installed by default.  But it is available in the repos, so you can install it via **System > Administration > Synaptic**.  It's in the **Multiverse** repos.  And, if you're a Free software junkie, there's **unrar-free** in the **Universe** repos.  (But unrar-free can't handle some rar-3.0 archives).

---

### Post by Frank_F on 2008-04-01
actually I installed it via the command line and not Synaptic.

maybe i will try that.

thanks

---

### Post by zvacet on 2008-04-01
Right click on package and select **unpack here**.

---

### Post by Nameless_one on 2008-04-01
By the way be aware that e doesn't preserve the file tree as it is inside the archive. You should use x for that (also, the command is actually unrar e, not -e). Check the manpage when you install it.

---

### Post by Frank_F on 2008-04-01
thanks I will give it a try

---

