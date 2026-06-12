---
title: "Does Chmod need sudo or not?"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by ltk5 on 2007-03-18
So, I've been playing with chmod lately. Just a little, but still. I've changed permissions of  some executables (folding@home, and xfractint) to make the able to be executed ;)  The silly question I was wondering about was: Why is it possible that I can chmod +x an executable without being root.
If there's a 'nasty' programme trying to hurt my ubuntu, can it do it? I mean it just chmod's itself, or does he need first to be chmodded and then he can do things. :confused: 

I'm a bit confused, and I hope you've understood my question. Thanks!

---

### Post by meborc on 2007-03-18
you can chmod the files in your /home without sudo as you have permissions to do whatever with these files... but you do not have the permissions to chmod system files without sudo...

---

