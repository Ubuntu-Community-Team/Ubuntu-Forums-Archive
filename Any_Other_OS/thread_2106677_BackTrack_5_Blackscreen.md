---
title: "BackTrack 5 Blackscreen"
date: 2013-01-19
forum: Any Other OS
---

### Post by ProxyCyber on 2013-01-19
So on the live CD the graphical interface loaded but when I installed it,  I typed startx and it was just a blackscreen. How can I "get" the graphical interface to load?  I really want to fix this issue.

---

### Post by oldos2er on 2013-01-19
Moved to Other OS/Distro Talk.

---

### Post by ProxyCyber on 2013-01-19
Okay.. so you moved the topic. I checked there. How does that answer the question? Can someone please help?

---

### Post by haqking on 2013-01-19
> **ProxyCyber said:**
> Okay.. so you moved the topic. I checked there. How does that answer the question? Can someone please help?

No offence but see my siganture ;-)

If you cant get it started it is likely you dont need it.

Backtrack is not a distro for daily desktop use, it is a toolbox for penetration testing and security auditing.

You will be better off looking at the BT wiki or in the BT forums.

Wiki: [http://www.backtrack-linux.org/wiki/index.php/Main_Page](http://www.backtrack-linux.org/wiki/index.php/Main_Page)
Forums: [http://www.backtrack-linux.org/forums/forum.php?](http://www.backtrack-linux.org/forums/forum.php?)

It is likely to be a graphics driver issue, BT uses nouveau by default for Nvidia.

Whether you post here or in the BT forums, people will want more informations such as hardware, usual command outputs, BT release so they know what kernel, x64 or x32, DE chose such as KDE or Gnome etc etc

As a note, everything BT is designed to do is designed and can be done from command line, a GUI is not needed and rarely used to be honest. (as muts would say "learn the /pentest directory first then when if you feel lazy later you can startx"

Peace

---

### Post by Gogsyd on 2013-01-22
I had a similar problem and this is basically how I fixed it:  Post #6 here [http://www.backtrack-linux.org/forums/showthread.php?t=42193](http://www.backtrack-linux.org/forums/showthread.php?t=42193)
 
If you are uncomfortable using vim you can, if I recall correctly, press E at the GRUB menu and add the "text splash vga=791" at the end of your default image.  This should load with a GUI as you had before, albeit temporarily.  You can then use a deifferent text editor to configure GRUB
 
Hope this helps, if not, as haqking says you'll need to provide more info

---

### Post by Cheesemill on 2013-01-22
> **Gogsyd said:**
> If you are uncomfortable using vim you can.....
If you are uncomfortable using vim you shouldn't be trying to use BackTrack in the first place :)

---

### Post by Gogsyd on 2013-01-22
> **Cheesemill said:**
> If you are uncomfortable using vim you shouldn't be trying to use BackTrack in the first place :)
 
True.  And it used to grip me s*** when people on Backtrack forums asked extremely basic questions lol I have to admit though if I have another option than vi/vim I go for it :p

---

