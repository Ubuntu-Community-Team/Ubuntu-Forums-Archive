---
title: "*Major* problem, possibly to due with suspension/hibernation. Please help!"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by hackle577 on 2007-04-06
Ok, here's what happened. I left my computer alone to go watch a movie at a friend's place, and when I came back, it appeared to have turned itself off. However, I know for a fact that I changed some of the power management settings, so I just moved the mouse and waited.. and waited. Nothing. I pressed a few keys but nothing happened after that either.

So I held down the power button until my laptop eventually shut itself off. I waited a few seconds and powered it back on. That when I got the first error message:

[[IMG]http://img367.imageshack.us/img367/706/errorgoodak5.th.jpg[/IMG]](http://img367.imageshack.us/my.php?image=errorgoodak5.jpg)

As you can see, at the bottom it says to press Ctrl-D to resume booting, so that's what I did. Immediately following that, I got this second error:

[[IMG]http://img366.imageshack.us/img366/9098/dscf0367hu8.th.jpg[/IMG]](http://img366.imageshack.us/my.php?image=dscf0367hu8.jpg)

It hung there for a bit and didn't do anything, so I held the power button down again until it turned off. I waited a bit and booted again and everything went fine, I'm in Ubuntu right now. I suspect it may be some sort of hibernation/suspension issue. My settings are here:

**Running on AC** (It was on AC it the time.)
Display to sleep after 6 minutes.
Computer to sleep after 25 minutes.

**General**
Sleep type when inactive: Suspend

If you need to know more of my settings, let me know. My setup:

Dell Inspiron 4150
Ubuntu 6.10 Feisty
1.70 GHz processor
30 GB disk, 640 MB RAM

Thanks for the help, I need it! :-)

---

### Post by gborzi on 2007-04-06
I think you need to put the "Sleep type when inactive"  under General to "do nothing" instead of suspend.

---

### Post by hackle577 on 2007-04-06
Ok, I did that, but I don't know if that will solve the problem itself.

---

### Post by gborzi on 2007-04-06
It's the setting I have for my laptop. I have left it inactive for hours and it didn't hibernated or suspended. Just blanked the video.

---

### Post by hackle577 on 2007-04-06
Well, I guess what I am wanting to know is this: was this scary-looking error a one-time thing caused by my power settings, or something that could cause problems soon/in the future?

EDIT: I've been Googling around and some other people with a similar problem were talking about restoring GRUB, editing /etc/fstab, some pretty in-depth stuff. Is this correct?

---

### Post by gborzi on 2007-04-06
I presume your system tried to suspend to RAM, or actually suspended and wasn't able to leave that state. Maybe this damaged some filesystem, but since now it's working it was able to repair the damage. Check if you still have a working swap, you can do this by typing in a shell the "free" command. The last output lines that starts with **Swap:** shows the amount of swap space. If it's 0 then you will have to restore the swap partition configuration. I hope this is not the case. Now I'm going to sleep, it's 4 am here.

---

### Post by hackle577 on 2007-04-06
I typed free in the shell, here's the output:

```
             total       used       free     shared    buffers     cached
Mem:        645468     585608      59860          0      33544     286668
-/+ buffers/cache:     265396     380072
Swap:      1020116          0    1020116

```

Bad? Good? Thanks for the help!

---

### Post by hackle577 on 2007-04-07
Bumpity bump bump. Help anyone?

---

### Post by bobplano on 2007-04-07
> **gborzi said:**
> Check if you still have a working swap, you can do this by typing in a shell the "free" command. The last output lines that starts with **Swap:** shows the amount of swap space. If it's 0 then you will have to restore the swap partition configuration. I hope this is not the case. 

it seems you have about a gig of swap so you should be fine.

---

### Post by hackle577 on 2007-04-07
Okie dokie, thanks a lot for the help guys!

---

