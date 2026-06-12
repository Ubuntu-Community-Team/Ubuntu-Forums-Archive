---
title: "Vim Latex-Suite"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Dougie187 on 2008-02-13
Hey guys, So I am having an issue with vim-latexsuite. I read through all related threads and Didn't get an answer to my problem. Soooo im posting a new one I also posted this in general help, so I will post here if I get an answer there first.

For some reason. My Latex-suite isnt working at all. I installed it just simply with a sudo apt-get install vim-latexsuite.

and then proceeded this with a
sudo vim-addons install latex-suite

and now when I open a .tex file with vim, nothing has changed. For example, the :TTemplate command is not working at all, however I do have access to the help files, but they are of little help for my problem.

Any help would be great. Thanks

---

### Post by glennric on 2008-02-13
try
```
sudo vim-addons -w install latex-suite
```
This will enable the latex addons system wide.  The :TTemplate works for me.

---

### Post by Dougie187 on 2008-02-13
Man.. thanks.

Just a stupid typo and it caused me tons of greif. Thanks a ton though!

---

### Post by Dougie187 on 2008-02-13
Actually. That didnt help me at all.. is there anything else i need to do too?

---

### Post by Dougie187 on 2008-02-14
Anyone have any other ideas? Or a way I could start from scratch to make sure I didnt mess anything up?

---

### Post by Dougie187 on 2008-02-14
I solved it. here is the solution
[http://ubuntuforums.org/showthread.php?t=695884](http://ubuntuforums.org/showthread.php?t=695884)

---

