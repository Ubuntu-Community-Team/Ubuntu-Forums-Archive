---
title: "Color in SSH?"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by Blagomir on 2006-10-10
Hello!

How can i change the colors for my ssh? I mean not the client... I`ll explain. When i connect to one specified server the colors of the files are different from all other servers. Same for username.
How to colorize my SSH?

---

### Post by BatteryCell on 2006-10-10
check out :
```

~/.bashrc

```
Im pretty sure though that after you change that file so that colors are inplemented, you have to restart the console (like exit and then ssh again).

I think the main section that you have to have in there for ls to have colors is:
```

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias rm 'mv \!* ~/TRASH'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

```

---

