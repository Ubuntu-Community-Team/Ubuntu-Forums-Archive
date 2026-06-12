---
title: "[SOLVED] trying to install wine on a presario v2000"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2007-12-01
The other day I was able to install Wine on my other laptop but when I attempted it on this computer it did not seem to work.

I went here: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Once there I opened up terminal and pasted this:

> wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

After that I entered:

> sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

There were not error messages but the whole process was shorter than I remember from before. Anyway, once I finished I tried to find Wine under the applications dropdown menu. When I didn't see it I searched for it in the packet manager.

Obviously I am doing something wrong. I will be grateful for any help.

---

### Post by boriquajake on 2007-12-01
I should also add that even though on my other computer I seem to have been able to succesfully install Wine I have yet to be successful in installing and running any .exe files so I am not out of the woods even if I can get Wine intalled.

---

### Post by overdrank on 2007-12-01
> **boriquajake said:**
> The other day I was able to install Wine on my other laptop but when I attempted it on this computer it did not seem to work.

I went here: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Once there I opened up terminal and pasted this:



After that I entered:



There were not error messages but the whole process was shorter than I remember from before. Anyway, once I finished I tried to find Wine under the applications dropdown menu. When I didn't see it I searched for it in the packet manager.

Obviously I am doing something wrong. I will be grateful for any help.

Hi and  you may want to enable your repos. You can add repos under system, administration, software sources. The ubuntu software and updates tab. Hope this helps and good luck!

---

### Post by boriquajake on 2007-12-01
> **overdrank said:**
> Hi and  you may want to enable your repos. You can add repos under system, administration, software sources. The ubuntu software and updates tab. Hope this helps and good luck!

I opened that up and it looks like I have everything that can be checked is checked. The only thing I do not have approved is Gutsy proposed stuff. (I am not bright enough to handle betas :) )

---

### Post by boriquajake on 2007-12-01
For the love of all that is holy! I went to the site for IEs 4 Linux and followed the instructions there to download IE. Anyway, those instructions included much clearer and more helpful instructions for downloading and installing Wine than the instrucions on Wine's own site! (at least I found them to be better) Now even though there is much that I do not understand about Wine it is freaking working. That was awesome.

---

