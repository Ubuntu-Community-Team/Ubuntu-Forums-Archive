---
title: "error when try to update"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Fred54 on 2007-06-13
i am a newby at ubuntu had it installed for about 2 weeks when i try to use the update manager 
i get this error 
would be grateful for any help 
thank 
Fred

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by scribles on 2007-06-13
Did you try running **dpkg --configure -a**?
Did you make sure your disk isn't full? This is a very common cause of update failures.

---

### Post by moffa on 2007-06-13
Try the following:

```

sudo apt-get update
sudo apt-get install -f
sudo dpkg-configure -a
sudo aptitude install -f

```

That should fix it

---

### Post by Fred54 on 2007-06-13
tried running this $ dpkg --configure -a 
got this 
fred@fred-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
fred@fred-desktop:~$ 


then tried to run this  sudo apt-get update
and got this E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Fred

---

### Post by apunc1 on 2007-06-13
you need to run sudo before that command like this

```
sudo dpkg --configure -a 
```

then enter your password and post any error messages here.

---

### Post by Fred54 on 2007-06-13
fixed it i had to uninstall a program vm player 

then was able to update 

thanks 
for all your input slowly getting the hang of ubuntu 

Fred

---

### Post by Bennef on 2007-06-13
I have just started doing everything mentionned before but then my terminal is bugging on the blue window with legal mention as ; 'Configuring sun-java6-bin' do not accept when I press enter key for 'ok'
What can I do?

---

### Post by Anicka on 2007-06-13
Try one of these suggestions: [http://ubuntuforums.org/showthread.php?t=472524&highlight=java+install](http://ubuntuforums.org/showthread.php?t=472524&highlight=java+install)

---

### Post by Bennef on 2007-06-13
look like it is running smoothly now.

Cheers mate

---

