---
title: "quod libet id3v2.3?"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by gantengx on 2007-06-18
Is it possible for quod libet to use id3v2.3 for default id3? I don't like id3v2.4 because not many software uses it (or implements it properly).

I had to convert my id3 to v2.3 so i can use it in itunes, for some reason itunes doesn't really support id3v2.4, i even changed the encoding to utf16-le, utf16-be while using v2.4, but itunes just doesn't detect it.

So i really appreciate if anyone can show me how to make quod libet/ex falso uses id3v2.3 as the default id3..

Thanks!

---

### Post by d_b on 2007-06-25
I'm also looking for the same thing.   QuodLibet is my favorite player, and the tag editing is very nicely integrated.   Unfortunately, my Sony Ericson w810i will only read ID3v2.3 tags, so I've had to resort to using EasyTag until I can find a fix.

d.

---

### Post by bluegray on 2007-06-26
I was [testing different id3 tags with my W850]("http://blog.floatinginspace.za.org/technical/2007/06/26/w850i-utf-8-and-id3v24-bug/") and it might be the UTF-8 encoding that is your problem. Quod libet does use UTF-8 in it's tags, so it's worth a try. As for itunes I have no idea...

I don' t think you will be able to write v2.3 tags in quodlibet - the developers are quite gung ho for 2.4. But you can go hack the code yourself ;)

---

