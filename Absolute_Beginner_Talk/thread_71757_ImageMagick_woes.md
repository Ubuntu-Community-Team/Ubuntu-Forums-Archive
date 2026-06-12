---
title: "ImageMagick woes"
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by TKDonut on 2005-10-04
I'm a new user to Linux (previously a windows user) just recently installed Ubuntu, currently i'm learning Haskell and I need the ImageMagick utility to complete my latest assignment, however whenever I try to call on ImageMagick i recieve the error,

"display : X Window library is not available."

This is leading me to beleve that i've got ImageMagick installed incorrectly, as I foolishly did not know about packages ect and i was trying to install it from source.

Much obliged if anyone can help me out.

Using EMACS as a text editor and gHCI as a compiler,

---

### Post by SilentCacophony on 2005-10-04
I'm running with Breezy, but hopefully this will still work. You could try:

**sudo apt-get install libmagick6**

which is listed as the only dependency for imagemagick on my setup. libmagick6 has several dependencies and will install several other packages if they're not there.

Since you built it from source, it would depend on the version being similar to that which is in the repositories, though.

---

