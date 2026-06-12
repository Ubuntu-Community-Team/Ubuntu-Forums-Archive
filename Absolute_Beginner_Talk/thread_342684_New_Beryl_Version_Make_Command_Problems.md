---
title: "New Beryl Version/ Make Command Problems"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Blue_Sky on 2007-01-20
Hi,
Without paying much attention I updated Beryl yesterday. When I logged on this morning Beryl wouldn't start and when I tried using the terminal it crashed my computer. I'm trying to reinstall the 0.1.4 version, but the site only has .tar.bx2 files. I tried to install them using the set of steps below, but I have run into a few problems.

"tar xvjf file.bz2
cd name_of_the_file/
./configure
make
su
make install"

This is the error message I get after "./configure", for the file "beryl-core-0.1.4":

"No package 'xcomposite' found
No package 'xdamage' found
No package 'libstartup-notification-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BERYL_CFLAGS
and BERYL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details."

And this is the error I get after i try "make":
"make: *** No targets specified and no makefile found.  Stop."

So, what am I doing wrong and how can i fix it? Is there any way to install the old files through synaptic or the terminal (as that would be hugely easier for me!)?

Thanks,
Blue

---

### Post by eXisor on 2007-01-20
You seem to have missing dependencies. If you install auto-apt from the repos, you can
```
auto-apt run ./configure
``` 
and it should check the repos for what it needs.

---

### Post by xpod on 2007-01-20
I watched the many issues with the new beryl update the last few days and left it till today.
It`s all worked great although one or two little things dont seem to be working but thats probably just me as usual.

I dont usually pay much attention to the updates etc myself but that was one that i did for a change.
Good luck with it anyway

---

### Post by Blue_Sky on 2007-01-20
i fixed my problem. I found out how to force versions in the synaptic package manager.

Thanks guys.

---

