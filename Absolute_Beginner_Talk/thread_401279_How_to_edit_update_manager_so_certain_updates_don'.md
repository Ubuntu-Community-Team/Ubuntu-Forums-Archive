---
title: "How to edit update manager so certain updates don't appear"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by bcrom on 2007-04-04
I recently downgraded my package libdvdcss2 to an older version because the new one didn't work.  Now the update manger is always lit up prompting me to update libdvdcss2.  Is there any way I can edit the manager so it won't prompt for this specific update?

---

### Post by brentoboy on 2007-04-04
What you need to do is called "pinning"

in the debian help, you can look into pinning here:
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)

its topic 3.10 near the bottom of that page.

--

I'd walk you through it, but I haven't done it recently, and I don't want to lead you astray.  But that help file gives thorough instructions.

---

### Post by bcrom on 2007-04-04
Thanks, that worked perfectly.

---

### Post by Irony on 2007-04-04
Better still just go to synaptic and select the package then click package then tick lock version.

This will then pin the selected packages - these pinned version can be viewed by clicking status and selecting pinned.

---

### Post by Roobert on 2007-04-13
> **Irony said:**
> Better still just go to synaptic and select the package then click package then tick lock version.

This will then pin the selected packages - these pinned version can be viewed by clicking status and selecting pinned.

Thanks for the tip, Irony, it worked perfectly.

~ Eric.

---

### Post by Mimsy on 2007-04-13
> **Irony said:**
> Better still just go to synaptic and select the package then click package then tick lock version.

This will then pin the selected packages - these pinned version can be viewed by clicking status and selecting pinned.

That didn't work for me. I tried to stay in a kernel I knew worked, but the update manager kept trying to push the updated one on me. I ended up installing the updates, just to get rid of the annoying reminder, and now I'm working on figuring out how to set the old kernel to the default at boot.

/Mimsy

---

