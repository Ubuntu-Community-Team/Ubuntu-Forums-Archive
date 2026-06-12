---
title: "Xubuntu equivalent of windows My Computer properties"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by dmeehan on 2006-08-25
Can someone thell me how (on Xubuntu) I would do the equivalent of this in windows: Right click on My Computer and select Properties
?


Basically I want to see what memory and CPU is in my pc (its an old one I got free so I have no idea what is under the hood).


Cheers!

---

### Post by muep on 2006-08-25
In the terminal, you can use this command:

top

to see some info of the system. The processor info can be obtained with this:

cat /proc/cpuinfo

---

### Post by dmeehan on 2006-08-25
as easy as that, thanks!

---

### Post by muep on 2006-08-25
No problem, nice that it works :)

free -m also quickly shows the memory state, if top feels a bit cluttered.

---

### Post by dmeehan on 2006-08-28
how can i find out the type of memory it uses (eg SDRAM)
I want to buy more memory for my xubuntu pc but I dont want to buy the wrong/incompattible type

any ideas?


(i suppose i could just open up the pc as i would have to do it at some stage to install the new memory)

---

### Post by Fedz on 2006-08-28
I was wondering the very same thing earlier today ...

I'm sure it says on the RAM (when you get too open-up the PC that is).

Saves taking it out and risking braking it tbh :)

---

### Post by Mimsy on 2006-08-28
This is just a wild shot in the dark, but... does the scanner at [www.crucial.com](www.crucial.com) work on Linux? I know it works with Firefox, once you've downloaded and installed the thing.

/Mimsy

---

### Post by Metacarpal on 2006-08-28
> **dmeehan said:**
> how can i find out the type of memory it uses (eg SDRAM)
I want to buy more memory for my xubuntu pc but I dont want to buy the wrong/incompattible type

any ideas?


(i suppose i could just open up the pc as i would have to do it at some stage to install the new memory)

Was your computer custom-built or does it have a model number?  If you have a model, you can often determine the memory type by doing a google search for the model number and "RAM"

---

