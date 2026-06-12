---
title: "user accounts completely screwed up"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by abijah on 2007-01-08
Hi:

I don't how this happened, b/c i share my PC with someone else.

All the user accounts on my installation just stopped working.

I don't even have "root" privileges.

Here is the error message I get when I try to run “Synaptic Package Manager”

> “Failed to run /usr/sbin/synaptic as user root: the underlying authorization mechanism (sudo) does not allow you to run this program.  Contact the system administrator”

hmmm...

---

### Post by kj1h234lkj1234 on 2007-01-08
What is in your /etc/sudoers file?

```
cat /etc/sudoers
```

---

### Post by taurus on 2007-01-08
Does that someone else have a root privilege on your machine?  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
groups
```

---

### Post by abijah on 2007-01-08
Thanks so much:

Okay... here what i got

The command > cat /etc/sudoers

gives me 

> cat /etc/sudoers: Permission denied

The command > groups 

gave me

> apex adm dialout cdrom floppy audio dip video plugdev lpadmin scanner

---

### Post by taurus on 2007-01-08
Well, you need to belong to both groups adm & admin in /etc/group but currently, admin is not in your group!  That's why sudo won't work.

Therefore, boot into recovery mode from GRUB menu and at the prompt, do

```
adduser apex admin
id apex
shutdown -r now
```
(I assume apex is your username...)

---

### Post by abijah on 2007-01-08
The command > groups

now gives me

> apex adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

But i still have the same problem, and I'm still getting this error message when trying to run Synaptic.

> “Failed to run /usr/sbin/synaptic as user root: the underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator”

---

### Post by taurus on 2007-01-08
And I assume you already reboot your machine.  Open a terminal and see if you get any error message from this command?

Applications -> Accessories -> Terminal
```
sudo aptitude update
```

---

### Post by abijah on 2007-01-08
Here the response i get when i type that command

> apex is not in the sudoers file.  This incident will be reported

---

### Post by taurus on 2007-01-08
Well, somebody screwed up /etc/sudoers big time!

Here's my /etc/sudoers.

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

So, boot into recovery mode and edit your /etc/sudoers to make it looks like what I have!

```
visudo /etc/sudoers
```
p.s.  You MUST use visudo to edit /etc/sudoers.  Press i to insert and when you are done, press Esc and then :wq! and Return to save and exit.  Reboot and see if you can run the "sudo aptitude update" again.

```
shutdown -r now
```

---

### Post by melancholeric on 2007-01-08
> **taurus said:**
> 
p.s.  You MUST use visudo to edit /etc/sudoers.  Press i to insert and when you are done, press Esc and then :wq! and Return to save and exit.  Reboot and see if you can run the "sudo aptitude update" again.
Aren't those for vi, and visudo (despite the name) actually uses nano. So if you hit i to insert it'll just add the letter i to the beginning.

The nano controls are printed right there.

---

### Post by taurus on 2007-01-08
It uses vi on my machine, not nano...

```
sudo visudo
```

---

### Post by abijah on 2007-01-08
I booted into Recovery Mode, but when i give the command

> visudo /etc/sudoers

I get this response

> usage: visudo [-c] [-f sudoers] [-q] [-s] [-V]

---

### Post by taurus on 2007-01-08
> **abijah said:**
> I booted into Recovery Mode, but when i give the command

I get this response

Just run "visudo" by itself.  It would automatically open /etc/sudoers.

---

### Post by Ptero-4 on 2007-01-08
Actually. visudo uses vi/vim. But you don't need to use it, just type
```
sudo nano /etc/sudoers
```

---

### Post by taurus on 2007-01-08
> **Ptero-4 said:**
> Actually. visudo uses vi/vim. But you don't need to use it, just type
```
sudo nano /etc/sudoers
```

He can't use "sudo" and besides, you need to use visudo to edit /etc/sudoers.

```

VISUDO(8)                    MAINTENANCE COMMANDS                   VISUDO(8)

NAME
       visudo - edit the sudoers file

SYNOPSIS
       visudo [ -c ] [ -f sudoers ] [ -q ] [ -s ] [ -V ]

DESCRIPTION
       visudo edits the sudoers file in a safe fashion, analogous to vipw(8).
       visudo locks the sudoers file against multiple simultaneous edits,
       provides basic sanity checks, and checks for parse errors.  If the
       sudoers file is currently being edited you will receive a message to
       try again later.

       There is a hard-coded list of editors that visudo will use set at comâ[m
       pile-time that may be overridden via the editor sudoers Default variâ[m
       able.  This list defaults to the path to vi(1) on your system, as
       determined by the configure script.  Normally, visudo does not honor
       the VISUAL or EDITOR environment variables unless they contain an ediâ[m
       tor in the aforementioned editors list.  However, if visudo is configâ[m
       ured with the --with-enveditor flag or the enveditor Default variable
       is set in sudoers, visudo will use any the editor defines by VISUAL or
       EDITOR.  Note that this can be a security hole since it allows the
       user to execute any program they wish simply by setting VISUAL or EDIâ[m
       TOR.

       visudo parses the sudoers file after the edit and will not save the
       changes if there is a syntax error.  Upon finding an error, visudo
       will print a message stating the line number(s) where the error
       occurred and the user will receive the "What now?" prompt.  At this
       point the user may enter "e" to re-edit the sudoers file, "x" to exit
       without saving the changes, or "Q" to quit and save changes.  The "Q"
       option should be used with extreme care because if visudo believes
       there to be a parse error, so will sudo and no one will be able to
       sudo again until the error is fixed.  If "e" is typed to edit the
       sudoers file after a parse error has been detected, the cursor will be
       placed on the line where the error occurred (if the editor supports
       this feature).

```

---

### Post by melancholeric on 2007-01-08
I swear to god it uses nano on my machine, on dapper and debian etch. But ...

There is a hard-coded list of editors that visudo will use set at compile-time that may be overridden via the editor sudoers Default variable. This list defaults to the path to vi(1) on your system, as determined by the configure script. Normally, visudo does not honor the VISUAL or EDITOR environment variables unless they contain an editor in the aforementioned editors list. However, if visudo is configured with the --with-enveditor flag or the enveditor Default variable is set in sudoers, visudo will use any the editor defines by VISUAL or EDITOR. Note that this can be a security hole since it allows the user to execute any program they wish simply by setting VISUAL or EDITOR.

from [http://www.gratisoft.us/sudo/man/visudo.html](http://www.gratisoft.us/sudo/man/visudo.html) . I never changed any defaults either.

But you don't want to use just nano to edit it because visudo includes the syntax check, which is sort of important.

---

### Post by MkfIbK7a on 2007-01-08
> provides basic sanity checksfrom visduo manpage

we all need that for sure:rolleyes:

---

### Post by taurus on 2007-01-08
> **melancholeric said:**
> 
But you don't want to use just nano to edit it because visudo includes the syntax check, which is sort of important.

And that's why it's a good idea to use visudo (vi/vim) to edit /etc/sudoers.  ;)

---

### Post by abijah on 2007-01-08
Thank you all very much!

It worked.

My problem is solved.  This forum is awesome.

Those few times when the system stated that 
> This incident will be reported

Where does it put this "report"?  
And who does it notify?

---

### Post by melancholeric on 2007-01-08
It notified you, probably. try 
```
mail
```
I don't know, just a guess.

---

