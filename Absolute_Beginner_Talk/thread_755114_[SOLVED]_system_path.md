---
title: "[SOLVED] system path"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by DGortze380 on 2008-04-14
I've search, and thought I found the solution, but for the life of me, I can't find my system path so that I can add a new directory to it.

I have a number of scripts I use often, and want to put them in one directory, and add that directory to my path so that I don't need to be in that directory and use ./ to run them.

I read .bashrc, .profile /etc/profile ... but none of those currently include a path statement. I tried adding one, but that didn't work.

---

### Post by ibutho on 2008-04-14
If you run "echo $PATH", you current path will be shown on the screen. To add to the path for an individual user, edit ~/.bash_profile and change the path variable (if its not listed, then just create a new entry) so that it looks like
```
export PATH=$PATH:/path/to/new/dir
```
To change the path globally, edit /etc/environment and add you new path directory to the list.

---

### Post by DGortze380 on 2008-04-14
forgot to export PATH

#-o

thanks!

---

