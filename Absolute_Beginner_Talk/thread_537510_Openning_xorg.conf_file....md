---
title: "Openning xorg.conf file...?"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by waytorun on 2007-08-29
When I tried to open xorg.conf file to fix berly related problem with

commend " sudo gedit /etc/X11/xorg.conf ",

it shows empty file named xorg.conf instead of xorg.conf file that 

I need to edit.


I tried openning xorg.conf file itself and copied all the content

then pasted it on xorg.conf(one which was opened using the command above).

But it won't let me save the file saying the file does not exist.


I've done this before doing exactly what I'm doing now,

but it won't let me open xorg.conf this time...


Much appreciation in advance.

---

### Post by splintercellguy on 2007-08-29
Shouldn't it be gksudo gedit /etc/X11/xorg.conf?

---

### Post by dwhitney67 on 2007-08-29
> **splintercellguy said:**
> Shouldn't it be gksudo gedit /etc/X11/xorg.conf?

The use of sudo is just fine.

What are the contents of the /etc/X11/xorg.conf file?  Try to examine it using a terminal.  Just run this command:

$ cat /etc/X11/xorg.conf

If everything looks fine, then your original problem was probably due to a typo in the path to the file when you ran the gedit command.

---

### Post by mcduck on 2007-08-29
> **splintercellguy said:**
> Shouldn't it be gksudo gedit /etc/X11/xorg.conf?

Yes, it should. Graphical applications should always be started using gksudo, not sudo.

While in some cases sudo might work without any problems it also can cause serious problems, changing ownership of some of your setting files to root and making it impossible for you to log in any more..

---

### Post by dwhitney67 on 2007-08-29
> **mcduck said:**
> Yes, it should. Graphical applications should always be started using gksudo, not sudo.

While in some cases sudo might work without any problems it also can cause serious problems, changing ownership of some of your setting files to root and making it impossible for you to log in any more..
I guess that's one more reason to avoid graphical editors that sprinkle one's account with countless hidden files.  I'll stick to vi.

---

### Post by mcduck on 2007-08-29
> **dwhitney67 said:**
> I guess that's one more reason to avoid graphical editors that sprinkle one's account with countless hidden files.  I'll stick to vi.

You can just disable automatic backups in Gedit's settings :D

In Gedit, Edit/Preferences and on Editor-tab disable "Create a backup copy before saving"

Anyway, the problem is not in GUI apps, it's in sudo which is only made for command line use so it doesn't load root user's profile correctly for GUI applications. That's what gksudo and kdesu are for.

---

