---
title: "How do I add my own path to bash profile in Ubuntu?"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by cloudsea on 2007-03-30
This is probably a rather simple question, but I could not get a good answer after googling for a while.

I add the following lines to /home/myusername/.bash_profile:
PATH=$HOME/bin
export PATH

After login again, I still can't use the executable files in the path I specified:( 

What should I do?

I tried the same to /etc/bash.bashrc, and ended with some error. I changed the bash.bashrc file to its original content (I had backup) afterwards. But strangely, I can't use some commands, like nano, etc using the root account, however, I can still use those commands as a regular user.

Any help is appreciated. Thanks!

---

### Post by psyberpnk on 2007-03-30
I had the same problem.  Here is what I added to my .bashrc.  It works for me so I hope it helps you.


PATH=~/bin:"${PATH}"

---

### Post by taurus on 2007-03-30
Yes, should add these two lines to your ~/.bashrc.

```
PATH=$PATH:$HOME/bin
export PATH
```

---

### Post by cloudsea on 2007-03-30
Thanks to you both.

It worked, however, now the terminal does not recognize commands like su, nano, ... 

How do I fix this? 

Thanks a lot..

---

### Post by taurus on 2007-03-30
Try

```

PATH=$PATH:~/bin
export PATH

```
Then, reread it with

```
source ~/.bashrc
```

---

### Post by psyberpnk on 2007-03-31
I think an equally important is why does bash not automatically recognize ~/home.  Looking at the following code and documentation from from .bash_profile it appears that it does try to add the folder 


```

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"

```
 

so why does this not work?  That is, why did I have to add to .bashrc?

---

### Post by jcearls on 2007-04-06
I'm pretty sure I read someplace that for some reason, either gnome or ubuntu made the decision not to read the .bash_profile and only use the .bashrc.  Still a newb myself so this isn't exactly authoritative, but that's my understanding.

---

