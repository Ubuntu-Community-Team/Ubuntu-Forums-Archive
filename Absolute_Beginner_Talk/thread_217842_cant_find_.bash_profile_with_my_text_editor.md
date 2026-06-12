---
title: "cant find .bash_profile with my text editor"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by sublimeprogie on 2006-07-17
hi, i am trying to learn about command line, and scripting, and i am using a site to do so.  part of this requests me to access my .bash_profile with my text editor.  i can read the file using **less** but i have no idea where i would go to open it with the editor](*,) .  i am using gedit.

thanks for any help

---

### Post by taurus on 2006-07-17
.bash_profile should be in your home directory, $HOME or ~.  In other words, if your login name is john, then /home/john is the same as ~ or /home/john/.bash_profile is the same as ~/.bash_profile!

---

### Post by sublimeprogie on 2006-07-17
i think i get what you are saying, but when i go into gedit and open i go to the home folder, then my username, the the only thing in there is my desktop, and examples.  the .bash_profile isnt there.  am i just being ignorant, or doing something wrong?  

Is there a way to launch a file into gedit by the terminal I.E. lauch gedit so that it opens with a specific file such as the .bash_profile

---

### Post by steve.horsley on 2006-07-17
There's a lot more than that there. But files and directories starting with a dot are normally hidden. You should still be able to look at the contents with **cat ~/.bash_profile** or **gedit ~/.bash_profile** from the command line. Also, typing Ctrl-H in nautilus turns on the showing of hidden files.

---

### Post by zekopeko on 2006-07-17
ok i'm new to linux but i think this explains it

file which start with a dot (".") are hidden files in linux.

you can't see it because you probably don't have enabled "Show hidden files".

you can find that in "view" menu of nautilus (that's the name of the file browser).
 
or just hit CTRL+H when in nautilus.

if you want to open it with gedit from terminal type this

```
gedit .bash_profile
```

remember to be in your home directory!

EDIT: somebody beat me to you :)

---

### Post by sublimeprogie on 2006-07-17
that is indeed the case, i found it out right before i left work, thanks for all the help

---

