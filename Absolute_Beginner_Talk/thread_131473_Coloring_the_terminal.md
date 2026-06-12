---
title: "Coloring the terminal"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by Connollyir on 2006-02-16
Sort of a noob question but I've seen this on other computers - most notably my Gentoo distro - and I want to replicate it on Ubuntu. I looked around but you get some pretty strange responses for "coloring the terminal" so I figured I would post here. I want to colorize my terminal text to make it not so bland........ can anyone tell me how to do this?

Thanks

-Ian

---

### Post by carlosqueso on 2006-02-16
If you mean the cool color of the prompt, open a terminal, and  use gedit .bashrc in your home directory.  Then find the lines about the prompt and make them look like this: ```
# set a fancy prompt (non-color, unless we know we "want" color)
# case "$TERM" in
# xterm-color)
#   PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
#    ;;
# *)
#    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
#    ;;
#  esac

# Comment in the above and uncomment this below for a color prompt
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

```

hope this helps.

---

### Post by Connollyir on 2006-02-16
> **carlosqueso]If you mean the cool color of the prompt, open a terminal, and  use gedit .bashrc in your home directory.  Then find the lines about the prompt and make them look like this: ```
# set a fancy prompt (non-color, unless we know we "want" color)
# case "$TERM" in
# xterm-color)
#   PS1='${debian_chroot:+($debian_chroot)}\[\033[01 said:**
> \u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
#    ;;
# *)
#    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
#    ;;
#  esac

# Comment in the above and uncomment this below for a color prompt
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

```

hope this helps.

Nasty. That helped a ton... I was so tired of staring at "stale" text. Thanks


-Ian

---

### Post by simon_is_learning on 2006-02-16
Is it possible to translate a HEX-string to "what ever is written there" 

So that i could choose my own color?

Also is it a simular trick for xfterm4?

---

### Post by carlosqueso on 2006-02-16
Connollyir: You're welcome, messing with your .bashrc file is loads of fun, and so far I haven't broken anything[-o< 

Simon:  That trick will work for all terminals using a bash shell, I use xfterm4 and it works for me.  I don't know what the hex means unfortunately, but if I find out I'll let you know.

---

### Post by carlosqueso on 2006-02-16
[http://www-128.ibm.com/developerworks/library/l-tip-prompt/](http://www-128.ibm.com/developerworks/library/l-tip-prompt/)  Check this out for a sort of good color key...I got my prompt changed with it.  after the [ the first number controls style, and the second color in our bashrc's though.  ```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;31m\]\u@\h\[\033[01;31m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
``` yeilds a pretty cool looking one in my opinion.

---

### Post by Aquinus on 2008-03-10
Personally I think that its nicer to set it so red is for the su and green for a regular user. Personal preference. :)

---

### Post by bodhi.zazen on 2008-03-10
Try these links :

[http://www.gentoo.org/doc/en/articles/prompt-magic.xml](http://www.gentoo.org/doc/en/articles/prompt-magic.xml)

	[http://www.linuxjournal.com/article/8603](http://www.linuxjournal.com/article/8603)

---

### Post by Warprunner on 2008-03-10
Wow that is really like a breath of fresh air!!! 
Thanks for the instructions and thanks for the links!!!

I found the following perfect for me!

PS1="\[\e[36;1m\]\u@\[\e[32;1m\]\H> \[\e[0m\]"

---

