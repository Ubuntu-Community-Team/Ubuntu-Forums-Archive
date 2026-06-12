---
title: "Opera 9.0 issue"
date: 2006-07-02
forum: Apple PPC Users
---

### Post by simonium on 2006-07-02
I'm having a problem running Opera 9.0, after aparently succesfully installing it on my 300mhz G3 iBook.  While there will be an icon in the applications internet menu, nothing happens when I click on it.  Earlier versions of Opera wouldn't install on my computer at all, so this is the closest I've come to being able to use a program I've used for years and years.  It's fairly frustrating.

I'd really appreciate any assistance anyone can offer.

Thanks!

---

### Post by evilghost on 2006-07-03
Try running Opera from the terminal and see if it segmentation faults.  If so, it's likely due to a plugin issue.  Opera will use plugins from Firefox and some are not compatible.  When I was using Opera I had to move a few.  I'm away from my Linux box at the moment so hopefully tonight I can give you more information.

---

### Post by simonium on 2006-07-03
Running Opera from Terminal landed me this:

ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.0-20060616.3/opera: error while loading shared libraries: libst dc++.so.5: cannot open shared object file: No such file or directory

Thanks so much for your help.  What does this mean to you?

---

### Post by evilghost on 2006-07-03
The first two are actually 'normal', looks like you're missing libstdc++.

In terminal, type:

```

sudo apt-get install libstdc++5

```

After it installs libstc++5 re-run Opera in the terminal and post any output if Opera fails to load.

---

### Post by simonium on 2006-07-04
Thank you sooo much!  That worked, and Opera does too.  Firefox was like walking through molasses on my little computer, so it's nice to have Opera back.

Now, can I use that code to fix other missing files I might come across in the future?

Thanks again.  Happy fourth!

---

### Post by evilghost on 2006-07-04
Sure, apt is what Debian/Ubuntu uses for the package management system.  apt-get is really a subset of apt for the command-line.  The GUI version is called Synaptic Package Manager.

Happy Independence Day to you as well. :)

---

### Post by Deacon Nikolai on 2006-07-04
:KS Good to know as I planned to install Opera 9.0 too, Thank you and happy Independence Day to you both!

---

### Post by kadymae on 2006-07-15
> **evilghost said:**
> The first two are actually 'normal', looks like you're missing libstdc++.


Bless you!  I've been wrestling with failed Opera installs for 3 weeks now.

Installed this via synaptic and HHJJ! it worked!

---

### Post by RavenOfOdin on 2006-07-15
I had the libstdc problem as well, and I also had to install libqt3-mt.

But I'm running it now and 9.0 quite honestly looks like a job well done on the part of the Opera developers.  I'm not a big fan of some of the clauses in the license agreement that popped up on first run, but I'll keep it around anyway.

---

