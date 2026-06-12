---
title: "help reinstalling"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by benner on 2007-02-03
this is a repost. i got 0 replies in the install forum so i thought i would try here.  my computer is slowly programming me to become more impatient.  anyways, here goes...

i have an older machine that i have been noodling around with to test out linux and learn everything i can. i started with edubuntu (dapper) and upgraded to edgy, installed kde, xfce, language support for a million languages, every program for everything i could think of. now, it's a mess.  currently, it is so gummed up with stuff, it freezes, gives stange errors and all kinds of little quirks, etc...  i am ready to wipe it and start fresh. 

i have settled on xubuntu and am ready to wipe everything and start fresh. problem is, i want to do it this weekend. i don't have a copy of the cd here, the linux box has no burner and my other computer has a broken burner. i figure that there must be some simple apt-get that will allow me to do this online. suggestions? 

thanks in advance for any help.

---

### Post by igknighted on 2007-02-03
> **benner said:**
> this is a repost. i got 0 replies in the install forum so i thought i would try here.  my computer is slowly programming me to become more impatient.  anyways, here goes...

i have an older machine that i have been noodling around with to test out linux and learn everything i can. i started with edubuntu (dapper) and upgraded to edgy, installed kde, xfce, language support for a million languages, every program for everything i could think of. now, it's a mess.  currently, it is so gummed up with stuff, it freezes, gives stange errors and all kinds of little quirks, etc...  i am ready to wipe it and start fresh. 

i have settled on xubuntu and am ready to wipe everything and start fresh. problem is, i want to do it this weekend. i don't have a copy of the cd here, the linux box has no burner and my other computer has a broken burner. i figure that there must be some simple apt-get that will allow me to do this online. suggestions? 

thanks in advance for any help.

I'm sorry to say but this might not be the best plan.  What you would have to do is:
```
sudo aptitude remove kubuntu-desktop ubuntu-desktop edubuntu-desktop
```
and also any other DE or any language pack you want to remove.  This **MIGHT** get it all, but I doubt it.  Let it remove all it can, in fact you might want to add xubuntu-desktop to that list and reinstall it as well.  After purging this, you will have to manually go back and look to see that everything is gone.  Chances are, there will be junk left over.  To achieve your goal, your best bet is to either (a) get a friend to burn the file, or (b) spend $10 on a cheap burner.  Or, you could wait 3 months for ship-it.  Best of luck with the cleanup.

---

### Post by riven0 on 2007-02-03
Also, you may want to try installing **debfoster**, (**sudo apt-get install debfoster**). This program will give you a list of all programs installed on your comp along with their dependencies and gives you the option of uninstalling them if you want. 
You have to run it through the terminal, so after installing it, just type **debfoster** to start.

---

### Post by benner on 2007-02-03
thanks for the info.  i just found a couple of good scripts on psychocats.net to install 'pure xfce' that can remove most of the junk.  if i have a problem with it i will post back.  cheers!

---

