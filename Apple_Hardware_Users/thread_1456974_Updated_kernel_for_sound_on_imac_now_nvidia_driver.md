---
title: "Updated kernel for sound on imac now nvidia driver fails"
date: 2010-04-17
forum: Apple Hardware Users
---

### Post by troubleshot on 2010-04-17
I just updated to 2.6.33 kernel and I am using an Intel Mac with ubuntu 9.10 running native. I upgraded because the new kernel has sound working for the imac (at least through headphones). Once the kernel was updated to 2.6.33 the proprietary NVIDIA graphics driver which I had activated through systems -> administration -> hardware drivers is now inactive and will not work. systems -> administration -> hardware drivers says to look in /var/log/jockey.log, here is the last part of that file [http://pastebin.com/FDHVMGTC](http://pastebin.com/FDHVMGTC). PLEASE HELP OUT. I hate using the Mac os on the other partition. I am losing my computer sanity with Mac! Help! Help! I would not have this problem had I the choice on which was bought for my parents.

---

### Post by tom4everitt on 2010-04-18
Hmm, maybe it'd work better in 10.04... :)

---

### Post by alexmurray on 2010-04-18
Looks like the headers package doesn't exist to compile the nvidia driver against. Perhaps try running Update Manager and doing an update first.

---

