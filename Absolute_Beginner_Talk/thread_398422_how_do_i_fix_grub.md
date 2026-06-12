---
title: "how do i fix grub"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2007-04-01
I have a triboot system. I have windows xp, backtrack and ubuntu 6.06. I use Gparted delted backtrack and installed backtrack2 over it. Now I dont have the grub menu to choose which operating system I want. I know backtrack uses lilo instead of grub. How do I make it use grub instead. As soon as I turn on my laptop the backtrack automatically starts running.  Any help is great. Thanks :)

---

### Post by jenny_psion on 2007-04-01
Hi!

I used to have a problem with my grub too. 
I just overwrote it with my friend's bootloader - problem fixed.

:) psion.

---

### Post by tommcd on 2007-04-01
When you installed lilo it overwrote the MBR and lilo did not detect ubuntu. It should have at least detected windows. This is why I don't like lilo. To reinstall grub from the ubuntu live CD:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
And to reinstall grub from the ubuntu alternate CD:
[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)
Try to reinstall grub with either of those methods.

---

### Post by 3rr0r on 2007-04-01
So I followed the GRUB reinstall directions and everything worked like a charm... except now when I boot up into backtrack, it first takes you to just command line.  There is a file that loads that tells you a few commands and the root/password before it gives you the command line.  The resolution in this "pre-gui" window is terrible now.  Before it used to be great, any ideas on how to fix it?  Is it because it is using GRUB's resolution default (which I don't know what that is)?  Thanks again for the help

---

### Post by tommcd on 2007-04-01
I'm not familiar at all with backtrack. Actually, I never heard of it until I read this thread. Their website looks interesting though.
You may have to consult the backtrack documentation to learn how to get it to boot normally. Sorry I can't help there.

---

