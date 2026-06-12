---
title: "Possible bug need help verifying"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Jimmmmy on 2007-05-29
Hi there, im quite a noob at linux been about 2 weeks since installed it. 

I was doing a cat on a file and I got a whole page full of messed up characters, the terminal window title changed characters too and the prompt changed also..

would this be classified as a bug?

---

### Post by Happy_Man on 2007-05-29
Depends on the file..... what was it?

---

### Post by tgm4883 on 2007-05-29
It needs to be repeatable and verifiable by other people.  If you could list steps to produce this "bug" and could reproduce it, and someone else could verify it.

---

### Post by lambros on 2007-05-29
Strange as it may seem, this isn't actually a bug :-)  Both the 'cat' program and your terminal are behaving as designed and intended.  It all boils down to the fact that you're feeding "random" data to your terminal.  Many terminal emulators have advanced capabilities that go beyond just displaying letters and numbers on the screen.  If you feed it "random" data, you'll find very occasionally that a sequence of bytes will happen to trigger one of these capabilities.

If you're unlucky, you can sometimes end up with an unusable terminal, because it displays gobbledegook whenever you type stuff in.  To get back to normal, you can use the command
```
reset
```
to cause the terminal's internal state to be reset.

Lambros

---

### Post by Jimmmmy on 2007-05-31
Oh right, Thanks for the info Lambros.

---

