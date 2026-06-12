---
title: "How to switch from command prompt to user friendly OS?"
date: 2005-07-13
forum: Absolute Beginner Talk
---

### Post by stellaNera on 2005-07-13
Hello all,

as you probably guess I am not a big Linux user. I just installed Ubuntu 5.04 (Hoary Hedgehog) Install CD and all looks fine. ( I have an HP Pavillon, read about some issues, but for now I am happy for what I hava gone so far ).

My simple question is how do I switch from command mode to desktop application (like in the screenshots section)?

I should add that I can boot just fine, and login with no problem as the first user as well.

Thanks in advance.

---

### Post by maruchan on 2005-07-13
what happens when you type "startx"?

---

### Post by stellaNera on 2005-07-13
I get 

- bash: startx: coomand not found


Thanks for the fast reply.

---

### Post by codejunkie on 2005-07-13
if you did a server install that's the reason because it doesn't come with a gui interface by default you have to install it like this ```
sudo apt-get update
``` then ```
sudo apt-get install ubuntu-desktop
```for gnome or ```
sudo apt-get install kubuntu-desktop
``` for kde hope this helps.

---

### Post by stellaNera on 2005-07-13
I am trying the ubuntu-desktop.

It looks like it is unpacking a lot of stuff... really fast. Thanks a lot.

After this installation, is it possible to switch back and forth from Desktop to command prompt?
I really want to learn some Linux commands, and was planning to use the desktop only when I am desperate.

Thanks again.  :grin:  :grin:

---

### Post by codejunkie on 2005-07-13
[QUOTE=stellaNera]I am trying the ubuntu-desktop.

It looks like it is unpacking a lot of stuff... really fast. Thanks a lot.

After this installation, is it possible to switch back and forth from Desktop to command prompt?
I really want to learn some Linux commands, and was planning to use the desktop only when I am desperate.

Thanks again.  :grin:  :grin:[/QUOTE]
yes you can just open a terminal of your choice and run the commands inside of a gui or press ctrl+alt+F1 and this will take you into what your in now, if you prefer having  a command line only  enter-face and you can just re-enter the gui environment by pressing ctrl+alt+F7 hope this helps.

---

### Post by stellaNera on 2005-07-13
hey codejunkie,

thank you so much. I just rebooted my machine and the Desktop version popped up.

I am installing few available updates now.

Thanks.

 :grin:  :grin:  :grin:

---

### Post by codejunkie on 2005-07-13
[QUOTE=stellaNera]hey codejunkie,

thank you so much. I just rebooted my machine and the Desktop version popped up.

I am installing few available updates now.

Thanks.

 :grin:  :grin:  :grin:[/QUOTE]
no problem I'm just happy to be of some use here.

---

