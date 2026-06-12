---
title: "I need to manually uninstall files in a terminal but don't know the commands."
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-12
Hi,

I did a search for easyamsn and I need to manually delete the following 6 files.
I don't know what commands to type into the terminal.

Thanks.


easyamsn
(link to shell script)
/usr/bin


easyamsn
(folder)
/usr/local


easyamsn.png
(PNG image)
/usr/local/easyamsn/conf


easyamsn
(shell script)
/usr/local/easyamsn


easyamsn_l
(shell script)
/usr/local/easyamsn


easyamsn.desktop
(desktop configuration file)
/usr/shar/applications

---

### Post by uzi09 on 2006-06-12
for folders, just type:
```

rm -rf easyamsn_folder

```

for file:
```

rm -f easyamsn_file

```

you may also have to use sudo in front of some of those.

ALSO A BIG FAT WARNING:
when you're using:
```
rm -rf folder
```
be verrrrrrry careful (ESP. when used with sudo) because it'll recursively AND FORCEFULLY (which means it won't ask twice) remove all files in the directory then the directory itself!!!!

---

### Post by taurus on 2006-06-12
You need to get into the same directory that you built it, source.  However, this time, you have to run 
```

sudo make uninstall

```
to uninstall it if you used "sudo make install" to install it...

---

### Post by u.b.u.n.t.u on 2006-06-12
Thanks,

I tried the following and it seems to have worked. Except the icon is still at

Applications / System Tools / Easy AMSN

Not the Easy AMSN icon but a default one. So this program is still on my computer.

Any suggestions as to how to deleted this icon here?

Applications / System Tools / Easy AMSN

These commands worked.

sudo rm -rf /usr/bin/easyamsn

sudo rm -rf /usr/local/easyamsn

sudo rm -rf /usr/share/applications/easyamsn*
[B]
[COLOR="Red"][SIZE="4"]Note to self: ONLY ever install from synaptic unless on a test machine.[/SIZE][/COLOR][/B]

---

### Post by u.b.u.n.t.u on 2006-06-13
"Not the Easy AMSN icon but a default one. So this program is still on my computer.

Any suggestions as to how to deleted this icon here?

Applications / System Tools / Easy AMSN"


I found a solution.

Applications > Accessories > Alacarte Menu Editor

Then right mouse click on the icon and select "delete".

The delete option only seems to appear for the default icon after the actual icon was deleted.

---

