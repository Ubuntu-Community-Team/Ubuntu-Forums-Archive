---
title: "Gnome &amp; KDE desktop shortcuts"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by serid on 2007-03-11
Hi everyone,

I have just installed kubuntu-dekstop on my ubuntu edgy and noticed, that
each time I add a shortcut to one of the desktops (gnome or kde), I get it
also on the other one. It a bit annoying because I would like to keep my
shortcuts on KDE separately from these ones created while using Gnome.

What is the workaround ?

Thanks,

Adrian

---

### Post by Crooksey on 2007-03-11
I think just have two logins with different /home directories, like just put a "k" in front of your user name, still being able to access the files in your own home directory.

---

### Post by serid on 2007-03-11
That's truly a good idea !
Thanks for that tip.

I'm still waiting for other solutions as well (if there are any ...)


Thanks,

Adrian

---

### Post by serid on 2007-03-11
BTW

You can add some shortcuts using gconf-editor, so it's gnome-specyfic and
won't be seen on KDE. Is there something like that for KDE (some kind of
control centre) ?


Cheers,

Adrian

---

### Post by Explosive_Cornflake on 2007-03-12
I'm sure there's a variable inside KDE conf file for desktop location, you could just edit that. I'll ask my house mate about it later, as he was sharing home directories between suse and solaris and he needed to tell the KDE on each to use a different folder inside the one /home/dir. Would save you having to have a seperate /home/dir/ .

---

### Post by Songwind on 2007-03-12
> **Explosive_Cornflake said:**
> I'm sure there's a variable inside KDE conf file for desktop location, you could just edit that. I'll ask my house mate about it earlier, as he was sharing home directories between suse and solaris and he needed to tell the KDE on each to use a different folder inside the one /home/dir. Would save you having to have a seperate /home/dir/ .

That's actually in the settings GUI (kcontrol) somewhere.  I haven't changed it so I remember seeing it but don't clearly remember under which applet it resides.

It was something to do with "paths."

Then you could just create a ~/kdesktop directory and point it there.

---

