---
title: "Xubuntu menu editing"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by Qwertinsky on 2006-11-06
I want to limit the programs my son can use on his login. 

I have tried the menu properies and the menu editor but I do not see where things like Gaim (thats what I want to remove) is.](*,) 

Is there an eaier way to limit the programs a user can use?

---

### Post by Qwertinsky on 2006-11-08
Hello? Is this thing on?...

Maybe I am asking the wrong question.

How do I restrict what programs a user can use?

---

### Post by -Phi- on 2006-11-09
Hmm, well I don't know how to limit access the programs themselves (he could probably get to them via the terminal or something?), but you can make a custom menu in the menu editor. 

Frustratingly, you basically only have a choice between the not customizable automagically generated menu, and making one from scratch. Fortunately it's relatively easy to drag and drop items from the Appfinder into the Menu Editor program to make a new menu. Once you've made and saved a menu .xml file, right click the Applications button (where the menu comes from) and point it at the custom menu file.

Hope this helps :)

- Phi

---

### Post by dannyboy79 on 2006-11-09
what about making the program only executable by root? I am a newbie so if this won't work than I am sorry I just thought that this might be a solution? unless of course your son knows' the root password?

edited: let me know if I am correct on this?

---

### Post by dwblas on 2006-11-09
You can create a group name for your son's programs and then add yourself and your son to that group.  Change the group for the programs you want to the created group name. These are usually in /local/bin.  As long as he isn't in any other groups, he can't access any other programs.  How you do all of this depends on which desktop you are using.  Groups are in the file /etc/group (with root access only).  To change the individual files it is easiest to use a GUI IMO.

---

