---
title: "what is pdflush?"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-02-08
do i need it/ if not, would i benefit in getting rid of it?

what about apache2? (i've got a feeling i need this one, yes?)

---

### Post by Rinzwind on 2006-02-08
Apache2: only if you want to host websites (either on your own network or on the web). Otherwise you don't need it.

pdflush is responsible for periodically flushing dirty pages in order to ensure that there is enough free memory and to save users from losing data when their computer crashes and things are still in the buffer cache instead of on disk.

So you might want this ;)

---

### Post by fuscia on 2006-02-08
cool. thanks.

---

