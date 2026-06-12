---
title: "Nautilus and symbolic links"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by WelshChris on 2007-04-24
In a terminal, I can create a symbolic link to a directory on a different filesystem on the desktop, i.e.

[CODE] 
ln -s /media/windows/text text 
[CODE]

Nautilus recognizes this as a link, and allows me to navigate as expected.

If I want to delete the link, however, Nautilus complains about the link being on a different filesystem.  

I can delete as normal using a terminal or Xfe.

Any reasons for this?

---

### Post by nanotube on 2007-04-25
hmm, this sounds like it may be a bug... you should post a bug on [http://lauchpad.net/ubuntu](http://lauchpad.net/ubuntu), and see what comes out of it.

---

