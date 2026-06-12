---
title: "What's the command for &quot;Force a misbehaving application to quit&quot;?"
date: 2005-09-05
forum: Absolute Beginner Talk
---

### Post by aysiu on 2005-09-05
I happen to like keyboard shortcuts very much, and I would prefer to have a keyboard shortcut rather than a button like [this](http://i22.photobucket.com/albums/b337/psychocats/66ba58a6.png) to force misbehaving applications to quit.

If I know what the command for it is, I can create the keyboard shortcut for it. When I right-click on the icon, though, there's no properties. The only options are "Help," "Remove from Panel," "Move," and "Lock to panel." Nothing indicates to me what command it uses.

Does anyone know the terminal command for this button or how I should go about finding the command for it? Any help is appreciated. Thanks in advance!

---

### Post by jpkotta on 2005-09-05
Graphical: xkill
All purpose: kill

Note that sometimes, like when an app is really misbehaving, you need to do a kill because xkill will just kill the window, not the process.  If kill still doesn't work, use `kill -KILL` or `kill -9` (equivalent).

kill is not just for killing processes.  You use it to send processes signals, which can do things like pause and resume in addition to terminating and killing.

I have the following in my ~/.bashrc for dealing with processes:
```
# list of processes matching a regex
alias psg='ps -e -o pid,ppid,user,cmd | grep -vE "grep|ps[gkK]" | grep -E'
function psk() { kill `psg "$@" | awk '{print $1}'` ; }
function psK() { kill -KILL `psg "$@" | awk '{print $1}'` ; }
```

---

### Post by aysiu on 2005-09-05
Thanks. I don't think either of those is the same command that little icon uses, but *xkill* seems to work just fine.

---

