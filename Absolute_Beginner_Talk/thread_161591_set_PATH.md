---
title: "set PATH ?"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by aquafina on 2006-04-17
For some reason, I can't set the PATH variable for myself.

I have tried to do 

> 
PATH=$PATH:/usr/.....
export PATH

on .bash_profile , .bashrc and /etc/profile but afterward when do

> 
echo $PATH


I got the same thing.

Any thoughts ?

Thanks

---

### Post by taurus on 2006-04-17
Maybe you need to source it to reflect the new changes...
```

source ~/.bashrc

```

---

### Post by henryk69 on 2006-04-17
You're almost there :) Just add quotation marks

If you want it permanently added, edit your **~/.bashrc** file and add at the end
```
 export PATH="$PATH:/your_new_path" 
```
Then all you need to do is to load the changes 
```
 source ~/.bashrc 
```

cheers,

---

### Post by aquafina on 2006-04-17
I actually did all that (plus re-open a new terminal) then what I got was "PATH : command not found" 


Really weird !

---

### Post by aquafina on 2006-04-17
Hah, didn't know about the " " thing.

That was quick :D

Thanks a lot

---

