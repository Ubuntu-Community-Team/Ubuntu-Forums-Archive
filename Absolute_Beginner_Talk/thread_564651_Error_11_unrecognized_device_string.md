---
title: "Error 11 unrecognized device string"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by path_finder on 2007-10-01
Hi,

I just edited my menu.lst file. I have installed both xp and ubuntu. when i am trying to boot from ubuntu
it says "Error11:unrecognized device string, Press any key to continue"
I want to go back to ubuntu without installing it again. I am new to ubuntu, so please be kind inough to explain everithing briefly. (i read previously posted threads regarding to this, but cant understand)

Thanks!

---

### Post by sirgogo on 2007-10-02
Hey:

I have the same setup (XP and Ubuntu). After my installation everything was working fine for me.

Later, though, I messed up my xorg.conf file (includes graphic drivers) and I used to get that error when trying to start the X (window manager). Try recompiling your kernel, or installing a new graphics driver through the terminal.

I'm not sure what else it might be based on your description, so let me know how it goes. Good luck!

---

### Post by path_finder on 2007-10-03
I dont knw how to do that friend. So can you please tell me the way I should do it?

Thanks in advance !

---

### Post by sirgogo on 2007-10-03
Alright:

I need to know if it lets you do *anything*... meaning that does it let you log in as root through the terminal?

If not, heres what I suggest you do:

Boot from a LiveCD, start up the terminal and type:

```
$sudo dpkg-reconfigure -phigh xserver-xorg
```

Then select your driver, follow the steps, let it recompile your kernel, and see what happens. Good luck man, hope it works ;)

---

### Post by Hospadar on 2007-10-03
> **sirgogo said:**
> Try recompiling your kernel, or installing a new graphics driver through the terminal.



Nopers! that would be painful.

Your problem I'm almost certain is that you probably accidentally made a mistake on the boot file you edited.  You should boot off the livecd and attempt to fix it.  alternatively going to the grub website and getting their cd and reinstalling grub should solve the problem.

The problem isn't with your xserver (that controls the graphics and has nothing to do with booting)

---

### Post by sirgogo on 2007-10-03
Yeah, you're probably right. I wasn't too sure what the situation was from the description.

Does "Error 11 unrecognized device string" always translate to a bad install of GRUB?

---

