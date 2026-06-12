---
title: "failed to initalize HAL! error iBook G4"
date: 2008-07-25
forum: Apple Hardware Users
---

### Post by lukerz8 on 2008-07-25
I was updating ubuntu from 7.10 to 8.04 through the update manager, nothing weird, and the update manager was stuck on 12 minutes for about an hour, so i shut down the computer (held the power button) and after i logged on, it just sat there with the default tan colored screen and nothing else except the mouse. did a ctrl alt backspace (which seems to log you out) and this time selected the failsafe GNOME session option. this time i got the desktop, but there's this internal error 'failed to initialize HAL!'.

My computer is a iBook G4 1.2 ghz.

---

### Post by stream303 on 2008-07-25
Although there have been some success stories with a distro upgrade, I have found that for peace of mind, it is just better to do a clean install for ppc especially, and even more so for an LTS.

I also had a G4 iBook like yours, and found that Network Manager was giving me fits, but only on that iBook.  Use top, or htop, to see if NM is eating up all your cpu cycles.  If so, and if you can live without it, perhaps disabling it (System > Preferences > Sessions).  If you don't use Evolution, or need it's alarms, you can also disable Evolution notificaton alarms from there too.

---

### Post by lukerz8 on 2008-07-25
ok, if i can't get the installation fixed I guess I'll just have to do a clean install. I don't really want to do this though because it has taken me a long time to get the iBook to run the way it is. Is there any way to update ubuntu from a cd? i was reading somewhere that you can do that with the alternate distribution cd.

Something I forgot to clarify originally, the computer will not log in to the default boot option (which is option 1 in the session menu named Run Xclient script). All it does when i log into this session option is show a tan screen with the mouse in it. Because of this, just to get to the desktop I have to use the GNOME option to log in. Not much seems to work correctly in this session option, including internet connection.

---

### Post by stream303 on 2008-07-25
Normally inserting another install image brings up a window that asks if you want to update to to the packages inside it.  I have never gone this route on ppc, so I can't verify it.

One thing that tripped me up before was when flying through an install is to make sure that you DON'T choose firewire as the ethernet port when that option comes up, as you can set up for "ethernet over firewire", which one normally doesn't want.  Could this have happened?

---

