---
title: "Group resize and Opera"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Maupertus on 2007-06-01
Heya guys,

it's been a while, but then, I've just been lurking and didn't need any help, and I'm not really the most experienced user, although I have posted some tips on Xubuntu (gotta love light weight usage)

However, I now have two questions:
Does anybody know a good program with which to resize my images (in this case, pictures from my camera) en groupe?

I'm downloading Opera via the Opera website, but is it possible to download opera and it's updates via the repositories in (X) ubuntu 7.04?

Thanks heaps,

Maupertus

---

### Post by kerry_s on 2007-06-01
Opera repo->

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) unstable non-free 

Key->

gpg --keyserver subkeys.pgp.net --recv-key 033431536A423791
sudo gpg --armor --export 033431536A423791| sudo apt-key add -

---

