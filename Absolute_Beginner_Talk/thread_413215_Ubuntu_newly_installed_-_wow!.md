---
title: "Ubuntu newly installed - wow!"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Cheese Sandwich on 2007-04-18
I'm a new Ubuntu user, and new to home linux computing (though I use Linux & Solaris at work). So I just installed the Ubuntu 6.10 download here on my old eMachine, and I must say it was completely smooth and problem free. I took a little getting used to (for example - where did my minimized windows go??), but otherwise it was as painless as can be. It auto-recognized everything, including my external USB drive (WD passport).

BTW, I ran update manager & downloaded/installed a ton of updates. Does this mean I now have the new release (7.04)? If not, will another run of the update manager after the official release install all the 7.04 features, or is that a completely new install?

Anyways, it's great to be here on planet Ubuntu. 8) I'd venture to say this OS is ready for primetime mass-marketing, unfortunately not many computer dealers sell Ubuntu-installed machines. :-?

---

### Post by Cheese Sandwich on 2007-04-18
One other question - I like to use tcsh in terminal windows, but it doesn't appear to be available in Ubuntu terminals - anyway to get this shell? Thanks...

---

### Post by shae on 2007-04-18
To upgrade between releases you need to run the upgrade manager.

In a couple days (to avoid the first day repo rush) run in terminal

gksu "update-manager -c"

This should update you to 7.04.  Back up any important data in case something goes wrong and keep your 6.10 disk handy just in case.  

Updating will take a little time as it downloads the updates.  If you have problems please feel free to post them on UF.

---

### Post by freebird54 on 2007-04-19
It is in the repositories if you want to use it.  Open up System->Administration->Synaptic Package Manager - choose Search - enter tcsh , mark it for installation - Install

Should not be a problem  ;)

---

