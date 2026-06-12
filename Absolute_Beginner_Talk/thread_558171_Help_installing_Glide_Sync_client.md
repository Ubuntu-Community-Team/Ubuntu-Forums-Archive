---
title: "Help installing Glide Sync client?"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by Robertjm on 2007-09-23
Hi all.

Has anyone here tried using the Glide Sync flash-based client for syncing your phone or multiple computers?

Its an .rpm format, however, I converted it using Alien to a .deb file. Did the install, but I get an icon on the desktop that is locked. When checking the file properties its only owned by Root.

Next I changed the file properties using chmod 777 to fully available. Unfortunately, I'm getting an error msg of: 

./glidesync: error while loading shared libraries: libQt3Support.so.4: cannot open shared object file: No such file or directory

when trying to run the program.

Anyone have any ideas?

Robert

---

### Post by deadjones on 2008-02-27
while this isnt exactly what you had asked, i had run into similar + other problems getting glide sync working on my gutsy box.   i ran across something that seems to have worked

cd into your /usr/lib directory and do the following:

ln -s libssl.so.0.9.8 libssl.so.6
ln -s libcrypto.so.0.9.8 libcrypto.so.6

or if its 0.9.7 then edit accordingly.  then cd /usr/share/glide and ./glidesync

---

