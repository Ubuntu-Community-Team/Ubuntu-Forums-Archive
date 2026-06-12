---
title: "New User Needs Some Quick RAR Help"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by Knapman on 2007-09-26
Quick hello to everyone.

Anyways,

I installed Ubuntu on my laptop, its sleek and sexy , love it.  Anyways I managed to install KTorrent using the easy built in installer thing.  I went to unrar my tv show and it didnt work.  I tried installing all 3 of the Ubuntu recommended Archivers, which claim to have RAR support, but I was not able to Un Rar my tv show.  I googled a bit, and tried some things, but Im too new.  I figured Id post here.  Can someone please help me?  

Thanks in advance,

Neil

---

### Post by Knapman on 2007-09-26
Thanks to Qpieus from another thread, I was able to figure it out:

"yeah, those are not zip files. they are rar files. To unpack, install unrar:

sudo apt-get install unrar

After installing you install it, you should be able to right click on the first file (it ends in ".rar") and see a selection for extract.

Note that some rar files made with a newer version of rar have a different filename pattern - they are filename.part01.rar, filename.part02.rar, etc. The files you have look to be the older filename pattern. The first file is filename.rar, the second part is filename.r00, the third is filename.r01, etc."


:)

---

