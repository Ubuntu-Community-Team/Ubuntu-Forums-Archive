---
title: "Script to help me chmod several files"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by hyapadi on 2007-02-27
/*                         (main files for site)
/admin/*                   (main files for admin-area)
/admin/javascript/*        (javascript helper scripts)
/admin/libs/*              (BLOG:CMS core libs)
/admin/language/*          (definitions of languages)
/admin/plugins/*           (plugin-dir)
/admin/xmlrpc/*            (XML-RPC interface)
/admin/documentation/*     (Documentation + admin-area help)
/admin/styles/*            (stylesheets for docs & admin-area)
/admin/forms/*             (skeletons for commentforms etc)
/extra/*                   (extra goodies)
/skins/*                   (skins directory [imported skins will go here])
/media/*                   (media library directory [emtpy])

I have to chmod those files. Is there any way to do it automatically?

Can somebody make me simple script to automate the chmoding?

Thanks:popcorn:

---

### Post by tribble222 on 2007-02-27
If you want to run a bunch of commands all in a row you can write a bash script to do it.  Just create a new file, call it myscript.sh and add the line "#!/bin/bash" to the top (without the quotes).  Then just put one command per line and save the file.  You run it by typing "sh myscript.sh" and it will execute each command one-by-one.

---

### Post by aysiu on 2007-02-27
> **hyapadi said:**
> /* I don't understand this. You're going to *chmod* the entire root directory? Won't that screw up your system?

---

### Post by annda on 2007-02-27
aysiu makes a very important point! i understand by "/" you mean the main directory of your website BUT it WILL be interpreted as the root directory. you certainly do not want that.

make sure you specify the full path in your script:
/var/www/your_sites_name/ instead of just /

the same goes for all the other directories and files.

also, there is an option for chmod that will change permissions recursively, which means for all subdirectories:  -R

---

### Post by aysiu on 2007-02-27
I think in this case, it's probably easiest to just do recursive *chmod*s through the GUI. I believe as of Edgy (or maybe even Dapper) Gnome now supports recursive permission changes through Nautilus. Konqueror has done this for some time, too. ```
kdesu konqueror
``` or ```
gksudo nautilus
```

Or is this a strictly command-line server with no GUI?

---

### Post by hyapadi on 2007-02-27
@all 
thx for the quick reply. really quick :>

I want to chmod certain files required in installing CMS.

That list above only an example. I need to know the way so that it can be applied on other situation too.

Could you give example of sh script for this?

Thanks

---

### Post by Brunellus on 2007-02-27
> **hyapadi said:**
> @all 
thx for the quick reply. really quick :>

I want to chmod certain files required in installing CMS.

That list above only an example. I need to know the way so that it can be applied on other situation too.

Could you give example of sh script for this?

Thanks
Step back and explain to us again what you're attempting to achieve?  What software are you installing and whose instructions are you following?

---

### Post by hyapadi on 2007-02-28
Simply a script to chmod several files, rather that type it one by one manually.

---

### Post by Brunellus on 2007-02-28
> **hyapadi said:**
> Simply a script to chmod several files, rather that type it one by one manually.
you understand that chmoding the root directory is a BAD idea?  If this is simply to install a piece of software, there are better ways.  Please tell us what software you're installing, and we can get around this problem.

---

### Post by hyapadi on 2007-02-28
that / is not the root of the system, but a CMS. That root belongs to root folder in shared hosting. :>

---

