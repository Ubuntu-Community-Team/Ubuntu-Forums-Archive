---
title: "[SOLVED] Symbolic link"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by rabbitman on 2008-04-14
I'm currently learning [Ruby](http://www.ruby-lang.org/en/) & in order to access the folder containing my Ruby programs I open a terminal & type.
```

cd documents/ruby/

```

Would it be possible to create a Symbolic link from the ruby folder to my home folder, so I could just type?
```

cd ruby

```

---

### Post by spiderbatdad on 2008-04-14
Documents is usually located in the Home directory. If this is the case, you can just move the ruby folder out of Documents by cutting and pasting...

---

### Post by cm.squared on 2008-04-14
You could also add an alias to your .bashrc file in your home directory:
```
alias cdr='cd ~/documents/ruby'
```
or whatever the appropriate path is.  Adding this command to the .bashrc file will execute it every time you start a terminal, so you can use the abbreviated command "cdr" to go straight to the ruby directroy.  If you don't have a file called .bashrc you can just make one.

---

### Post by rabbitman on 2008-04-14
Thank's for the help. :KS

I managed to figure out how to solve the problem, I just did the following.
```

sudo ln -s /home/user/documents/ruby/ ./ruby

```

Now I can type
```

cd ruby

```

---

### Post by spiderbatdad on 2008-04-14
Certainly it would have been:```
sudo ln -s /Home/user/Documents/ruby ./ruby
```

since linux is case sensitive.

---

### Post by rabbitman on 2008-04-15
> **spiderbatdad said:**
> Certainly it would have been:```
sudo ln -s /Home/user/Documents/ruby ./ruby
```

since linux is case sensitive.
You're right, most people would need to capitalize the 'h' & 'd'.

But I renamed my 'Home' & 'Documents' folders a few Weeks after I installed Ubuntu. ;)

---

