---
title: "Black screen after boot"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by macdo on 2006-11-25
So I came to boot up this morning, and although everything seemed to go fine, I ended up with a black screen (the lights are on, just nobody at home). Now I'm not aware of having done any strange config recently. I can boot in recovery mode, and get a prompt, but I'm not a CL genius...
I have tried remplacing my xorg.conf file with a backup, no joy. I've tried running dpkg-reconfigure xserver-xorg (or a command to that effect, I can't remember it off hand), no luck.
The only things I've installed recently (i.e. since the last time I rebooted) are nethack and superkaramba. 
Now I'm using lynx to post this, and I really need a hand... 
Any ideas?

---

### Post by klaus_15 on 2006-11-25
The same is happening to me, I tried everything. However, recently I have noticed that if I wait several seconds after the black screen appears, the system asks me to login but in text mode. I only can login as root, because I get an error logging in as a normal user. Then, I write the command "startx" and the graphical interface starts. A message appears on the screen, something about power management (gestión de energía, my system is in spanish). I click OK. Everything seems OK, but I can't run some admin tools -the root is unable to access to users-admin or add a printer by default- and, of course (?) I can't change the user. Then I want to shut down. The same message about power management, but I can't close the message window. I wait a bit, and the options (hibernate, change user, log out, shut down, reboot) appear, some of them. Then I can shut down. It's all very strange. Why can I start the graphical interface by the command line, but not automatically after boot?? Why the power management message at start and when i want to shut down?? In a spanish ubuntu unofficial (is this a word?) forum I read about some people with the same problems, but the answers to their topics couldn't help me.I hope somebody could help us. Sorry for my English!

---

### Post by jerrykenny on 2006-11-25
macdo, if you log in root and type <startx> what output does it spit out at you ? 

Also at the grub prompt press <e> to edit your boot parameters, then remove the "splash" option, then you'll get some info from your screen as to whats actually happening at boot time . .

Maybe its just a daft thing like the mouse not being detected ? but you need to run startx to find out

---

### Post by macdo on 2006-12-01
Thanks for your interest. In the end, I reformatted and reinstalled, with a 32 bit system - 64bit just isn't quite there yet, so I'll wait for Feisty before going back to it.

---

