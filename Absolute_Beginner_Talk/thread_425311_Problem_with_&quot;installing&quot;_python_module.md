---
title: "Problem with &quot;installing&quot; python module"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by mjekl on 2007-04-27
Hi,

 I'm an abs beginner trying to install a python module in the correct directory. So that python knows where it is!

Looking around I've managed to figure, I think :-( out that the correct location is: "/usr/lib/python2.4/site-packages". It should be unless there's more than one site-packages dir in the system? Which I suppose there's not!

All my previous experience is with M$Win. I understand it's a matter of permissions but copying, but I really don't know how to copy a python module file from my "home folder/pyfiles/mgDispatcher.py" to "usr/lib/python2.4/site-packages/mg/". Let alone figure out how to bypass permissions.

all help greatly appretiated.
Thanks in advance,
Miguel

---

### Post by Seisen on 2007-04-27
Actually you can do this in the terminal

gksudo nautilus

This will give you superuser rights in nautilus and then you can move the file in nautilus, which would be easier for you.

---

### Post by LaRoza on 2007-04-27
Moving this to the Programming Talk forum would get you answers quicker.

I do not know about installing Python modules, I am new to the language, but if you want to move something with as root, you such add sudo before the copy or move command.

---

### Post by mjekl on 2007-04-27
Thanks for the answer Seisen.

Thanks for the suggestion LaRoza. Actually I've posted here because this issue is not really related to python. I know here the module should be  (location of a file), just not how to put it there!

Thanks for the help.
I'll look into reading something about sudo.

Txs,
Miguel

---

