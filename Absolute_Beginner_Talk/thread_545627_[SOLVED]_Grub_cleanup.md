---
title: "[SOLVED] Grub cleanup?"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2007-09-07
I would like to know how to, remove/make invisible, a lot of things on my boot screen. As it is now, I have to scroll through a lot of Mem Test, recovery mode listings, 9 clicks in all, in order to get to Win XP. On those rare occasions when I have to visit MS, that is.

Outside of all the clicking, it just looks sloppy.

Many thanks,

Jon

---

### Post by overdrank on 2007-09-07
> **Romin-1 said:**
> I would like to know how to, remove/make invisible, a lot of things on my boot screen. As it is now, I have to scroll through a lot of Mem Test, recovery mode listings, 9 clicks in all, in order to get to Win XP. On those rare occasions when I have to visit MS, that is.

Outside of all the clicking, it just looks sloppy.

Many thanks,

Jon

Hi and I think this link will help you
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
Good luck! :KS

---

### Post by banewman on 2007-09-07
You can edit the file that controls all that.
 At the terminal - applications-terminal - type :
 sudo gedit /boot/grub/menu.lst (that is small L s t)
then enter password at the prompt
That will bring the file up in a form where your edits will be saved
Now scroll right to the bottom, you will notice that op systems come in blocks of several lines. For the ones you don't want to see you can put a "#" at the front of the lines and that will comment them out of the boot display. I recommend that you keep one recovery partition in case of trouble. Remember to comment every line in a block entry for an op system. :)

---

### Post by overdrank on 2007-09-07
> **banewman said:**
> You can edit the file that controls all that.
 At the terminal - applications-terminal - type :
 sudo gedit /boot/grub/menu.lst (that is small L s t)
then enter password at the prompt
That will bring the file up in a form where your edits will be saved
Now scroll right to the bottom, you will notice that op systems come in blocks of several lines. For the ones you don't want to see you can put a "#" at the front of the lines and that will comment them out of the boot display. I recommend that you keep one recovery partition in case of trouble. Remember to comment every line in a block entry for an op system. :)

I would recommend using 
gksudo gedit

 [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by banewman on 2007-09-08
Sudo gedit is the recommended syntax in every ubuntu doc I've seen. They never mention gksu - but that terminology does turn up in a lot of threads. The difference? :)

---

### Post by Romin-1 on 2007-09-08
Thanks Guys,

I got it tidied-up nicely now...

Jon

---

### Post by overdrank on 2007-09-08
> **banewman said:**
> Sudo gedit is the recommended syntax in every ubuntu doc I've seen. They never mention gksu - but that terminology does turn up in a lot of threads. The difference? :)

Hi this is what I have found
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[/QUOTE]You should never use sudo to start graphical programs unless you know exactly what you are doing. You should use gksudo or kdesu to run such programs (e.g. ALT+F2 gksudo nautilus).[/QUOTE]

---

### Post by banewman on 2007-09-08
When it comes to /boot/grub/menu.lst I have never seen a reference to editing it that did not use sudo. Thinking about it the only reference to gksu I have seen is with regards to update-manager. But my experience is limited - seven years with linux and usiing anything but gksu (even with update-manager, but that is because I keep forgetting - silly me).

---

