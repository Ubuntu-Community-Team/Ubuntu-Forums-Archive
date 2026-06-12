---
title: "Tried to display on TV..."
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by JJFO on 2007-07-25
I tried to get ubuntu to display on my TV by following these directions, [https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut)

After doing that I got stuck with a tiny corner on my screen on my TV and nothing on my monitor and I'm am unable to even log in because I can't click on the username field.

So 1. How do I get xorg.conf back to the way it was before
and 2. How did some of you guys get the display on TV

thanks!

---

### Post by wolfen69 on 2007-07-25
it takes a little energy to do it.

---

### Post by JJFO on 2007-07-26
What do you mean a little energy? I don't care so much about getting the TV display working anymore, I just want to get my ubuntu working again. Do you know how I can change my xorg.conf back to what I backed up?

---

### Post by Motoxrdude on 2007-07-26
Press control+alt+backspace. Then enter
```
sudo dpkg-reconfigure xserver-xorg
```
Now answer to the best of your knowledge.

---

