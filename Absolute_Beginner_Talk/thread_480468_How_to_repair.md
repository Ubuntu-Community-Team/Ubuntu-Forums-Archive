---
title: "How to repair"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by burt_57 on 2007-06-21
Here goes nothing:
I have Ultimate install but can not get it to load.
error = Setting sensors limits = fail 
Now I am working from the CD.
I would presume that on my hardrive I still have my previous Ubuntu Ultimate.
Is it possible to do a repair now without reinstalling ?
Can I do it here from life CD?
In terminal that is !

---

### Post by FleetAdmiral74 on 2007-06-21
Super GRUB is a nice utility to fix lots of boot up problems, might want to give it a try. Or just use gParted and see if the partitions are stil in tact and mount em.

---

### Post by burt_57 on 2007-06-21
> **FleetAdmiral74 said:**
> Super GRUB is a nice utility to fix lots of boot up problems, might want to give it a try. Or just use gParted and see if the partitions are stil in tact and mount em.

Seem I have to repair my /ect/X11/org.conf.   ( not exitinng anymore )
Darn it, everytime I do some suggesstion from some people I get
all screw up. :(
I alway print the sugesstion before I do anything.

---

### Post by alienexplorers on 2007-06-22
> dpkg-reconfigure -phigh xserver-xorg

Use this to reconfigure your xorg.conf.

---

### Post by burt_57 on 2007-06-22
> **alienexplorers said:**
> Use this to reconfigure your xorg.conf.

This what I get
ubuntu@ubuntu:~$ gksudo dpkg-reconfigure -phigh xserver-xorg 
GTK Accessibility Module initialized
GKsu version 2.0.0

Usage: gksudo [-u <user>] [options] <command>

  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.

  --user <user>, -u <user>
    Call <command> as the specified user.

  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!

  --description <description|file>, -D <description|file>
    Provide a descriptive name for the command to
    be used in the default message, making it nicer.
    You can also provide the absolute path for a
    .desktop file. The Name key for will be used in
    this case.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
    Only use this if --description does not suffice.

  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful to use in scripts with
    programs that accept receiving the password on
    stdin.

  --sudo-mode, -S
    Make GKSu use sudo instead of su, as if it had been
    run as "gksudo".
  --su-mode, -w
    Make GKSu use su, instead of using libgksu's
    default.
ubuntu@ubuntu:~$

---

### Post by tgalati4 on 2007-06-22
sudo dpkg . . .

---

### Post by lamalex on 2007-06-22
gksudo is for launching graphical applications as root, dpkg-reconfigure is a terminal command, do sudo dpkg-reconfigure ...

---

### Post by burt_57 on 2007-06-22
> **Iamalex said:**
> gksudo is for launching graphical applications as root, dpkg-reconfigure is a terminal command, do sudo dpkg-reconfigure ...

ubuntu@ubuntu:~$ sudo  dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070622152901
Oh boy...am so new at all this ..thank for the help.

---

