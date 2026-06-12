---
title: "Any way to edit GRUB?"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by civicsi99 on 2007-04-30
when booting up in GRUB, it lists all my previous versions since DD (like 4 i think) and it only gives me 10 seconds to select the OS. is there any way to edit out DD and increase the countdown to select which OS to boot? thanks.

---

### Post by expatCM on 2007-04-30
sudo gedit /boot/grub/menu.lst

---

### Post by starcraft.man on 2007-05-01
and to understand more about grub, the great grub page [here]("http://users.bigpond.net.au/hermanzone/p15.htm") :)

---

### Post by rsambuca on 2007-05-01
> **expatCM said:**
> sudo gedit /boot/grub/menu.lst

Actually it should be ```
gksudo gedit /boot/grub/menu.lst
```

You can either delete the entries you don't want to see (but they will show up after the next kernel upgrade)
or, you can change the line that says:  how many 
to 1, and it will only show the last kernel.
Another option is to put a # in front of the lines you don't want read by grub.

And the last option would be to open up the Synaptic package Manager and remove the old linux-image files.  Just make sure that everything is working properly with the new kernels if you are going to remove the old ones.

---

### Post by civicsi99 on 2007-05-01
ok i got the countdown edited, but how do i get rid of all previous kernels? can i just uncomment them in gedit? thanks for your help.

ps........do i just save the edited file as the same filename or name it something different?

---

### Post by rsambuca on 2007-05-01
> **civicsi99 said:**
> ok i got the countdown edited, but how do i get rid of all previous kernels? can i just uncomment them in gedit? thanks for your help.

ps........do i just save the edited file as the same filename or name it something different?

Yeah, you have to resave it as /boot/grub/menu.lst

Also, keep in mind that you only need to hit an arrow key during the countdown and it will stop the clock.  You can then take your time selecting the OS of your choice.  You can also change the default OS to whatever you wish.

---

### Post by civicsi99 on 2007-05-01
thanks for the help guys, that link was very helpful and i think ive got it nowl

---

