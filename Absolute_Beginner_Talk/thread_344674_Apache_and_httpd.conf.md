---
title: "Apache and httpd.conf"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by bxbailey on 2007-01-23
I'm trying to setup apache which I now have installed, but now I'm trying to edit the httpd.conf using the text editor but it's saying I don't have the permissions. I've tried opening it with vi under su access but I'm not having much luck actually editing it. Any advice?

---

### Post by pizzutz on 2007-01-23
Unlike some other distros, Ubuntu requires that you prefix the actual command with sudo. try 

sudo vi httpd.conf

---

### Post by bxbailey on 2007-01-23
I may not know how to edit in VI because if i try changing or editing the document I receive the message E486 Pattern not found: <text i'm typing>

---

### Post by pizzutz on 2007-01-23
try gedit.

gksu gedit httpd.conf

hope this helps.

---

### Post by bxbailey on 2007-01-23
That worked. what is that command?

---

### Post by pizzutz on 2007-01-23
gksu?

As I said, Ubuntu requires you to prefix comands to be run as root with sudo.  this is safer than opening a root terminal, or using su.

sudo prompts for you password in the terminal
gksu (or gksudo)  prompts you with a popup window.

I use gksu for applications that do not run in terminal, like gedit.

---

### Post by Srirangan on 2007-02-02
Ok .. I try editing apache conf files, using the gui (file manager) and it says insufficient perms.. where/how do i use the commands you have mentioned above?

---

### Post by Imperial on 2007-07-13
> **pizzutz said:**
> try gedit.

gksu gedit httpd.conf

hope this helps.
That worked great.

Thank you.

---

### Post by twiceasworn on 2007-07-13
I would like to add something to this pertaining to text editors.  I highly HIGHLY suggest that anyone who uses gedit regularly learn one of the terminal editors.  The reason being that sometimes you can't get to the gui and all you have is the terminal.  Knowing how to use emacs, pico, nano or my favorite VI is seriously an indispensable skill for Linux.  There are lots of guides out there for these text editors, just search on google for them.

---

### Post by Warren Watts on 2007-07-13
> **twiceasworn said:**
> I highly HIGHLY suggest that anyone who uses gedit regularly learn one of the terminal editors.  The reason being that sometimes you can't get to the gui and all you have is the terminal.  Knowing how to use...((a terminal editor)  is seriously an indispensable skill for Linux..

As an aside to your aside, so to speak, I agree 100%.  I have to admit I **DON'T** know the first thing about using any of the available terminal editors.  And my ignorance has cost me a lot of unnecessary grief on more than one occasion after having after having done something stupid like say, edit and thereby screw up the xorg.conf file without making a backup of the original first....

It's a struggle to have to use a terminal editor when you don't know even the most basic of commands for the editor....

---

