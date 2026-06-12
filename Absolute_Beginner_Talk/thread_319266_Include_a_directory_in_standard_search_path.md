---
title: "Include a directory in standard search path"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by lance_klusener on 2006-12-15
How does one include a particular directory ( e.g : /xxx/FirstTimeUser ) in the standard search path.

---

### Post by taurus on 2006-12-15
What shell are you running because for /bin/bash, you use ~/.bashrc

```
PATH=$PATH:/xxx/FirstTimeUser
export PATH
```
and for /bin/csh, you use ~/.cshrc

```
set path = (/xxx/FirstTimeUser)
```

---

### Post by lance_klusener on 2006-12-15
I am using bash , I have just typed the first code that u have mentiooned in your response , I didn't get the use of "~/.bashrc" . Where do i use this one 

Thanks

---

### Post by taurus on 2006-12-15
Applications -> Accessories -> Terminal
```
gedit ~/.bashrc
```
Now, add those two lines in there and save it.  Then, source it so the new changes will be in effect...

```
source ~/.bashrc
set
(you should now see the new path in PATH...)
```

---

### Post by lance_klusener on 2006-12-15
So i have modified the ~/.bashrc file and included the search path in it . 

Thanks for your help Taurus

---

### Post by taurus on 2006-12-15
Yip.  If you need to add a path or an alias for your /bin/bash, just modify ~/.bashrc and add it in there.  Then, you don't have to log out and back in again for the new changes to take effect.  Just run the "source ~/.bahsrc" from a terminal and you are all set to go.  Here's something for you to test out.  Add this line to the end of ~/.bashrc.

```
alias l="ls -la"
```
Save it and run these two commands from a terminal.

```
source ~/.bashrc
l
```
You will see the list of your files and directories listing, even the hidden ones...  ;)   In other words, l is the same as "ls -la" now!

p.s.  That's letter l as in larry, not the pipe sign!

---

