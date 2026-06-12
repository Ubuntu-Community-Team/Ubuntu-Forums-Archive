---
title: "my abiword crashed"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by 2wins on 2007-09-18
today i just remove OOo and installed abiword, after installation, the item appeared in the menu,
but when i click to start, the abiword just splashed and exit, when i start it in term, it says:
abiword aborted (core dumped), how to correct it?

also a problem in my totem player, when i use it to play rm and rmvb files, it searches decoders, but after i install the plugins, totem works, but no video, just sound, why? i thought of changing the plugins, but the search results only display only one plugin, which is ranked one star, not so popular, ah?

---

### Post by misfitpierce on 2007-09-18
Can try easyUbuntu for codecs and such found in my signature. useful program that auto installs codecs from repo's.

As for abiword... make sure you installed abiword-common as well from repo's.

[http://archive.ubuntu.com/ubuntu/pool/main/a/abiword/abiword_2.4.6-1.1ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/abiword/abiword_2.4.6-1.1ubuntu2_i386.deb)

I installed that package... so do this

terminal: sudo apt-get remove abiword

then install that package which should install dependancies as well and it worked for me. Goodluck :)

---

