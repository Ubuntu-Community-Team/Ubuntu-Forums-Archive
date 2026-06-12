---
title: "Difference between &quot;Add/Remove Programs&quot; and Adept Package Manager?"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by CaptSaltyJack on 2007-02-17
What's the difference between these two options on the start menu?  To me, it just seems that "Add/Remove Programs" is a dumbed down version of the Adept Package Manager.

---

### Post by v8YKxgHe on 2007-02-17
Yep, that's what it's suppose to be I think. It's just to supply the user with an easy way of installing Programs instead of other things Adept offers such as downloading any file from the Ubuntu repostories.

---

### Post by rusty4r on 2007-02-17
Does add/remove programs resolve dependancies like synaptic does?

And I think it was in Linux Ubuntu Resources where I read something about aptitude doing that but apt-get would not. Or am I lost too?

---

### Post by v8YKxgHe on 2007-02-18
> **rusty4r said:**
> Does add/remove programs resolve dependancies like synaptic does?

And I think it was in Linux Ubuntu Resources where I read something about aptitude doing that but apt-get would not. Or am I lost too?

Add/Remove, Adept, Synaptic, apt-get and aptitude all resolve dependencies, other wise the installed program would most probably not work (as it depends on other software).

The difference between apt-get and aptitude is that if you install a program via aptitude and it installs dependencies, when you come to uninstall the program via aptitude, it will not only remove the program but also the dependencies that were installed when you first install the program. 

This is now possible though, with apt-get. Say if you do "apt-get remove program", if any dependencies were installed when you installed "program" you can run "apt-get autoclean" to remove them, afaik. (as long as another program doesn't depend on them)

---

