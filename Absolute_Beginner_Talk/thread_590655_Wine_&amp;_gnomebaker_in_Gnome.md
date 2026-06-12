---
title: "Wine &amp; gnomebaker in Gnome"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by custommadename on 2007-10-24
I have Gnome installed as the GUI, and I've been trying to use the terminal to install wine & gnomebaker.  Here's what I've got:

sudo apt-get install (either app)
I let both work through the initial quickly-scrolling steps, but I forgot what to do next.  It's been a while since I've used Ubuntu, and I just reinstalled this OS.  Could you please help me out?

Thanks a lot!

---

### Post by TeaSwigger on 2007-10-25
You can safely use Synaptic until you're reacquainted, that's my suggestion. 

First make sure you have the repositories you want. Then sudo apt-get update. Run sudo apt-get upgrade to update the existing goods. To install run sudo apt-get install [app name] if you know the app's full name. Alternately look up the name either in Synaptic or at ubuntu's package archive site [http://packages.ubuntu.com/](http://packages.ubuntu.com/) . It will tell you if dependencies are required, offer to install them for you, and may ask you if it should proceed. You'd agree and it'll do all the work for you. When it returns you to the command line, it's installed.

Gnomebaker's real easy. WINE though... in a command line run 
```
wineprefixcreate
``` and then ```
winecfg
``` to open the configuration gui and to finish setting it up. 

You'll get the hang of it again ;)

---

### Post by custommadename on 2007-10-25
All right, I think I'm getting along now.  I've used the Applications menu's Add/Remove to add a bunch of programs, and my desktop looks so awesome.  It feels so good to use Ubuntu again.  Thanks!

---

