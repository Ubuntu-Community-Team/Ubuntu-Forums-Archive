---
title: "How to Install 2.6.17.11 ???"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2007-02-20
I've just re-installed Edgy on one of our computers but the CD I used only had the kernel version 2.6.17.10.
Although I have run the "sudo update" and the "sudo upgrade" commands, the kernel was not upgraded to 2.6.17.11

Do I have to wait for this to show up in the notification icon before I can install it or is there some other way?

Thanks
Paul

---

### Post by Bachstelze on 2007-02-20
You cannot switch kernels while the system is running. To use another kernel, you need to reboot your machine.

---

### Post by madmetal on 2007-02-20
you mean sudo apt-get update and sudo apt-get upgrade..
did you see the 2.6.17.11 at the updates?
did you reboot after updates installed?

---

### Post by PaulFXH on 2007-02-20
Thanks for the replies.
Yes, I did mean sudo apt-get install (or upgrade) but I just used an abbreviation.

Yes, I HAVE rebooted my machine quite a number of times since the upgrades/Updates but there is no sign of kernel 2.6.17.11

No, I did NOT see any mention of 2.6.17.11 during the upgrade process. However, this machine already HAD 2.6.17.11 until I did the re-install about 2 hours ago.

Is there no way, other than waiting for the notification icon to alert me to it, that I can upgrade to 2.6.17.11 now?

---

### Post by madmetal on 2007-02-20
go system >> administration >> update manager and check for updates..
just in case there is something wrong with it..

---

### Post by PaulFXH on 2007-02-20
OK, it was in the list provided by the update manager and I've got it installed now.
However, still don't understand why it didn't install when I did the upgrade and install.
Just one more thing to add to the very large list of things I don't understand.
Thanks for your advice
Paul

---

### Post by madmetal on 2007-02-20
i am glad i helped even though i also dont know why this happened..
but its always good to know where to look for the problem (linux thing :) )

---

### Post by Bachstelze on 2007-02-20
Because *apt-get upgrade* never installs new packages. You should have run *apt-get dist-upgrade*.

---

### Post by PaulFXH on 2007-02-20
OK, thanks for the explanation
Cheers
Paul

---

