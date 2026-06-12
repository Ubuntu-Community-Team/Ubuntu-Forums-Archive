---
title: "&quot;Dumb&quot; shell on server"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by burningbunny on 2007-07-22
Hi,

My server shell (no X) seems to be a bit "dumber" than a terminal I start on my Ubuntu box with X, eg. "killall - <TAB>" lists the killable processes in KDE, but not on the server. Are these different shells? Is there a way to enable this on the server?

---

### Post by asmoore82 on 2007-07-23
make sure these lines appear in the .bashrc file in your HOME directory:
```

if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
```

you mentioned "server" ... if you are logging in to this machine remotely, the bashrc maybe 
being by-passed because BASH is acting as a real old-school login shell. If this is the case,
BASH is setting up your environment from a .bash_profile instead of .bashrc ...
so the proper way to get all of the features is to load your bashrc from within your profile:
add these lines to the file ".bash_profile" in your HOME directory and it's okay to create the file
if it's not already there ...
```

if [ -f "$HOME/.bashrc" ]; then
   source "$HOME/.bashrc"
fi
```

---

