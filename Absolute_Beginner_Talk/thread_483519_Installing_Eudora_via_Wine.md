---
title: "Installing Eudora via Wine"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Carnage_7 on 2007-06-24
I am trying to install Eudora 7.1.0.9 via Wine on Ubuntu 7.04.  I am running a dual boot with WinXP Pro.  The problem is this:  I aleady have this version of Eudora already installed on WinXP.  When I try to install Eudora on Ubuntu it wants to install it to the same directory where Eudora is installed on WinXP.  I stopped at this point because I didn't want to screw up Eudora on WinXP.  Can I install it to that directory without screwing up Eudora on WinXP?  There isn't any other directory to install it to on C:.  Please advise.  Thanks

Frank
El Paso, Texas

---

### Post by eljalill on 2007-06-25
Hey Frank,
There is no problem there. The "C" directory in wine is not the same place as your windows "c" directory. Actually it is in ~/.wine/drive_c . wine just makes belief to Eudora that this is a "real" C-directory. 
So you can just go ahead, and let wine install Eudora on C, you are not touching your xp partition in the process.

And if you want to make sure and see how it works, just install another program in wine, and see, where that installs to. Let wine install it on "C", and than look for it with "locate" in the terminal.

Cheers!

PS: There is loads of information on winehq, maybe you  want to check it out sometime

---

### Post by Peter6218 on 2007-09-20
> **eljalill said:**
> Hey Frank,
There is no problem there. The "C" directory in wine is not the same place as your windows "c" directory. Actually it is in ~/.wine/drive_c . wine just makes belief to Eudora that this is a "real" C-directory. 
So you can just go ahead, and let wine install Eudora on C, you are not touching your xp partition in the process.

And if you want to make sure and see how it works, just install another program in wine, and see, where that installs to. Let wine install it on "C", and than look for it with "locate" in the terminal.

Cheers!

PS: There is loads of information on winehq, maybe you  want to check it out sometime

I have installed Feisty on three different HD's. On only one of them would it install Eudora. Have downloaded Wine via Add/remove. What am I missing??

---

### Post by Peter6218 on 2008-03-24
Solved the "Won't Install" problem. Set Wine config for Win98 and it works fine.

Now I do have a problem.

Can't C&P from Firefox or anything else into a Eudora mail. Does anybody know how to solve this?

---

### Post by tkgafs on 2008-05-01
> **Peter6218 said:**
> Solved the "Won't Install" problem. Set Wine config for Win98 and it works fine.

Now I do have a problem.

Can't C&P from Firefox or anything else into a Eudora mail. Does anybody know how to solve this?

Turn off compiz screen effects and cut and paste will work

---

### Post by Peter6218 on 2008-05-01
> **tkgafs said:**
> Turn off compiz screen effects and cut and paste will work

OK For this total amateur please explain a little more?

---

