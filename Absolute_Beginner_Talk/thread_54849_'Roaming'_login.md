---
title: "'Roaming' login?"
date: 2005-08-06
forum: Absolute Beginner Talk
---

### Post by Elijah on 2005-08-06
I dunno what exactly my boss wants me to do ..  :| 

He wanted users to be able to logon to *any* pc, be authenticated (without being added as a new user in the machine) and can be able to save files to their own ~/home directory to their main pc. This is from a web development environment. 

I was thinking at first .. thin clients, they could login anywhere, but that might be a problem when some other developer decides to change the database. I plan to use subversion to this environment too. So I scrapped the thin-client idea. 

Next I thought of SSH, they could logon to their machines from a diff pc, also that VNC thing (never tried it, have only the littlest idea of what it does) ... that could give them access to their own machines ... but how about authentication?? logging in from a different pc requires another account from the new user. 

Maybe I need some kind of org-wide authentication?? how do I do this?? and what tools can I use to be able to authenticate and let users access their files from their local pc anywhere(file servers??)??? nfs?? samba(we might be using windows soon on some pc's) ??  ](*,)

---

### Post by varunus on 2005-08-06
I've never done this before, but this is how my university has their SunOS clients set up.  The password files are all stored remotely, I think, but all software is available locally. 

I can answer part of the puzzle; you need to use something like nfs or shfsmount to configure each computer that after a login, it mounts the correct home directory from a server.  Because all program settings are stored on each person's home directory, Their GNOME and Firefox or whatever settings will be preserved from computer to computer as long as each computer has the same software on it.

---

### Post by dcraven on 2005-08-06
[QUOTE=Elijah]I dunno what exactly my boss wants me to do ..  :| 

He wanted users to be able to logon to *any* pc, be authenticated (without being added as a new user in the machine) and can be able to save files to their own ~/home directory to their main pc. This is from a web development environment. 
[/QUOTE]

 This is commonly known as "Desktop Teleportation" and was my second choice for a thesis program this year. I was going to implement such a system for GNOME using tools such as ssh and rsync. It is still being looked at in the area of pervasive computing where the user's info, including everything from wallpaper to browser cookies "follow them around" as they move from one station to another.

For your usage, you might want to look into using X remotely (remember Xorg is actually a server similiar to any other). I'm not sure exactly how this works, but I'm sure there are several howto's around the web somewhere.

As for Windows clients, I have no idea.

Cheers,
~djc

---

### Post by Elijah on 2005-08-06
[QUOTE=dcraven]This is commonly known as "Desktop Teleportation" and was my second choice for a thesis program this year. I was going to implement such a system for GNOME using tools such as ssh and rsync. It is still being looked at in the area of pervasive computing where the user's info, including everything from wallpaper to browser cookies "follow them around" as they move from one station to another.

For your usage, you might want to look into using X remotely (remember Xorg is actually a server similiar to any other). I'm not sure exactly how this works, but I'm sure there are several howto's around the web somewhere.

As for Windows clients, I have no idea.

Cheers,
~djc[/QUOTE]
 Thanks =) 

shfsmount could be the one I'm looking for ... I now have to figure out how to setup nfs & mount them upon login. 

Now for authentication ... my boss mentioned something about LDAP? I only used it for storing info but never for authenticating ... hmmm ... anyone had any idea how to use it?

so what I'm doing all along is some kind of 'remote authentication and user dir mount'? or something. I could'nt find the right keywords for googling ...

---

### Post by cwaldbieser on 2005-08-06
The "Linux Network Administrator's Guide" from O'Reilly has a chapter on setting up authentication with OpenLDAP.  You can also probably find info over at [http://www.openldap.org/](http://www.openldap.org/) .  It is sort of like Active Directory for Windows, but it is an open protocol.

---

### Post by Elijah on 2005-08-07
[QUOTE=cwaldbieser]The "Linux Network Administrator's Guide" from O'Reilly has a chapter on setting up authentication with OpenLDAP.  You can also probably find info over at [http://www.openldap.org/](http://www.openldap.org/) .  It is sort of like Active Directory for Windows, but it is an open protocol.[/QUOTE]
 Thank you, I'll do some more reading on that one. 


Please post if there other options I missed =)

---

