---
title: "failed to start x server"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by gkrugerradar1 on 2006-03-16
Installed ubuntu 5.10 on my notebook. Ubutu almost loads, then the message "failed to start x server" and I end up at the command prompt. I never have got to the ubuntu screen. Checking the forums, I understand that my ati video card could be the problem. My problem is that i can't get the command line to work. Is there a simple tutorial for ubuntu command prompt how to? Am I on the right track?

---

### Post by incubus on 2006-03-16
Have you tried this:
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI")

...using the Ubuntu provided drivers, not ATI's.

Tell us what you get.
By the way, the command line is working, right? CTRL+ALT+F1 should bring you to one of the terminals, if you're not there. CTRL+ALT+F7 is the one for the X server display.

incubus

---

### Post by mlind on 2006-03-16
if you don't get it to work, post your /var/log/Xorg.0.log

---

### Post by gkrugerradar1 on 2006-03-16
I'm not sure if the command line is working. ctrl+alt+f1 does nothing. As I was saying, I have never got to the gui.

---

### Post by gkrugerradar1 on 2006-03-16
At the command prompt, whenever enter is hit, it takes me back to the log in screen.

---

### Post by mlind on 2006-03-16
if you press Ctrl+Alt+F1 and login the terminal using your username and password,
can you view the file /var/log/Xorg.0.log ?

```

less /var/log/Xorg.0.log

```

try to post the contents of this file here.

---

### Post by gkrugerradar1 on 2006-03-16
Thanks a lot gentlemen. Success at last. Let the learning begin. All is normal and good.\\:D/ \\:D/

---

