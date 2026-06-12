---
title: "How do I install .bz2 files?"
date: 2005-10-07
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2005-10-07
I just downloaded the latest kernel patch  (patch-2.6.13.3) but its a txt file and I don't know what i am supose to do with it.
I would have installed it from synaptic but its not there.
Is this even worth installing?

Thanks again from the kind of stupid and ovbious questions.

---

### Post by mlomker on 2005-10-07
There's nothing wrong with the question.  The answer, though, is that you can't apply a kernel patch to a Ubuntu kernel because they are already patched by the Ubuntu developers.  The best thing to do is just to wait for the update to show up in Synaptic.

Patches like that can only be applied to previously unpatched kernel source that was downloaded from kernel.org.  People that build custom kernels could use it.

It is applied by changing to the source directory and issuing this command:

```

bzcat patchname.bz2 | patch -p1

```

---

### Post by nitricacid on 2005-10-07
Sweet, thanks for the enlightenment.

---

### Post by wylfing on 2005-10-07
To expound on this a little further: As long as you don't turn off automatic updates, your system will check for new kernel versions all by itself. All you have to do is install them when it asks you to. If you are using Breezy, a nice little help balloon will pop up informing you that updates are available. Otherwise, just look for the little red icon in your taskbar.

---

### Post by nitricacid on 2005-10-07
For got to askthis. 
Would it help at all if i installed any of the patches that apear in Synaptic?

---

