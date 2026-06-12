---
title: "noob question about the shell..."
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by dkalien on 2007-07-09
I have been putting off running Linux for years, I have been with the OTHER os for over 15 years for work, but I have encountered flavours of Linux along the way.

With Ubuntu, I have finally got a version installed and in use.  I do however remember a friend always had a famous quote appear everytime he opened the shell in terminal.  Can someone tell me is this is possible in Ubuntu also and if so how to do this.  I have a look at terminal preferences but that is my OTHER OS ideals following me to Linux I suspect.

Many thanks

Dkalien

---

### Post by felicity on 2007-07-09
In your .bashrc file (in your home folder) insert this code to check if the shell is interactive:
```

# Test for an interactive shell.  There is no need to set anything
# past this point for scp and rcp, and it's important to refrain from
# outputting anything in those cases.
if [[ $- != *i* ]]; then
   # Shell is non-interactive.  Be done now
   return
fi

```
And add this to the end of the file for fortune to display:
```

export PATH=$PATH:/usr/local/bin
export PS1="\[\033[01;32m\]\u@\h \[\033[01;34m\]\W \$ \[\033[00m\]"
alias ls='ls --color'
fortune

```

---

### Post by dkalien on 2007-07-09
Thank you Felicity :-)

---

