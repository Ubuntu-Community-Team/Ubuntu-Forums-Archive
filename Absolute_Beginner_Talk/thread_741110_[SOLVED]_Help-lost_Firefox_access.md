---
title: "[SOLVED] Help-lost Firefox access"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Rodney2 on 2008-03-31
I'm just getting started with Ubunto and have been learning a lot.  However, when I turned on the computer this morning everything seemed to come up fineuntil I tried to get online.  This has worked perfectly up to now but, I now get the the little wirling circle for a bit then back to a blank screen.  I went to the terminal changed to the .mozilla directory by typing in "cd .mozilla"
then, when the directory came up I typed in .mozilla$ firefox
and I get the following message:
Segmentation fault (core dumped)

My question, what happened and how do I correct or recover?  Thanks Rodney
In addition, I am hard wired to a router and that is working okay as, on my Windows setup on another computer but the same router, everything works, that is how I am writing this.  I've double checked all wiring between the router and computer.  thanks.

---

### Post by AndyCooll on 2008-03-31
And if you go to the terminal and simply enter:
```
firefox
```
what do you get?

:cool:

---

### Post by Rodney2 on 2008-03-31
I get
Segmentation fault (core dumped)
nothing else

---

### Post by AndyCooll on 2008-03-31
Ok, two simple options spring to mind. 

1. You could delete your .mozilla folder in your home directory (press CTRL+H to reveal your hidden directories). It might be worth making a backup of this folder first if you have some settings, e.g. bookmarks that you don't want to lose. Then try restarting Firefox.

2. Re-install Firefox. Go to System > Administration > Synaptic Package Manager. Search for Firefox and then right click on the green coloured box. It brings up a list of options. Choose "Mark for reinstallation". Finally click on "Apply". When it's finished try re-starting Firefox.

:cool:

---

### Post by Rodney2 on 2008-03-31
Thank you so much, I used the Synaptic Package Manager as you suggested and reinstalled Firefox.  It is now up and running.  Can't tell you how much I appreciate your fast response.  Rodney

---

