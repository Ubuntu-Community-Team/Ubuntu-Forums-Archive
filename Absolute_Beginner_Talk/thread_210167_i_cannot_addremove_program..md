---
title: "i cannot add/remove program."
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by penguinKabuki on 2006-07-06
emm....
i cannot do a lot of things....
add remove prog...
create folder...
updates kernel....
it said...i dont have the permision...
wonder y?

---

### Post by T700 on 2006-07-06
Exactly how are you attempting these actions?  Is there a prompt for you to enter a password?

Paul

---

### Post by penguinKabuki on 2006-07-06
the 1st time i notice it...

when i want to add/remove prog...it ll ask for password....but the....it just keep quite like that....emm...

the....when i want to update my kernel...it just the same thing happen...

next....when i want to edit my sourceslist in /etc/apt....i cannot do so...

emm...wonder why~~~

---

### Post by T700 on 2006-07-06
I don't mean to be rude, but could you please formulate your response a little more clearly?  I don't understand what is going on.  Is your password being rejected?  Are you not able to enter commands or start a program as root?

Paul

---

### Post by lordlollo on 2006-07-06
Did you try with sudo? ;)

---

### Post by penguinKabuki on 2006-07-06
emm..
usually..if i want to add/remove prog.....just click the icon right?the ubuntu icon and then go to...add application....right?

then it ll ask password.....right?i enter the password....but nothing happen...it just stop like that...

sudo?how to use sudo?

---

### Post by T700 on 2006-07-06
Try this:  Log out of your current session and log back in.  Now, try adding a program again.  

"sudo" and "gksudo" are ways of temporarily becoming root to run an application or execute a command.  After you enter them in a terminal, you are prompted for your password.  For example:

```
gksudo nautilus
``` 
or

```
 sudo aptitude install xyz 
``` 
gksudo (or kdesu if you are running KDE) is used if you are starting a graphical application such as Nautilus and sudo is used for non graphical commands.

Paul

---

### Post by penguinKabuki on 2006-07-06
the same thing happen...what is the same thing?nothing happen after i enter my password....

and....after i copy paste the...

gksudo nautilus

it became like this...

[[IMG]http://img443.imageshack.us/img443/403/screenshot6vs.th.png[/IMG]](http://img443.imageshack.us/my.php?image=screenshot6vs.png)

plz help me...i love to use ubuntu...i dont want to change to other distro....[-(

---

