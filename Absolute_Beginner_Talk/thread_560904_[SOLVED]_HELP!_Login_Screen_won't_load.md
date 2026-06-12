---
title: "[SOLVED] HELP! Login Screen won't load"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by calebash82 on 2007-09-26
Hey all!

Ex Windows wiz here. Wanting to convert to the light-side of the force!

I made the following changes to the login window under System>administration:

*<Local>

- Changed the login screen to "happy GNOME with Browser"

- Changed the welcome message to something.... possibly a Star Wars or a BSG quote

*<Security>

- Allowed local system administrator login
- I can't remember if I changed the permissions or not... I don't believe I did.

Anyway, now that I've set the mood, here is the problem.

When I load up Ubuntu, the regular stuff all goes okay until the GUI loads up, the Screen Resolution changes/flickers and then all I see is that mouse cursor telling me I'm waiting for stuff to load. There is minor Hard Drive activity and nothing happens. I once left it overnight with no avail. I Hit the <Ctrl>+<Backspace> button to see the terminal and noticed the loading of the firewall FAILED (in red) and that seemed to be the only thing wrong.

Can anyone help? I was wondering is it possible to rollback changes, load the last good config, maybe repair the installation? Anything like that?

Cheers guys!

Anthony

---

### Post by jfinkels on 2007-09-27
> **calebash82 said:**
> Hey all!

Ex Windows wiz here. Wanting to convert to the light-side of the force!

I made the following changes to the login window under System>administration:

*<Local>

- Changed the login screen to "happy GNOME with Browser"

- Changed the welcome message to something.... possibly a Star Wars or a BSG quote

*<Security>

- Allowed local system administrator login
- I can't remember if I changed the permissions or not... I don't believe I did.

Anyway, now that I've set the mood, here is the problem.

When I load up Ubuntu, the regular stuff all goes okay until the GUI loads up, the Screen Resolution changes/flickers and then all I see is that mouse cursor telling me I'm waiting for stuff to load. There is minor Hard Drive activity and nothing happens. I once left it overnight with no avail. I Hit the <Ctrl>+<Backspace> button to see the terminal and noticed the loading of the firewall FAILED (in red) and that seemed to be the only thing wrong.

Can anyone help? I was wondering is it possible to rollback changes, load the last good config, maybe repair the installation? Anything like that?

Cheers guys!

Anthony

<Ctrl>+<Alt>+<Backspace> will restart the X server (the graphical windowing system).

<Ctrl>+<Alt>+<F1 through F6> will bring you to one of the six virtual terminals.

As for your question, what is the exact error message you see?

If you are willing to try to reconfigure your X server (the graphical windowing system), type the following in a terminal:```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by nowshining on 2007-09-28
"Allowed local system administrator login"

that means that you allowed root to login via the gui logon prompt - you don't want root, :) the username for root is root and if you haven't got one then disable it which is best. There is NO NEED to run as root to run programs ,etc.. and most stuff for root can be dune in the terminal via sudo or to use the root account you can su root

gksudo nautilus in the terminal will give you root access thru the gui nautilus disk browser.

---

### Post by calebash82 on 2007-09-28
Hello gentleman, 

Thanks for the info nowshining I really appreciate the education ;-)

Jfinkels, I did as you suggested and followed the prompts. There  was nothing there that helped my issue sadly. I did reboot and see but still the same problem. Luckily I still Windows *shudders* XP still on dualboot.

Is there a way I could manually UNDO the changes I've made if someone can walk me through it or give me the code?  Cheers.

Failing that, if I can get access to my user files and get stuff from "my documents" that would also be great even if it means I have to do a reinstall.

Cheers!

Calebash82

---

### Post by jfinkels on 2007-09-29
> **calebash82 said:**
> 
Failing that, if I can get access to my user files and get stuff from "my documents" that would also be great even if it means I have to do a reinstall.


You can access your files in a couple of ways:

1. Boot into the Ubuntu LiveCD environment, make sure both the Ubuntu partition and the Windows partition are mounted (you may need to install the ntfs-3g drivers to access an NTFS partition [i.e. your Windows partition]), and copy any files you want from the Ubuntu partition to the Windows partition.

2. Boot into the Ubuntu LiveCD, make a new partition, copy all files you want to keep over (or choose to make a separate /home partition [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)) and then reinstall. Then once you have reinstalled, mount the partition and you will have access to your files.

3. Install ext3 drivers for Windows [http://www.fs-driver.org/](http://www.fs-driver.org/) and access your files from Windows.

---

### Post by calebash82 on 2007-10-05
Hey all thank you for your kind support. I have backed up the files I needed to in order to wipe and reinstall my UBUNTU installation thanks for all your help. I will try and work out a way of gettting back my emails on firefox but I have the files backed up nevertheless

Cheers again! :-)

---

