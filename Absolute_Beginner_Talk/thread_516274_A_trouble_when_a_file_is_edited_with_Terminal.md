---
title: "A trouble when a file is edited with Terminal"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by Chalaco on 2007-08-03
Hi everyone,
 I have been using Fedora LInux in the last 3 years but now I would like to surf in the Ubuntu sea.  I always edit a program code or whatever with vi (by means of Terminal), I can do it with Ubuntu. After open a file with vi, I press the key I, in order to insert something, and I can write, but the words INSERT should not appear at the bottom of the Terminal's window (as usual in Fedora), When I am editing a text with vi and I press UP and DOWN cursor key appears some characters and the cursor go to the next line. I tried with different keyboard options without any success.
 I hope that somebody can provide me a solution
 Regards,

---

### Post by apswartz on 2007-08-03
Try vim instead of vi -- for some reason there is a difference even though the same program is called.

---

### Post by girishv on 2007-08-03
If you call vim as vi, it will not set the nocompatible mode and will try to act like actual vi. Wither put a line in .vimrc 
set nocompatible

or alias vi to vim

No idea about how to remove INSERT at the bottom of the vim window :(

Girish

---

### Post by apswartz on 2007-08-03
> **girishv said:**
> No idea about how to remove INSERT at the bottom of the vim window

Actually, I believe he is wondering why the word INSERT does NOT appear. I just tried it as he described and he is right, the word does not appear. But if you call the program as vim it works as expected (for me at least).

---

### Post by p_quarles on 2007-08-03
Just one thing to add: the default installation of Vim in Ubuntu is not fully featured. To fix this:
```
sudo apt-get install vim-full
```

---

### Post by apswartz on 2007-08-03
> **p_quarles said:**
> Just one thing to add: the default installation of Vim in Ubuntu is not fully featured. 

Wow, I didn't realize that. I just did the vim-full install and it fixed the vi INSERT situation.
Thanks, that should make this thread solved.

---

