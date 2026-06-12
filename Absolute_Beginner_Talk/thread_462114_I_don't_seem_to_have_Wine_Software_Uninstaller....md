---
title: "I don't seem to have Wine Software Uninstaller..."
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-06-02
Hi, I'm in Ubuntu Studio and I don't seem to have Wine Software Uninstaller installed. (Obviously, I do have WIne). But I understand that if you have Wine, the uninstaller should be there also.

I know how to find it, because I have Ubuntu Feisty on my laptop and I see it under Applications/System Tools/Wine Software Uninstaller....

But it's not there in Ubuntu Studio... Maybe this is just a newbie thing, but thanks for any assistance,....Frank B.

---

### Post by jonward0690 on 2007-06-02
Well if you ever want to remove wine just type"sudo apt-get remove wine"

---

### Post by Brightbelt on 2007-06-02
Thanks for responding. Actually I don't want to remove Wine; I want to remove a program which I installed thru wine that isn't working.

That's why I want the wine software uninstaller....Thanks, Frnak

---

### Post by zvacet on 2007-06-02
I don´t use Studio but you can look under **programs>accessories **or **system> settings**

---

### Post by Brightbelt on 2007-06-02
Thanks, Frank

---

### Post by Brightbelt on 2007-06-02
Thanks for responding. I've learned that Ubuntu Studio and Ubuntu Feisty do have very slightly different menu options. It's subtle but it's there.

I have looked under both Accessories and all the System menus.

Thanks again for responding, Frank B.

---

### Post by Brightbelt on 2007-06-02
What I'm actually trying to do is to remove the Fireworks 4.0 program which I installed under wine. 

FYI, it seems to be a problem only in Ubuntu Studio; it actually it runs well so far as I can tell with Ubuntu Feisty.

If I could use the 'sudo apt-get remove' command with a wine program, someone could help me by telling me how to address a program in the wine directory with that command. Would that work?  

Thanks, Frank B.

---

### Post by fabertawe on 2007-06-05
try this from a terminal...
```
uninstaller
```

Paul

---

### Post by Big_Croc7 on 2007-06-05
'sudo apt-get remove' won't work with a program in wine, since apt only keeps track of programs installed through apt (or aptitude, or synaptic/adept etc.).  You could delete the directory it's installed in - this will remove the program and free up the space on your hard disk (although the settings will still be kept in the 'wine registry').

---

### Post by ccfjeff on 2007-06-05
> **Brightbelt said:**
> Thanks for responding. I've learned that Ubuntu Studio and Ubuntu Feisty do have very slightly different menu options. It's subtle but it's there.

I have looked under both Accessories and all the System menus.

Thanks again for responding, Frank B.

I'm quite the newbie (haven't even installed any Linux yet), but it does sound like it should be in the menus according to this post:

[https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/112052](https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/112052)

> If you install wine, you get a "Wine software uninstaller" item in the system submenu of the Applications menu.

---

### Post by zvacet on 2007-06-05
If you still have no luck to find uninstaller then do this.Go to the .wine folder(in your home folder>view>show hidden files) and delete program from there.

---

### Post by regomodo on 2007-09-14
> **fabertawe said:**
> try this from a terminal...
```
uninstaller
```

Paul

you're a star

---

