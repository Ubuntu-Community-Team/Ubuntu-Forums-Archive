---
title: "Opening Files as Administrato in Gnome/Nautilus"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by creed1 on 2007-04-02
Hello there,

I have installed Ubuntu and am loving it so far =).

One question, in other distro's I have been able to right-click a file, say, xorg.conf, and have the option to 'Open as Administrator'.

I would then be prompted for a password, and then be able to modify my file accordingly.

I found this method very easy. Im using Ubuntu dapper 6.06.

Any advice on how to enable this feature will be appreciated =O).

Thank You =).

---

### Post by justleen on 2007-04-02
create a new laucnher, and add this as command
```
 gksudo nautilus 
```
that will open a file browser with root-rights

---

### Post by justleen on 2007-04-02
option 2:
copy paste this in a terminal
```
gedit ./.gnome2/nautilus/scripts/admin_edit 
```

and paste the following in the new file
```

#!/bin/sh
gksudo gedit $@

```

save and exit.
if you now right click on a file, you will have an option under Scripts called admin_edit.. it will ask for a pasword, and edit as root..

---

### Post by Obor on 2007-04-02
If you want to add right click option in nautilus to open as root do this in terminal
```

gedit $HOME/.gnome2/nautilus-scripts/Open\ as\ root
```

Paste the following into file
```
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gksudo "gnome-open $uri" &
done
```

and run this in terminal
```
chmod +x $HOME/.gnome2/nautilus-scripts/Open\ as\ root
```

Now you can right click on file and choose scripts - open as root

Edit: too late :)

---

### Post by 3rdalbum on 2007-04-02
lol... beaten by two people! Use the 2nd method described as it allows you to edit more than one file.

---

### Post by creed1 on 2007-04-02
Thank you all =)

I will give it a go tonight. I really appreciate it.

Peace.

---

### Post by zvacet on 2007-04-02
[http://doc.gwos.org/index.php/Nautilus_Scripts]("http://doc.gwos.org/index.php/Nautilus_Scripts")

---

### Post by creed1 on 2007-04-02
Hello all,

Just wanted to report that I do not think I have had success with the instructions.

I first ran the instructions from Obor but I didnt seem to have success. I then ran the instructions on the link from zvacet, but it still doesnt seem right.

Am I correct in saying that now I should be able to right-click a file (any file) and have the option to open it as root? Because the shell script looks no different.

Any advice would be great,

Thanks again.

---

### Post by creed1 on 2007-04-02
UPDATE: Sorted. Thanks for all your help, got it sussed.

Appreciate it =)

---

