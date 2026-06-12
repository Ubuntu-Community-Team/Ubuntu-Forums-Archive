---
title: "Password problems"
date: 2005-06-28
forum: Absolute Beginner Talk
---

### Post by AntiDragon on 2005-06-28
Hi

Despite a previous on/off relationship with Linux (And it's now definitely ON - XP has thrown it's last tantrum as far as I'm concerned!), I still pretty green with it. I was wondering if someone could help? :) 

I've got two user accounts set up, one during install and the other I set up through the GUI (Users and Groups). I went in yesterday to grant the second account Administrator rights - I'm guessing this adds her to SUDO? and no probs. But now I can't logon to either accounts. I *did* reset the second account's password but I certain I didn't get it wrong - no caps lock either (I tried it both ways anyway). What's more worrying is how my own account seems to have had the password altered as well.

Does anyone know what may have happened? Am I going to have to boot from CD and reset the passwords? And if so, which file is it again?  :?

Thanks!

---

### Post by fdoving on 2005-06-28
[QUOTE=AntiDragon]Hi

Despite a previous on/off relationship with Linux (And it's now definitely ON - XP has thrown it's last tantrum as far as I'm concerned!), I still pretty green with it. I was wondering if someone could help? :) 

I've got two user accounts set up, one during install and the other I set up through the GUI (Users and Groups). I went in yesterday to grant the second account Administrator rights - I'm guessing this adds her to SUDO? and no probs. But now I can't logon to either accounts. I *did* reset the second account's password but I certain I didn't get it wrong - no caps lock either (I tried it both ways anyway). What's more worrying is how my own account seems to have had the password altered as well.

Does anyone know what may have happened? Am I going to have to boot from CD and reset the passwords? And if so, which file is it again?  :?

Thanks![/QUOTE]
 It's hard to tell what could have caused the problem.

I suggest you reboot your computer, and in the boot-menu (GRUB) you select the Recovery option.
That will boot your system into a root shell. where you can reset the users password with the command:

'passwd username'


When you're done you can reboot the system with  the command 'reboot' 


- Frode

---

### Post by AntiDragon on 2005-06-28
Ah, so no CD? Cool. I'll try that when I get back from work.
(It's a good job I resisted the urge to comment those recovery kernels out of GRUB...!  ;-) )

---

