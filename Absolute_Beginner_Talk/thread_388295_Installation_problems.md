---
title: "Installation problems"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2007-03-19
I get to the last step of the install. The installer gets to 63% I think (Not exact) and then freezes up my pc. It was like that all last night. Can anyone help me?

---

### Post by Najand on 2007-03-19
Hmm, maybe there is a failure in installing something. I think it is better you try to install using the "alternative cd-rom".

---

### Post by guru369 on 2007-03-19
Can you post your installer log?

The log is under /var/log/installer/syslog

Thanks.
Dekel

---

### Post by wpshooter on 2007-03-19
Have you checked the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

Did you burn your CD at 4X or less ?

---

### Post by ProjectWhat on 2007-03-19
I tried to find the installer log. It wasnt there. Most likely becuase I had to hold the power button on my PC to turn it off.

<edit> My PC actually froze up. Nothing would move or anything except for the mouse.

---

### Post by H3g3m0n on 2007-03-19
Might have just been a random lockup. Have you tried again?

If X does lock up, you can try to recover by pressing Alt+SysRq+R and then Ctrl+Alt+F1, hopefully this will switch you to a terminal and you can look at the log on the command line or restart the xorg server with "/etx/init.d/gdm restart". If it doesn't you can try the more forceful Alt+SysRq+K to kill the X session (might need Ctrl+Alt+F1 again if you just get a black screen).

Might be worth trying the disk checker on the cdrom to ensure there is no corruption.

---

### Post by ProjectWhat on 2007-03-19
I will try the alternate installation.

---

### Post by aijazbaig1 on 2007-03-19
Hello.

Where exactly is the sysreq button on the keyboard. Is it included by default on all keyboards?? :) ...

---

