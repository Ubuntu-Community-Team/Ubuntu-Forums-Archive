---
title: "Windows Fonts...on Linux.."
date: 2005-10-13
forum: Absolute Beginner Talk
---

### Post by Lord Illidan on 2005-10-13
Hi everybody...
I am about to install Linux on my sister's pc.. However, she wants to use the fonts which she has downloaded for Windows from the web in open office. Is this possible under Ubuntu/Linux? By fonts I mean external fonts, not arial, etc...

10x..

---

### Post by mcduck on 2005-10-13
yes, it's possible. In her home directory is directory called .fonts (all files&directories with a . in the beginning are hidden, select 'view' and 'show hidden files' in nautilus). Just put all those fonts in there and she can use them.

If there are many users on same computer, you can instead put those fonts in /usr/share/fonts/truetype/ so that all users can use them.

---

### Post by TristanMike on 2005-10-13
Hmmmmm....I don't seem to have the ./fonts directory, any reason why I don't have it?

---

### Post by mostwanted on 2005-10-13
Allow Nautilus to view hidden files first or create the directory if it really *is* missing.

---

### Post by wylfing on 2005-10-13
Be careful with those slashes, they're dangerous! It's not "./fonts" it's "~/.fonts". Open up a Nautilus window, type Ctrl-L, and type "~/.fonts" into the box. If it says it couldn't find that place, go ahead and make the directory yourself. Dump all your fonts in there. You might need to log out and log back in again to see all the fonts.

---

