---
title: "how to copy CD to drive?"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by s1baker on 2006-12-20
How can I copy from the CD to the HD ?
When I select a file on the CD and select right mouse click and then copy,  I 
can paste it into my home directory but not in the main or root directory.
How can I copy with admin permissions using the mouse .

 I found out the other day about typing in the terminal to copy files to root using 
the sudo option, but I want to copy and paste using the mouse. not by typing out the 
file names using the keyboard.

Thanks
S1baker

---

### Post by meng on 2006-12-20
You could type at terminal:
gksu nautilus

But why would you want to clutter up your / directory with stuff like that?

---

### Post by s1baker on 2006-12-20
> **meng said:**
> You could type at terminal:
gksu nautilus

But why would you want to clutter up your / directory with stuff like that?





I tried gksu nautilus but i got this:

GnomeUI WARNING ** While connecting to the session manager:
Authentication rejected, reason: None of the authentification protocols specified 
are supported and host=based authentification failed

---

### Post by mr_samsonov on 2006-12-20
I guess you could log in as root? Which is how I would have done that while using Gentoo. I know Ubuntu handles things a little differently, but you can create a root password, and I guess log in as root. However I do agree with meng. Why do you want to store files there?

---

### Post by meng on 2006-12-20
> **s1baker said:**
> I tried gksu nautilus but i got this:

GnomeUI WARNING ** While connecting to the session manager:
Authentication rejected, reason: None of the authentification protocols specified 
are supported and host=based authentification failed
But it still works, doesn't it? You didn't mention whether it works. gksu often gives that error, but the application generally opens anyway.
By the way, if you type at the terminal, TAB will auto-complete file names for you.

---

### Post by johnstar on 2006-12-20
open up mycomputer (it's in places in the start menu rightclick the cd select copy disc  then copyto: will list your  
 burner change it to file image  it will save isos        ps  rightclick on a iso and select burn to burn it!

---

