---
title: "[SOLVED] Can't configure &amp;amp; compile ettercap"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by hazardgreen on 2008-01-08
I want to compile ettercap from source because the one included in ubuntu packages does not have GTK support.
After i run ./configure it finishes with :
Checking for required libraries...
"
checking for library containing gethostbyname... none required
checking for library containing socket... none required
checking for library containing poll... none required
checking for library containing gzopen... no
configure: error: not found.

"

what can be the problem:confused::confused:

(i have build-essential installed)](*,)

---

### Post by RomeReactor on 2008-01-08
Hi. Try installing zlib:
```
sudo apt-get install zlib1g zlib1g-dev
```

---

### Post by hazardgreen on 2008-01-08
solved the first dependence
but after installing some more packages:

"
configure: error: Package requirements (gtk+-2.0 >= 2.0.0 pango >= 1.0 atk >= 1.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the GTK_CFLAGS and GTK_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
"

i think ive them installed ( i've installed the $-devs too)
thanks for the fast help
feel soo n00b now:oops::frown:

---

### Post by p_quarles on 2008-01-08
This may fix it:
```
sudo apt-get build-dep ettercap && sudo apt-get install build-essential
```

---

### Post by hazardgreen on 2008-01-08
thanks a lot:)
(build-dep ... 'ill never forget:))

SOLVED

---

### Post by p_quarles on 2008-01-08
No sweat. Just remember to mark the thread itself as SOLVED (using the 
"thread tools" button at the top of the page).

BTW: noticed the "I have build-essential installed" part only after I posted. Sorry to be redundant. ;)

---

