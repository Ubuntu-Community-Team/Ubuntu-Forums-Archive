---
title: "sudoers - can't save using visudo"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by unwoken on 2005-11-10
if extra info is needed just let me know.

i am trying to run firestarter on startup (without succes - as i am continually told i do not have permission.  the path selected (in sessions - startup) is the same as that listed below in the sudoers file).

if i run 'sudo visudo' it opens the terminal, showing commands highlighted in black at the bottom.  if i attempt to use these commands nothing happens... (e.g. ^X)  it worked for me once, but has not since.

'sudo visudo' opens a .tmp file.  is this normal?  i am not asked for a password after using this command.

the /etc/sudoers temp file looks like this (bottom part):
btw i now have about 6 of them because i gave up and started trying to edit it using gedit (as listed in a different thread).



# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL
anubis  ALL= NOPASSWD: /usr/sbin/firestarter






^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell



What am i doing wrong?

thanks,
u.

---

### Post by unwoken on 2005-11-10
EDIT

Ahhh...  Alas.

I was wrong.  To anyone who read this previously i apologise as i do not have an answer.

i cannot yet save the sudoers file using visudo? (any solutions??)
nor can i get firestarter to run automatically... :(

However, i can run it via a password on bootup (good enough for now)
AND i have just returned from xorg.config hell :), but luckily a little bit of DOS knowledge and reading on the terminal previously helped there.

so here i am, back where i (almost) started. :) ;)

does anyone have any ideas which may help me figure these ones out?

thanks,
u

---

### Post by bluefrog on 2005-11-10
sudo visudo
ctrl x
save as sudoers (without the .tmp)

---

### Post by unwoken on 2005-11-10
[QUOTE=bluefrog]sudo visudo
ctrl x
save as sudoers (without the .tmp)[/QUOTE]

thanks bluefrog!

maybe the time i saved it i accidentally hit ctrl without paying attention...

thanks for clearing it up, i feel a little silly, but hey, at least i know now! :D 

...

That solves the first question, i wonder if anyone can help me with the second?

Trying to get firestarter to run automatically on startup (including reboot) seems a little more difficult.

I'm not at home now, so i can't confirm, but what appears to be happening is that when i turn the computer on i am asked for my firestarter password immediately on login.  if i just log off and then log back on, it opens automatically. ???  Restarting the computer completely (at any time after this) makes me enter password again.  i don't know enough at this stage to have any ideas on what else i can do.

what else do i need to do to get it to run automatically on startup?  i can live with this, but it would be great to sort completely.

---

