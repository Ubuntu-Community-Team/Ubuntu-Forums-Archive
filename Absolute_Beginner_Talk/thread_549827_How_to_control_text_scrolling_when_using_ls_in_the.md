---
title: "How to control text scrolling when using ls in the shell"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by anotherbigal on 2007-09-13
Hi.
Can anyone advise on how to control the output of ls? I am looking around to see the workings of the shell in Feisty but when I type "ls" some directories a lot of info disappears off the top of the screen. Of course the up arrow only reproduces the previous commands while page up has no effect whatsoever. Tried "ls --help" but a lot of the output from that scrolls off the top of the screen as well! A simple question I know but I am completely flummoxed. Can't find any posts about this either.
  BigAl

---

### Post by BlackMeTaL on 2007-09-13
You can use Shift-PageUp to scroll up and Shift-PageDown to scroll down.
Or you could pipe the output to less for instance, like this:
ls | less

---

### Post by hyper_ch on 2007-09-13
or you could save the output to a file:

```

ls > output.txt

```

---

### Post by anotherbigal on 2007-09-13
I knew it would be simple. That is probably the only thing I hadn't tried. Thank you
BigAl

---

