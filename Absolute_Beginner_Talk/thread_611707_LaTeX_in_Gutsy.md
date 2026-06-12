---
title: "LaTeX in Gutsy"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-11-13
Hello all.
I installed Ubuntu Gutsy and texlive-base and tetex-base. I used to be happy with the three packages tetex-base, tetex-extra and tetex-nonfree in Feisty, but I understand that the story is somewhat stilted in Gutsy. 

I tell you what I need: I mean, I need these in \usepackage:
[LIST=1]
[*]mathrsfs
[*]txfonts
[*]wasysym
[*]graphicx
[*]graphics
[/LIST]
and those others which a mathematician most often needs in his work.

What packages should I install now? tetex-extra is quite large! I am now installing (ie, downloading) tetex-src. But I'm sure I will need to install other packages as well. Why is the change? 

Okay, let's talk less as to why the change is; but please tell me which packages would be meeting my needs?

---

### Post by sauravbhaumik on 2007-11-14
None cared to help me!
Okay, I have endured a long wait sitting on the chair before my computer and ended up at last with tetex-extra which is near 153MB. With it I have downloaded more than 300MB for LaTeX. So I would suggest that anyone that has Gutsy should not waste time with texlive-latex-extra and the like, but instead, should straightforwardly install tetex-extra.

---

### Post by hugmenot on 2007-11-14
Patience, my friend. Installing both Tex Live and TeTeX is complete duplication and redundant.
The chunky packaging of the TeX distributions is unfortunate but we have to live with it for now. A tip: If you want to find out where certain files you need are packaged you can use the web interface at [packages.ubuntu.com]("http://packages.ubuntu.com"). There&#8217;s a file search field down on the page. So if you enter e.g. "txfonts.sty" there you will get the answer "texlive-fonts-recommended".
Et cetera.
So, the big space waster is your having both of the available distros. I would purge all of TeTeX, it is more or less obsolete.

BTW, I hand installed "mpm", the package manager of MikTeX, to pull single packages into my personal texmf root. It also updates these packages. Building this takes a while though.

---

### Post by yellowbread on 2007-11-14
Its not that nobody cared to help, there just aren't too many here that use or have even heard of TeX. hugmenot is right, TeTeX is obsolete. Use texlive instead.

---

### Post by sauravbhaumik on 2007-11-14
Thanks for replies.
I will try to learn how to figure out the correct packages.

---

### Post by yellowbread on 2007-11-14
Is there a reason you want to use TeTeX instead of texlive? All the packages you list are in the default texlive distribution.

---

### Post by sauravbhaumik on 2007-11-14
> **yellowbread said:**
> Is there a reason you want to use TeTeX instead of texlive? All the packages you list are in the default texlive distribution.

There is no reason other than that I, having installed some texlive packages in vain, was frustrated so much, and  felt a little disappointed when (unlike other threads in this section) I spent several hours without a reply to my question. Indeed I wasted much space - and that might be attributed to my own ignorance and impatience; I should have searched out the appropriate packages myself in [http://packages.ubuntu.com](http://packages.ubuntu.com).

There are many changes in the new repositories of Ubuntu, the Gutsy packages are quite alien to one who has just installed Gutsy, especially to one with slender homework.

---

### Post by sauravbhaumik on 2007-11-14
I withdraw the suggestion previously I gave. 
Rather, one should be careful enough about selecting packages to be installed. Less action and more knowledgebase should have been there.

---

