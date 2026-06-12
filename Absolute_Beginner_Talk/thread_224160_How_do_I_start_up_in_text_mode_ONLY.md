---
title: "How do I start up in text mode ONLY?"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-07-27
Hi,

How can I start up in text mode only? I don't mean how to switch to text mode, I know you can do that with CTRL+ALT+F1 and then back with CTRL+ALT+F7. I basicaly don't want X to start. 

Or, if say I have already started in graphic mode and I then switch to text mode and login there, how can I reset X and how can I stop it altogether if I wanted?

Thanks

---

### Post by ErsatzM on 2006-07-27
I think you can just boot up in recovery mode

---

### Post by bensexson on 2006-07-27
If you boot in recovery mode X will not start.  If you want to stop X after boot up.  Just login in text mode and:
sudo /etc/init.d/gdm stop

---

### Post by ovimunt on 2006-07-27
Umm... tried that... X definitely did stop but so did everything else... :-|

Well what actually happened is that I lost all the display. I kept pressing CTRL+ALT+Fx but nothing would show up on the screen... :confused: The computer was not frozen though since the LED of my wireless was still showing data transfer. Plus, when I eventually decided to pressed CTRL+ALT+DEL the HDD led started flashing and the computer restarted properly. 

In conclusion I guess there might be something wrong with my config since once I stop X I loose the display not only graphic but also text.

Any ideas?

---

### Post by steve.horsley on 2006-07-27
To stop X, use > sudo /etc/init.d/gdm stopTo start X use either > sudo /etc/init.d/gdm startor if you just want one session withoutthe login manager, just > startx in which case X will die again when you choose to log out.

To stop X from starting as the machine boots, use this command:> sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/K13gdmand renaming it back again will restore it:> sudo mv /etc/rc2.d/K13gdm /etc/rc2.d/S13gdm

---

