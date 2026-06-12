---
title: "Is it safe to add a lib32 and where to find it?"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by migla on 2006-10-15
Can I get a 32-bit lib with the same name as a 64-bit lib and put it in another place?


Downloaded static qt opera .deb and installed it. First it said it couldn't find libX11.so.6 so I made a symbolic link in /usr/lib/opera/9.02-20060919.1/ to /usr/lib/libX11.so.6.2.0 (the libX11.so.6 in /usr/lib/ was a symlinc to /usr/lib/libX11.so.6.2.0)

Now it finds it, but says it's "wrong ELF class: ELFCLASS64"

So, can I put a 32-bit lib in the opera or lib32 dir without messing things up and if so, where do I get it?

Or am I barking up the wrong tree here? Is there another, proper way to do this?

---

