---
title: "Is there a way ??"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by MrKlean on 2007-12-24
Is there a way to reinstall Ubuntu without formatting the partitions ?? So it keeps the data but over writes the program files ??
Thanks ; )

---

### Post by Perpetual on 2007-12-24
If you created a seperate /home directory, yes.  You can simply do a new install, format / but do not format /home.  If you did not create a seperate /home, I would first create a seperate partition /MyData (or whatever you want to call it) and move any documents into that partition.  You can do this with gparted.

Then do the reinstall, create a new / and new /home and format both but do not format the /MyData partition you created above.

For details about creating the partition with gparted see a [psychocats tutorial]("http://www.psychocats.net/ubuntu/separatehome").

---

### Post by logos34 on 2007-12-24
> **MrKlean said:**
> Is there a way to reinstall Ubuntu without formatting the partitions ?? So it keeps the data but over writes the program files ??
Thanks ; )

No, if you have just / and /swap.

---

### Post by LaRoza on 2007-12-24
> **logos34 said:**
> No, if you have just / and /swap.

That is true.

But you can copy your home directory and put it back when you reinstall, this will keep all your settings.

Example:

I reinstalled Ubuntu a while ago, moved my ~/.purple directory (Pidgin) and had all of my settings and contacts in the new install.

---

