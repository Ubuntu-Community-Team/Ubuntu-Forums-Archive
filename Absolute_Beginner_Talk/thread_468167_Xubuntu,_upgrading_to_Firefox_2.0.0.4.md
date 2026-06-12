---
title: "Xubuntu, upgrading to Firefox 2.0.0.4"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by casals on 2007-06-08
I have Xubuntu/Feisty on an IBM TP 600x (500mhz, 192MB). (Fresh install from regular live CD, last Sunday.) This morning Update Manager suggested I let it go update Firefox to 2.0.0.4. The update was agonizing, took over an hour, machine completely unresponsive. It finally finished, with the window manager frakked -- ctl-alt-backspace to restart. Seemed ok then, so I started Opera (my browser of choice). Once again, heavy heavy disk use, machine so tied up I can't even move the cursor. It did this for about an hour, so I finally did ctl-alt-backspace again and shut the maching down. Booted back up, ran some little things, started Opera, it seemed ok. Then I clicked to start Firefox, and once again, hard drive grinding and grinding, an hour has passed, the machine is unresponsive, and Firefox hasn't even appeared yet ...

What to think? This is an old machine with not so much memory, but Firefox from the installation didn't do this. I have the tool bar system resources thingy, and it says I'm using 115MB out of 186MB, and no use of swap.

---

### Post by kittyhawk63 on 2007-06-08
.

---

### Post by bapoumba on 2007-06-09
> **casals said:**
> I have Xubuntu/Feisty on an IBM TP 600x (500mhz, 192MB). (Fresh install from regular live CD, last Sunday.) This morning Update Manager suggested I let it go update Firefox to 2.0.0.4. The update was agonizing, took over an hour, machine completely unresponsive. It finally finished, with the window manager frakked -- ctl-alt-backspace to restart. Seemed ok then, so I started Opera (my browser of choice). Once again, heavy heavy disk use, machine so tied up I can't even move the cursor. It did this for about an hour, so I finally did ctl-alt-backspace again and shut the maching down. Booted back up, ran some little things, started Opera, it seemed ok. Then I clicked to start Firefox, and once again, hard drive grinding and grinding, an hour has passed, the machine is unresponsive, and Firefox hasn't even appeared yet ...

What to think? This is an old machine with not so much memory, but Firefox from the installation didn't do this. I have the tool bar system resources thingy, and it says I'm using 115MB out of 186MB, and no use of swap.

Older computer here too.
```
~$ aptitude show firefox
Package: firefox
State: installed
Automatically installed: no
Version: 2.0.0.4+1-0ubuntu1
Priority: optional
Section: web
```
Just tried it, running fine here. Any plugin enabled ? Please try to remove them.

---

### Post by casals on 2007-06-11
Thanks, Kittyhawk, bapoumba -- 

I uninstalled Firefox completely. The system was still very unresponsive; the xfce toolbar widget continued to say no swap, although qtparted showed a swap partition (533mb, my ram is 192). 

So I did a complete reinstall of Xubuntu. I put the toolbar widget back, and it's showing consistent, and changing, use of swap. The system seems responsive so far, even with heavy use of the browser. 

Is it possible for something to make swap invisible to the system? How could I tell?

---

### Post by bapoumba on 2007-06-11
> **casals said:**
> Thanks, Kittyhawk, bapoumba -- 

I uninstalled Firefox completely. The system was still very unresponsive; the xfce toolbar widget continued to say no swap, although qtparted showed a swap partition (533mb, my ram is 192). 

So I did a complete reinstall of Xubuntu. I put the toolbar widget back, and it's showing consistent, and changing, use of swap. The system seems responsive so far, even with heavy use of the browser. 

Is it possible for something to make swap invisible to the system? How could I tell?
Sorry I missed the mention to swap in your previous post. One thing you could have checked (before reinstall...):
```
~$ free
             total       used       free     shared    buffers     cached
Mem:        499724     446368      53356          0      22756     192048
-/+ buffers/cache:     231564     268160
Swap:       931760          0     931760

```
To see if the swap was correctly used and look in fstab (**cat /etc/fstab**) to see if correctly set up.

---

### Post by eeried on 2007-06-27
Why would one use Automatix to install a package that's in the Ubuntu repositories?

in Xubuntu, you can use the command line to update and upgrade -- it's faster.

---

### Post by Bartender on 2007-06-27
Would adding some memory be horribly expensive and/or a hassle?  Betcha 512 of RAM would make a huge difference...

---

