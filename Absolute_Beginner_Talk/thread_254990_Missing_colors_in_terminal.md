---
title: "Missing colors in terminal"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by ubonetu on 2006-09-10
I'm going crazy.  I'm quite sure that my filetypes were colorized in xterm and gnome-terminal and now they are not.  Help!

Ubonetu

---

### Post by MiKuS on 2006-09-10
i'm not 100% sure what you mean, but did you try going into "edit>current profile ..." and checking the colours tab?

---

### Post by neko18 on 2008-02-06
In a terminal run:
```
gedit ~/.bashrc
```

Then at the end of the file, on a new line, add:
```
alias ls='ls --color=auto'
alias grep='grep --color=auto'
```

Save the file and close gedit

Now run this in a terminal to apply the changes to your current session:
```
source ~/.bashrc
```

---

