---
title: "Need help restoring"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by Naddiseo on 2005-11-30
Hello
I was tring to install firefox manually last night,
 and in my tired state I did something really really bad :(

I "cd" to the folder on my desktop that had firefox in it and typed

mv /* /usr/lib/mozilla-firefox/

I thought that this would move the contents of the current folder there..

Seems not, It moved almost every file into that folder, and now 
I cannot boot into it, and I don't know how to mount it from
a rescue CD (Which I'm using to type this)

Can anybody help me restore my computer from this CD? with having to
install again.

Thanks.

---

### Post by gord on 2005-11-30
you might have to do some messing about to get it to work again but to remount it you just need to know what partition its on, you'll also need to create the directory to where its mounted ("sudo mkdir /tempmount" or whatever)

if your linux partition is hda1 then you would do the following.
```
 sudo mount /dev/hda1 /tempmount 
```

---

