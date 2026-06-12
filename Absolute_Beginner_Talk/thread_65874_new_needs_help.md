---
title: "new needs help"
date: 2005-09-15
forum: Absolute Beginner Talk
---

### Post by ark on 2005-09-15
when i run a program whit the terminal like:
```
xmms
``` 

and i close the terminal the xmms closes too.

i know there is an expression (i think thats how they are called) that you write after a command ( like  -h    -l   -r) and that expression make possible that if you close the terminal, the xmms keep running. can someone tell me which one is it?

---

### Post by aysiu on 2005-09-15
Or you could just type xmms in the "run" dialogue, as opposed to the terminal.

---

### Post by bogoliubov on 2005-09-15
[QUOTE=ark]when i run a program whit the terminal like:
```
xmms
``` 

and i close the terminal the xmms closes too.

i know there is an expression (i think thats how they are called) that you write after a command ( like  -h    -l   -r) and that expression make possible that if you close the terminal, the xmms keep running. can someone tell me which one is it?[/QUOTE]

Can't you run xmms from the gnome-menu? If you have installed xmms using apt-get or synaptic you should have it in your menu I think...

If not, you can add it to the gnome-menu. Or you can add it as a launcher on one of the bars (top, bottom, sides) by right-clicking on the bar...

---

### Post by bsussman on 2005-09-15
if you want to run it from a terminal, type:

 ```
> nohup xmms
``` 

nohup essentially means, if I hang up dont hang up this exec as well. In other words, dont make it a close child of my terminal.

if you want your terminal command line not to be blocked:


 ```
> nohup xmms&
``` 

The & means run in background (the command interpreter is in foreground)

If you run  the program often, putting it on your desktop or task bar is probably a better solution.

---

