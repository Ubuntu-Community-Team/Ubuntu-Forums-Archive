---
title: "[SOLVED] Synaptic and Users &amp;amp; Groups wants a password?"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by nuttycat on 2006-01-20
I got Ubuntu up and running, but have not been able to get into the GUI versions of the package manager or users...

# Users and Groups asks for password to run users-admin.
Now which password do i type in? My current user password or my root password? 
I think i have tried both, but have not managed to get into the GUI config screen as yet. 'su' works as a charm from the CLI.

Synaptic refusues to start. It just goes to the taskbar with a "starting synaptic" message, then in about 30 seconds vanishes...

Any suggestions as to what i can do? For synaptic i guess i could use apt-get (i have already used it twice), but users and groups?

Suggestions would be most welcome
-Nuttycat

---

### Post by amohanty on 2006-01-21
> I think i have tried both, but have not managed to get into the GUI config screen as yet. 'su' works as a charm from the CLI.

Did you do something to make this happen? By default the _root_ user is disabled in Ubuntu, which means you cant do an **su**. 

But since you have done it, by doing so (somehow or other - it shouldnt have happened) you have removed the first user's - your - sudo rights. The easiest fix is edit your /etc/sudoers file using:
> sudo gedit /etc/sudoers

and add the following line at the bottom:
> your_username  ALL=(ALL) ALL

HTH
AM

---

### Post by nuttycat on 2006-01-21
amohanty,
 thanks !!!! that fixed it !

i wonder what i did to make that happen? probably some mindless meddling during the immediate post install process, while i was trying to get ubuntu to work. 

can typing a wrong password multiple times cause this to happen? because, the first few times that i tried to use sudo i think i may have used the root password rather than the current user password.

i have another question along the same line, is is better to REMOVE the root ALL=(ALL)ALL  line from sudoers file? does that allow for more secure access?

anyway, many thanks for solving my original problem.
-Nuttycat

---

### Post by amohanty on 2006-01-26
[QUOTE=nuttycat]
i have another question along the same line, is is better to REMOVE the root ALL=(ALL)ALL  line from sudoers file? does that allow for more secure access?
[/QUOTE]


Sorry for the delay, was kind of busy... but to answer your question _NO_ dont do it :)

HTH
AM

---

### Post by nuttycat on 2006-01-27
Ok. Will leave the "Root" entry as is in that file.
Thanks again for the assistance.
N'Cat

---

