---
title: "Can't create alias"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by fredscripts on 2007-08-31
Hi! I'm trying to get into alias. I think one way to make an alias is:


```
sudo vi ~/.bashrc
```


and append that file with, for example:

```
alias tryalias = "echo aliasworking"
```

Then logout and enter again with Control+Alt+Back

and when I login and I open a terminal appears the following message:

```

bash: alias: tryalias: not found
bash: alias: =: not found
bash: alias: echo aliasworking: not found
fredscripts@laptop:~$


```

Why I can create any alias? Could you help me?


Thank you very much for your help!

---

### Post by Steve1961 on 2007-08-31
You've got the syntax and spacing wrong.  Try this:

alias tryalias='echo aliasworking'

works here :)

---

### Post by YoG%*@ on 2007-08-31
hello, 

> **fredscripts said:**
> 
```
sudo vi ~/.bashrc
```
and append that file with, for example:


first of all, you shouldn't have to use sudo to edit a file in your home directory. vi ~/.bashrc should be sufficient ;)

> **fredscripts said:**
> 
```
alias tryalias = "echo aliasworking"
```Then logout and enter again with Control+Alt+Back


try 
```
alias tryalias='echo aliasworking'
```
(no whitespaces!) and see if it works then.

hth,
mux

---

### Post by YoG%*@ on 2007-08-31
> **Steve1961 said:**
> You've got the syntax and spacing wrong.  Try this:

alias tryalias='echo aliasworking'

works here :)


argh, you were faster =)

---

### Post by fredscripts on 2007-08-31
Oh perfect! Thank you very much to all :) By the way how could I mark this post as SOLVED?

---

