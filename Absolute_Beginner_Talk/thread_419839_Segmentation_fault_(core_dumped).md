---
title: "Segmentation fault (core dumped)"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Anicka on 2007-04-23
I just updated to Feisty and I didn't encounter any problems during the update. It boots, X starts, aptitude is working, but otherwise nothing seams to work; less, more, cat, man, emacs and evince are all failing, giving the message "Segmentation fault (core dumped)". I haven't found a good solution, so if you have any ideas, please share them.

---

### Post by leibowitz on 2007-04-23
Check what kernel you are using. And if you have any space left on the root partition. Otherwise I have no idea.

---

### Post by Anicka on 2007-04-23
After purging cpp-4.0, gcc-4.0 and gcc-4.0-base, everything works. They were held back because of one of the programs that I have installed, but after downloading and installing the feisty-adapted versions, life is good. \\:D/

---

### Post by leibowitz on 2007-04-23
That's great.

I was going to tell you to use this **ldd /usr/bin/less** and you would have found that some libraries related to gcc libstdc or something else would be the problem.

But you found that by yourself :-)

---

