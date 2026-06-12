---
title: "Permission Questions"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by blukattt on 2007-10-04
I have a problem.  I am very new to the Linux system, and my work comp is just that.  I am trying to upgrade both Ubuntu, as well as Firefox, but have run into a snag.  I figured out how to upgrade, but when I try to remove the old firefox folder, it says I can't because I am not the owner.

I contacted the original owner of the comp (boss's husband) and he assured me that this account was indeed the only account on here.

My question is this:  Is there a way to make sure this account is the "owner", or at least change the permissions so that this account can write and execute as well?

As I said before, I am almost clueless when it comes to Linux systems, (PC raised) so please talk to me like a 5 year old.

Thank you in advance. :confused:

---

### Post by skymera on 2007-10-04
aha! your not root :wink:

try this: open terminal:

sudo rm /path/to/file/here

thats it :) for files

or 

sudo nautilus to navigate GUI to the folder/files and delete.

---

### Post by blukattt on 2007-10-04
> **skymera said:**
> aha! your not root :wink:

try this: open terminal:

sudo rm /path/to/file/here

thats it :) for files

or 

sudo nautilus to navigate GUI to the folder/files and delete.

Blah, didn't work; all I got was:

"rm: cannot remove `/path/to/file/here' : No such file or directory"


Any other ideas?  The forums are my Obi-Wan... (they're my only hope LOL)

---

### Post by philinux on 2007-10-04
in the terminal type gksudo nautilus.

Be careful with this. Navigate to the correct folder and move it to trash

{edit] if anything goes wrong you can copy the folder back

---

### Post by blukattt on 2007-10-04
> **philinux said:**
> in the terminal type gksudo nautilus.

Be careful with this. Navigate to the correct folder and move it to trash

{edit] if anything goes wrong you can copy the folder back

No good; this time I got:

"(nautilus: 10741) : GnomeUI - WARNING **: While connecting to session manager: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed."

---

### Post by bodhi.zazen on 2007-10-04
> **blukattt said:**
> No good; this time I got:

"(nautilus: 10741) : GnomeUI - WARNING **: While connecting to session manager: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed."

That is a know bug. It has been reported and can be ignored.

---

### Post by philinux on 2007-10-04
People always say use gksudo but it always gives that error. 

However we should really sort out the permissions. If you go to place and click home this should show your home folder. Is there  a folder in there that matches you sign on user ID,  go into it. Then click view at the top and check view hidden files.

Now also in view select at the bottom view as list. Also view visible columns check owner and permissions this will show you who owns what. scroll doen to firefox and post back what it says

---

### Post by blukattt on 2007-10-04
> **philinux said:**
> People always say use gksudo but it always gives that error. 

However we should really sort out the permissions. If you go to place and click home this should show your home folder. Is there  a folder in there that matches you sign on user ID,  go into it. Then click view at the top and check view hidden files.

Now also in view select at the bottom view as list. Also view visible columns check owner and permissions this will show you who owns what. scroll doen to firefox and post back what it says


I went to the folder ".mozilla" (I'm assuming that's the Firefox folder you were referring to.  It says that this account is the owner for everything on that list except for ".mailcap", ".mime.types", and ".rnd", which are all root.

Inside of the .mozilla folder, I went to "firefox", it says the same thing, all are owned by this account

[EDIT]  I'm leaving work now, so I won't be on this comp until tomorrow afternoon; please throw out any possible solutions and I'll check them tomoorw, and thanks again Phil.

---

### Post by philinux on 2007-10-04
Ok go to Applications Accessories and click terminal.

then type this but you will have to change it to suit your user ID

sudo chown -R youruser /home

chown  -R changes the ownership of all files in home to your logon user ie youruser

How they got to be different is a mystery

computer eh

You will then have the correct permissions to delete files in home. dont forget to click show hidden files though when you browse

---

