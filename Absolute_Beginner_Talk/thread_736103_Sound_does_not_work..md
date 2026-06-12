---
title: "Sound does not work."
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Vandorin on 2008-03-26
My sound does not work at all on ubuntu, is there something i can do for it to recognize my sound driver?


-Thanks.

---

### Post by c-ron on 2008-03-26
Hi,
Check out this awesome thread.
Comprehensive Sound Problem Solutions Guide v0.5e:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by superprash2003 on 2008-03-26
hope this works for u 
[http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by oedha on 2008-03-26
what is your sound card ?
you can check from terminal by typing :==> lspci ( then look at multimedia controller )
or
sudo lshw -short -C multimedia

---

### Post by northern lights on 2008-03-26
or ```
cat /proc/asound/cards
```(gives you nothing but your sound devices, so no looking around)

--> anyways, whatever problem you have, post it with specs...

---

