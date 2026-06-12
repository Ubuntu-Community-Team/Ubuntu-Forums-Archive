---
title: "RealPlayer Install Problem..."
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by sardopsycho on 2006-04-30
I followed the Wiki on how to install RealPlayer 10 - and this is what I got....

chmod +x RealPlayer10GOLD.bin

sudo ./RealPlayer10GOLD.bin

./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

---

### Post by gingermark on 2006-04-30
if you do
'sudo apt-get install libstdc++5 '

first and try again it should work.

But I'd install the .deb file mentioned in the wiki - it's easier to remove later.

EDIT: In fact that is stated on the wiki - if you missed it fair enough, if you're using a different page, I'd recommend this one: [https://wiki.ubuntu.com/RealplayerInstallationMethods](https://wiki.ubuntu.com/RealplayerInstallationMethods)
Not sure there are too many other pages though.

---

### Post by sardopsycho on 2006-04-30
That worked perfectly - Thank You!

---

