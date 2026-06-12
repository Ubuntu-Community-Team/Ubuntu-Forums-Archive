---
title: "killall esd? ....."
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by faeros on 2005-10-08
is that the only way to get sound on firefox?

f:confused:

---

### Post by Mustard on 2005-10-08
I imagine sometimes it is, depending on how well your sound is working.  What configuration have you done with regards to your sound prior to discovering this problem?

---

### Post by faeros on 2005-10-08
Just installed ubuntu.  there were about 500 updates, a few of which were for firefox.  I had problems with those upgrades, but worked them out.  I have done nothing for the sound except installing pluggins for firefox.  I do have system sound, just not with java or flash.

---

### Post by Wolki on 2005-10-08
Try this:

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

---

