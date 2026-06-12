---
title: "problem with wvdial"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by gargoyle on 2006-08-08
I am trying to use **wvdial** however it is giving me and error.
I do the following
[LIST=1]
[*]Open terminal window
[*]type in **sudo wvdial**
[*]enter password
[/LIST]
It then returns an error:
*wvdial: error while loading shared libraries: /usr/lib/libconf.xo.4.2: invalid ELF header*

Am I missing a library or is it corrupted?
What do I need to do here to correct this?

---

### Post by zxee on 2006-08-08
You usually need to run > sudo wvdial.conf to set up wvdial although there are exceptions to that. Have you used pppconfig to create an account? I'm presuming that you have a dial up internet account. If there's some other way you're trying to use wvdial then please specify that, and see the link in my signature for help with dial up.

---

