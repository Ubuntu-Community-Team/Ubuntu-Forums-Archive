---
title: "Help"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by simple1 on 2005-10-09
I know this is a idiot question, but I been told not to pull the plug on a Linux system.

Then what are you supposed to do with a frozen computer?  And how?

---

### Post by Kyral on 2005-10-09
Well, its safer to "pull the plug" on a Linux system than it is on a Windows system (GO GO GADGET JOURNELED FILESYSTEM!)

That being said its not the best way to shutdown a machine, but if its absolutely frozen (try hitting CTRL+ALT+F1 and see if you can pop to a Virtual Terminal. CTRL+ALT+F7 will get you back to X) then go ahead.

If you can get to a terminal, login and force X down with "sudo /etc/init.d/gdm stop" and then start it again with "sudo /etc/init.d/gdm start"

---

### Post by simple1 on 2005-10-09
Thanks for responding; didn't think anybody would.
At one point I tried alt-control and all the F-keys and one terminal came up working - loged as root, and a working curser.  Then I shutdown and restarted; still don;t know which F-key.
thanks

---

