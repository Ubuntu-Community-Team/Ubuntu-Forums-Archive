---
title: "Problem with file permissions [Resolved]"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by RBird on 2007-02-10
I have recently installed Ubuntu 6.06 on my Travelmate C300 tablet PC. I would like to enable the pen functions on this computer. I found a tutorial to enable the Wacom drivers and followed the instructions. I was to make changes to "xorg.conf" and save them. 

I followed the directions and everything worked fine until I tried to save the file. I received a message stating that I don't have the correct permissions to save the file. I do not know how to change permissions to allow me to do this.

I am the person who installed Ubuntu on the computer and I thought I had all the permissions I needed to be "administrator" (not sure if that is the right term in Linux). What am I missing?

I realize the answer is probably very easy, but I am new to Linux and am still dealing with the learning curve. Any help would be greatly appreciated - even if simply pointing me to another webpage with the answer.

Thanks.

---

### Post by 23meg on 2007-02-10
You'll need to use *sudo* and *gksudo* (which is the equivalent of *sudo* for graphical apps) to temporarily get root status in order to edit configuration files such as xorg.conf that you (as a regular user) don't have write access to. ```
gksudo gedit /etc/X11/xorg.conf
```will do.

More on sudo [here]("https://help.ubuntu.com/community/RootSudo").

---

### Post by nickoli_02 on 2007-02-10
Welcome to linux :) In fact you aren't the only user on your computer: there's you and there's root. Root is the equivalent to windows' "administrator" user. For security reasons you are not automatically given root privileges, and it's actually very unsecure to be logged in as root user for long periods of time (good old windows). Whenever you need to root privilege use "sudo <command>" for terminal commands or "gksudo <command> " for commands which open graphical apps.

---

### Post by RBird on 2007-02-11
> **23meg said:**
> You'll need to use *sudo* and *gksudo* (which is the equivalent of *sudo* for graphical apps)

Thank you very much for the advice. I was using "sudo" when I should have used "gksudo". I tried it again and it worked like a charm.

Thanks again.

---

