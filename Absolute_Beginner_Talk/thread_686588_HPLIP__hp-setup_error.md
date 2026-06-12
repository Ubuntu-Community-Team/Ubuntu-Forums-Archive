---
title: "HPLIP  hp-setup error"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by sirfonners on 2008-02-03
I am trying to etup my printer
but whenever I run hp setup I get this:

```
HP Linux Imaging and Printing System (ver. 2.7.7)
Printer/Fax Setup Utility ver. 4.5

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.
[B][COLOR="Red"]
error: You must be root to run this utility[/COLOR][/B].
```

---

### Post by bumanie on 2008-02-03
You need to type sudo before the hplip .sh command

---

### Post by PmDematagoda on 2008-02-03
Append the hp-setup command with "sudo" to make it look like this:-
```
sudo hp-setup
```

The "sudo" grants root permissions to the commands you attach it to or when you execute commands in Recovery Mode or when you become the root user. Be careful when using "sudo" since it can cause your whole system to get damaged since you can make changes to any file while being root.

The following [page]("https://wiki.ubuntu.com/RootSudo") can be useful in order to understand more about "sudo" and root.

---

### Post by sirfonners on 2008-02-03
ooooooooh thats what the whole sudo thing is about
im really gonna have to buy one of those linux for dummy books and 
go over all the command ands stuff.

thanks for the help!:KS

---

### Post by kellemes on 2008-02-03
[http://eu.wiley.com/WileyCDA/WileyTitle/productCd-0470125055.html](http://eu.wiley.com/WileyCDA/WileyTitle/productCd-0470125055.html)
;-)

---

### Post by sirfonners on 2008-02-03
lol thanks



does anyone know how to help me with my visual effects problem?
when i try to switch "extra"

it says ```
 The composite extension is not available
```

how do you fix that?

---

