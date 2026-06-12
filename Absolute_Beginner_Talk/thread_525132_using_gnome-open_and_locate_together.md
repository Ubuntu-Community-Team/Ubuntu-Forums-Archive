---
title: "using gnome-open and locate together"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2007-08-14
Hello,

I would like to open a file that has just been searched .

when I locate a file that includes "ayse" i got the following output: 

> mozkaynak@ozkaynak:~/research/literature/workflow analysis/general$ locate ayse
/home/mozkaynak/research/literature/PREVIOUSLY USED/other/ayse.pdf
mozkaynak@ozkaynak:~/research/literature/workflow analysis/general$ 


then I would like to open the file that has been found with locate command then I type
> mozkaynak@ozkaynak:~/research/literature/workflow analysis/general$ gnome-open | locate ayse

the output is

> mozkaynak@ozkaynak:~/research/literature/workflow analysis/general$ gnome-open | locate ayse

then how to make ubuntu search and open file(s) with a single command.
Thanks

---

### Post by nanotube on 2007-08-14
```
locate ayse | gnome-open
```
or
```
gnome-open $(locate ayse)
```

should do the trick

---

### Post by mozkaynak on 2007-08-14
Thanks alot with the help 
however, these tricks do not work

> mozkaynak@ozkaynak:~$ locate ayse | gnome-open
Usage: gnome-open <url>


> mozkaynak@ozkaynak:~$ gnome-open $(locate ayse)
Error showing url: The location or file could not be found.


is any ideas?

---

### Post by nanotube on 2007-08-15
it wants to be like that, eh? :)
ok, then, this should do it;
```
locate ayse | xargs -I'{}' gnome-open {}
```

---

