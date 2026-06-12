---
title: "Adding a Secondary Samba User"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Matuku on 2007-07-15
Quick question which has been confusing me through all the Samba guides; is it possible to add a Samba User who doesn't have a local user account on the ubuntu PC? I ask because my brother has files on my PC which he wants to access from a windows machine so I was wondering if I could set him up with a samba account but not a local one?

---

### Post by kidders on 2007-07-16
Hi there,

Normally, Samba maintains its own user database, so there often isn't a direct association between Samba users and Linux system accounts. For convenience, many people like to keep their Samba & Linux accounts in sync with each other, so they can *think* of them as being the same thing ... but they're not.

For instance, you might have a Samba user called "Matuku", that so happens to be mapped to a Linux user also called "Matuku". On the other hand, you might want to create a Samba user called "Administrator" that maps to a Linux user called "root".

So, the answer to your question is yes, but you will still need to choose (or create) a local Linux account to map your brother's Samba account to. You see, when your brother logs in and attempts to access your filesystem, Samba will need to know what local access privileges to use, so your Ubuntu can properly control his activity. If this sort of thing is likely to crop up reasonably frequently (ie you'll want to have the freedom to create lots of Windows accounts without bothering to distinguish between them in Linux), I would suggest doing something like this...
[LIST]
[*]Set up a highly constrained Linux account called something like "samba_generic" with no special group memberships (eg audio, video, etc.) that would allow extended privileges on your box, no shell, and perhaps not even a password.
[*]Set up a private group for your generic Samba user account.
[*]Map as many Samba users as you like to the new account.
[*]Make sure anything you want to allow all the "fake" Windows users to access is at least "chmod o+r" or "chgrp samba_generic".[/LIST]I hope that helps. Check out samba's man page for more details. It's *extremely* long, but you may be interested in the subsection called "username map", 5-6,000 lines into the file (depending on the width of your terminal window).

---

