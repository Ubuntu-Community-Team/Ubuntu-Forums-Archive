---
title: "Stuck at command prompt - help!"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by jimbobadahey on 2008-02-19
I'm trying to run from a freshly burned copy of 7.10, and am stuck at a command prompt. I'm so frustrated that i'm even considering just paying bill gates some money for his $#!+ os...

Help!

---

### Post by timbounceback on 2008-02-19
enter ```
sudo dpkg-reconfigure xserver-xorg
``` or try booting in safe graphics mode

---

### Post by amingv on 2008-02-19
Or try

```
startx
```

and see if it loads.

---

### Post by JoshuaRL on 2008-02-19
Yeah, it sounds like problems with the Xserver app that loads the Desktop Environment (GUI) of your choice.

Do you know if you installed the Server Edition?  If you can't remember, was there an option to install a LAMP system from the boot menu on the CD?

In explanation, the command in post #3 will try to start Xserver to see if it's installed and running.  If there are any errors that pop up make sure to post them here.

The command in post #2 is trying to reconfigure your Xserver so it is attuned to your system.  You should probably hold off on trying this yet, we're not sure you have Xserver installed yet.

And sorry this is so confusing and aggrivating.  But we're here to help.

---

### Post by jimbobadahey on 2008-02-19
It's the live cd desktop version that I'm using, and I didn't see an option 'LAMP'
After trying sudo dpkg-reconfigure xserver-xorg I get /bin/sh: sudo: not found
I havn't tried startx yet...

---

### Post by JoshuaRL on 2008-02-19
Try startx then.

The reason it can't find sudo is that sudo stands for "super-user do".  It allows you to have administrative (root) priviledges while still keeping your system secure.

Right now you're in the terminal as root.

So try startx and see what happens.

---

### Post by jimbobadahey on 2008-02-19
Okay, brb after some rebooting...

---

### Post by jimbobadahey on 2008-02-19
startx gives /bin/sh: startx: not found

---

### Post by Hobo Joe on 2008-02-19
You should get a new disk.

Make sure to burn it as an .iso image.

---

### Post by JoshuaRL on 2008-02-19
Okay.  Are you connected to the internet on that computer?

If so, try doing this:
```

apt-get install ubuntu-desktop

```

That's what's called a metapackage that installs everything you need for the Gnome-based Ubuntu Desktop Environment.

Let me know if you have any errors.

---

### Post by JoshuaRL on 2008-02-19
> **Hobo Joe said:**
> You should get a new disk.

Make sure to burn it as an .iso image.

Yep, that was what I was gonna suggest next if the shell couldn't get apt to work.

Just make sure you burn it as a CD image (.iso) at the lowest speed speed.

---

### Post by jimbobadahey on 2008-02-19
It's actually this machine, just switching back and forth from xp...

---

### Post by jimbobadahey on 2008-02-19
ok, gonna try apt, if it doesn't work, I'm of to bed, and will regroup tomorrow. Thanls for your help.

---

### Post by jstevans on 2008-02-29
Hello,

I found this thread because I too was stuck at the command prompt.  I tried the suggested command of "sudo apt-get install ubuntu-desktop" but ended up with a whole lot of errors that seem to all say "[COLOR="Red"]Error: Microcode "bcm43xx_microcode5.fw" not available or load failed[/COLOR]"

I'd welcome any help as to what I should do now?

Also, once the install is done what do I type at the command prompt to get it to actually run the desktop?

Thanks

EDIT: More wandering through these forums revealed that gdm restart should (and actually did - yay!) start the gnome desktop.  

And even better - when I rebooted it all came back, desktop, network connection, everything.

However, I still would like to know what, if anything, I need to do about the error messages mentioned above.

Thanks to those who contributed to this thread.

Jay

---

