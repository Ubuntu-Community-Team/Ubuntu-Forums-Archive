---
title: "[SOLVED] This question is for the xubuntuers"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by MacHaddock on 2007-10-25
Hello I tried to get the little starter icon on the top panel that opens your home folder to become a menu so that I could open other folders with it like my download folder and a networkfolder on a mac in my network. (long sentence I know)

Well I couldn't make it work and now the home folder won't even open. What did I do wrong?

When I click it now it says:
"
Could not run "Home"

Failed to execute child process "thunar/home/machaddock" (No such file or directory)
"

If i right click it and go to properties it says this under command:
thunar/home/machaddock

Soooo please help me get it working and I would be oh so happy.

If you could help me fix the make it in to a menu like the one in ubuntu with other folders and network places problem I would be thrilled

That's it I'm out
/MacHaddock

---

### Post by paul.matthijsse on 2007-10-25
Hello,

when configuring that panel, say for every dir you want to have a shortcut to:
thunar /home/<user> 
thunar /home/<user>/downloads, etc. 

Works well here.

Edit: so simply put a space after thunar: thunar home/machaddock

Cheers, Paul.

---

### Post by MacHaddock on 2007-10-25
The space did it!

Thanks a million man.:)

---

