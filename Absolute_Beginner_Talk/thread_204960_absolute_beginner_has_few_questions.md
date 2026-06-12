---
title: "absolute beginner has few questions"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by peanutplanters on 2006-06-27
Hey guys, i just installed Ubuntu as a duel boot onto my laptop to try it out.

My first question is, whats the command to copy things from 1 folder to another? Im following the directions from the WOW wine setup and i dont know how to copy my /media/sda1/Program Files/World of Warcraft to /usr/games.

Secondly, are there any other programs that work like aim/deadaim besides gaim? I want somthing that fades out and has a little better UI.

Lastly, how can i change the boot menu so Windows is the default boot OS. I want my laptop to boot into windows if i let the countdown expire.

Thanks again. :mrgreen:

---

### Post by 23meg on 2006-06-27
> whats the command to copy things from 1 folder to another?It's "cp". Alternatively you can use Nautilus, but to write to /usr you'll need root access. Hit Alt+F2 and type ```
gksudo nautilus
```to run Nautilus as root.

---

### Post by Jagot on 2006-06-27
[QUOTE=peanutplanters]Lastly, how can i change the boot menu so Windows is the default boot OS. I want my laptop to boot into windows if i let the countdown expire.[/QUOTE]

[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by peanutplanters on 2006-06-27
Wow, thanks alot guys. Do you know of any better aim clients besides gaim? Also, is it possible to remote to my linux computer from a windows machine, and if so, what ports does linux use for remote desktop?

---

### Post by skale on 2006-06-27
> sudo cp -rv /media/sda1/Program Files/World\ of\ Warcraft /usr/games/
To boot in windows, not sure, try looking in the BIOS page, press Fsomething when the computer logo comes up. Someone else could probably help you more.

---

