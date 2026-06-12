---
title: "How to uninstall rar package through terminal"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by zech on 2007-10-15
Hello, 
Can someone help me figure out how to uninstall rar 3.51?

I downloaded an RAR 3.51 package and installed it with the command "sudo make" and "sudo make install" in my Ubuntu 7.04.  Now, I can't seem to uninstall it.  I'm an Ubuntu newby.  I could see 3 files in the "rar" folder of the  /usr/local/bin path, so I tried to use the command "sudo make uninstall" and it didn't work.  I couldn't find it in the regular "add/remove" place, either.  What should I do? 

thanks!

---

### Post by Anolis on 2007-10-15
don't really know how to uninstall it, maybe someone else can help with that, but..

[PHP]sudo apt-get install unrar[/PHP]

then..

[PHP]unrar <pathtofile.rar>[/PHP]

minus the  <>

---

### Post by realvz on 2007-10-15
try this

sudo apt-get install unrar

and then 

sudo apt-get remove --purge unrar

this should do what you want.

---

### Post by zech on 2007-10-16
Thank you very much guys! Neither one of the methods worked. :( Any more ideas?

---

### Post by bodhi.zazen on 2007-10-16
Just delete the 3 files you mentioned then.

You can see if you have additional files :

```
locate unrar
locate rar
```

and delete those too ;)

---

### Post by zech on 2007-10-16
Thank you bodhi.zazen for your help. 

If I just deleted the 3 files, instead of uninstalling it through a proper way, would it leave a lot of unwanted files in the system? 

Is there anything like windows registry in the ubuntu system?

---

### Post by bodhi.zazen on 2007-10-16
No, that would do the trick

You can find any associated files with the commands I gave you, and if you remove those too that is it ...

---

### Post by zech on 2007-10-16
Great! Thank you very much again!

---

