---
title: "add a program to your PATH"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by n.aggel on 2006-12-28
hi, i recently installed password gorilla{in /opt/gorilla} .And in order to start it i have to type the full path...so i was wondering how to add it to my $PATH...:confused: 

thanks

---

### Post by n.aggel on 2006-12-28
i just found that using a symbolic link will do the job!!

read:: [http://kb.iu.edu/data/abbe.html](http://kb.iu.edu/data/abbe.html)

:) 

is there any difference between hard and symbolic links?

---

### Post by maxamillion on 2006-12-28
```
export $PATH="/opt/gorilla"
```

if i remember correctly, I haven't added anything to my path in years ... apt has been good to me.

---

### Post by maxamillion on 2006-12-28
massive difference, i suggest you either google or wikipedia the two.

---

### Post by amo-ej1 on 2006-12-28
```

edb@rogue:~$ fgrep PATH .bash*
.bash_profile:# set PATH so it includes user's private bin if it exists
.bash_profile:    PATH=~/bin:"${PATH}"

```

Shows that you paths get set in the file ~/.bash_profile (the file .bash_profile in your home directory). So when extending this for your own user you open that file and modify the line
```

 PATH=~/bin:"${PATH}"

```
inyo
```

 PATH=/opt/gorilla/:~/bin:"${PATH}"

```

every new shell you start (or terminal you open) will execute this file and update your $PATH variable. 

(if you want to do it system wide you could also do something alike in /etc/profile) or if you don't want to mess with the path variable use a symlink (as suggested above).

---

