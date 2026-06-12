---
title: "[SOLVED] Pidgen turns off"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by hillbillybrit on 2007-10-24
Dunno where i went wrong here.
Turned the pc on today to chat to friends and read mail blah blah
pidgen came on for about 30 secs then turned itself off.
worked fine last night
I've tried add/remove to uninstall and then reinstalled it but get the same fault.
I know i've got to get into the terminal thingy and type some code and do the geeky stuff but I'm a new linux user and got no clue on this just now though not through want of trying.
I'm guessing its a prog connected with pidgen rather than pidgen itself
Any clues?
I'm planning an hour a day playing on the terminal once everything is up and working generally. Once you know the terminal you know Linux and you've set yourself freeeeeee!!!

---

### Post by kelbizzle on 2007-10-24
Try running Pidgin from the terminal window
```
pidgin
```

See what error it returns in the terminal window. That will give us the first clue. 

You can also try starting pidgin with 
```
pidgin -n
``` That will start pidgin without logging you in automatically.

---

### Post by hillbillybrit on 2007-10-24
seems it turns off as soon as it makes the connection to the internet.
As this is a most awesome program i'd love to have it back working

---

### Post by hillbillybrit on 2007-10-24
from the terminal window it opens the prog but blank
No error messages on the terminal window

---

### Post by hillbillybrit on 2007-10-24
Ok while offline it stays on but blank
When trying to connect it logs in the drops off
Error message on terminal then is:
Segmentation fault (core dumped)

---

### Post by kelbizzle on 2007-10-24
So no error messages in the terminal window at all? After you run pidgin what does it say after that line. 

Did you try starting pidgin with the -n option?

---

### Post by hillbillybrit on 2007-10-24
yup when tried with the =n i get that error after i try to connect
Segmentation fault (core dumped)

---

### Post by kelbizzle on 2007-10-24
try renaming the .purple folder inside of your home folder. You may have to press ctrl+h to see the hidden files and folder. Then try to run it you will have to reenter all of your login info. See if the issue persist after that. If the issue does persist change the name back to .purple

---

### Post by hillbillybrit on 2007-10-24
Erm i think I've fixed it.
I had multiple accounts set up within it and turned some off.
Now it seems to be stable and connected.
I shall go look at that purple folder however to see what it is anyway. Plodding round these new folder systems has been fascinating.
THanks for the help

---

### Post by kelbizzle on 2007-10-24
Your welcome. The .purple folder is pretty much all the preferences for pidgin for Your user.   
Removing it or renaming it will cause pidgin to think this is the first time you've ever opened it up. Don't forget to mark your thread as solved.

---

### Post by hillbillybrit on 2007-10-24
Seems its the Myspace account that kills it.
AIM and Yahoo all work fine
Dunno if thats a bug or myspace not up to the job.

---

### Post by kelbizzle on 2007-10-24
Hrmmm...It shouldn't I use myspace im. Which version of pidgin are you using?

---

### Post by hillbillybrit on 2007-10-24
Its version 2.2.1
Yes it worked fine yesterday.
Now that account is disabled its been running fine
I shall try deleting and reinstalling that account

---

### Post by hillbillybrit on 2007-10-24
Deleting and reinstalling that account caused the same fault

---

### Post by kelbizzle on 2007-10-24
> **hillbillybrit said:**
> Deleting and reinstalling that account caused the same fault

Did you rename the .purple folder or just goto the accounts window and delete it?

---

### Post by hillbillybrit on 2007-10-24
I initially just deleted the account and obviously the data remains in the folder right? so when i reinstalled it it went back to the previous settings I assume
I have now renamed the purple folder and re done all the accounts and everything is working great.
Many thanx for your efforts. Much appreciated
Now how do I end a thread eh?

---

### Post by kelbizzle on 2007-10-24
> **bromix said:**
>   You can do this by navigating to that particular thread, and choosing "Thread Tools" and selecting the option to "Mark This Thread As Solved".

There ya go. again your very welcome.

---

