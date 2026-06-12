---
title: "bash shell"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by krisfrajer on 2007-08-13
Hi I jsut woke up today and decide to run the the csh bash in my linux which I find a bit more useful thxs to his handy colour  handling of files (blue for dir, green for executables, red for zip) and I was curious to know how to set up this bash as my standard bash for my linux. Do I have to also define my file .cshrc with the same parameters as for those in  .bshrc?
Thxs

---

### Post by Paul133 on 2007-08-13
Let me get this straight: you want csh to be your default shell?

---

### Post by krisfrajer on 2007-08-13
Any more interesting replies?

---

### Post by mali2297 on 2007-08-13
You don't need csh to get fancy colors. If you haven't explored bash yet, I would suggest that you do that first.

---

### Post by bodhi.zazen on 2007-08-13
Yes, you will need to set up a cshrc 

The terminology is different then bashrc ...

Search the web and you will find lots of info, 

For example : [http://foe.mmu.edu.my/sdba/ianchai/unix_tutorial/4.html](http://foe.mmu.edu.my/sdba/ianchai/unix_tutorial/4.html)

If you want to add color to ls in bash,

Add this alias to your .bashrc :

alias ls='ls -c --color=auto'
alias la='ls -ac --color=auto'
alias ll='ls -lah --color=auto'

You might also like zsh :

[http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need](http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need)

Here is a very fancy zsh prompt :

[img]http://www.aperiodic.net/phil/prompt/normal.png[/img]

[http://www.aperiodic.net/phil/prompt/](http://www.aperiodic.net/phil/prompt/)

---

