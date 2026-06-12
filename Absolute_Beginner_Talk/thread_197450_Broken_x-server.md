---
title: "Broken x-server"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by codesplice on 2006-06-15
Hey all,
I'm desperately in need of some help now.  I recently re-installed 
Ubuntu after running into a very similar problem just two days ago, and 
I managed to break something again...  Fresh install of Dapper, so I had 
been downloading and updating a number of packages.  I the process, I 
believe I downloaded an updated kernel, and was given the message that I 
needed to reboot.  So I did.

First alarms went off in my head when I was greeted not by the pretty 
Ubuntu graphical login screen, but by a text login prompt.  "Okay, I can 
get around this..."  I log in, and run startx.  It runs, but there's 
nothing actually showing up.  I've got a neutral background and a cursor 
- that's it.

I can't for the life of me get X to start as it should - and I'm new 
enough that I don't know all the fancy config files that I should be 
looking in.

Can someone please point me to some files to examine to get my X 
functionality back?  

Thank you SO very much.

---

### Post by muep on 2006-06-15
Because you didn't get your graphical login, there is probably something wrong with the xorg config.

The config is stored in /etc/X11/xorg.conf . However, you probably don't need to edit it by hand.

First, try ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

It should make a new config for you, automatically. Then,

```
sudo /etc/init.d/gdm restart
```

This restarts GDM, the graphical login manager, which also starts X. Or at least it tries :)

If you don't get graphics by now, try

```
sudo dpkg-reconfigure xserver-xorg
```

,which runs the x server reconfiguration again. The difference is that now you have to answer the questions. In the beginning, there are different drivers available, try at least vesa. If you have an ATI card, you can also try ati or radeon, or possibly fglrx if it is installed. Nvidia user can try nv or nvidia.

Most of the questions can be answered just by accepting the default.

After each reconfiguration, restart GDM as described above.

---

### Post by codesplice on 2006-06-15
Thanks a lot for the reply, but it's still no good :(

I went through those steps, and try to restart gdm a few times, and never had any luck.  After typing that gdm restart command, it just went back to the terminal prompt.  Tried startx again (after reconfiguring the xserver) and still no luck.  

It seems that one of the packages I downloaded may have messed up my x settings, but I don't have a clue which one (otherwise I'd uninstall that package).  

Any other suggestions?  I'd hate to have to re-install again - it's getting really old.

---

### Post by codesplice on 2006-06-15
Well, I fixed it, I think.  I ended up re-installing ubuntu-desktop and then reconfiguring and restarting gdm:

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

With luck, this will still work after I reboot!

Thanks for the input :)

EDIT: Rebooted, and it worked fine.

---

### Post by mahesh_sonawane on 2006-06-23
Hello,
I am also facing the same problem....
I have done similar but when I put the command
sudo /etc/init.d/gdm start[/CODE]
Then it gives the message as follows
* Starting GNOME Display Manager...                [fail]
Please, give me the solution.
Thank you

Mahesh

---

