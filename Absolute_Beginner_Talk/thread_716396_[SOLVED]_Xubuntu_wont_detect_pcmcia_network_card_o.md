---
title: "[SOLVED] Xubuntu wont detect pcmcia network card on install?"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by TygerTung on 2008-03-05
MY wife has this old Dell inspiron 5000 laptop which has a Xircom Realport Etherenet 10/100+Modem 56 REM56G-100 PCMCIA network card.

I decided to install Xubuntu on it as windows 98 is rubbish and I can't figure out how to make it go on the ADSL network here at home.

I start to install Xubuntu on it but then when it gets to the detect network hardware stage it can't find anything.

Could the problem be that this card is too old and is unsupported? I'm pretty sure it's the card which came with the computer when it was new all those years ago.

Do I need to buy a new card?

Any help would be appreciated!

Cheers,

Sam

---

### Post by jw5801 on 2008-03-05
Did you complete the install? It's not an issue if you can't get a connection during the install process, it just means you'll need to get some updates afterwards rather than during the install process. If you have a complete install open a terminal (Applications > Accessories > Terminal) and run ```
lspci
```

Your network card should show up in the output of that somewhere. If it doesn't then we really have issues. Once it shows up in there it should just be a matter of telling the kernel to use a module. It's strange that it doesn't recognise it during install though.

---

### Post by TygerTung on 2008-03-06
it doesn't appear to show up there, but it is fitted to a pcmcia slot, not a pci slot?

---

### Post by TygerTung on 2008-03-06
I tried the command lspcmcia to see if that would work and it appeard to come up with somthing which looked like it might be the network card on "Socket 0 Device 0 [xirc2ps_cs] after I ejected the card and put it back in again.

Just now I glanced over my shoulder at the router and it appeared to be picking something up on terminal 3 which is the one the computer is plugged into!

I then had a look at the networking icon up on the top left of the screen and lo and behold! it appeared to be connected to the network! I booted up firefox and it seems to be going fine now!

Maybe it was just a bad connection or somthing? terminals a bit dirty? who knows.

All I know that is it a good thing now anyway, thanks for your help!

---

