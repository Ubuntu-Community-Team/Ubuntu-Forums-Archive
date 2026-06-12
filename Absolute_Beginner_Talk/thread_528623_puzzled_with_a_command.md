---
title: "puzzled with a command"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by bellzii on 2007-08-18
Im a newbie to linux can some1 tell me if  i need to ~/.mplayer/gui.conf  for instance , how do i access this directory , it doesnt work if i paste it in the terminal

thanks in advance

---

### Post by nitro_n2o on 2007-08-18
The tilda '~' will expand to you home directory, for example if you home is /home/bellzii 
then typind cd ~ in the command will take you there.. 
the thing you are trying to access is not a directory, it's a file 
try this 
```
gedit ~/.mplayer/gui.conf
```
or 
```
gedit /home/<user_name>/.mplayer/gui.conf
```
Any file starts with a "dot" is a hidden file.. if you want to see it in the files browser.. press CTRL+H 
you should also learn some command line text editing program like Vim or Emacs 

good luck :)

---

