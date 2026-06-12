---
title: "Where to put my aliases and variables"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by dragonfli on 2006-06-28
Thanks for any replies.

Where would I put aliases and variables so when I boot or open a new shell these are all set?

Thanks 

Doug

---

### Post by xtacocorex on 2006-06-28
You can put them in ~/.bashrc file for aliases and variables

---

### Post by Rui Pais on 2006-06-28
hi,
they usually go to /home/<username>/.bashrc

---

### Post by jchau on 2006-06-28
aliases should go into a file called ".bash_aliases" in your home directory.  An exampe .bash_aliases file might read:
```
alias startx="exec startx"
alias shutdown="sudo shutdown"

```

I am not sure if there is a special file for variables, but you should be able to place commands in ".bash_profile" or ".bashrc" to be executed everytime bash starts.

---

### Post by xtacocorex on 2006-06-28
I couldn't remember if .bash_aliases was automatically linked to .bashrc, hence why I didn't include that.

---

### Post by Rui Pais on 2006-06-28
I post in same time as xtacocorex (and i couldnt find a way to delete my redundant post) so to add a little extra info, to apply changes without logout just do:
```
source ~/.bashrc
```

---

