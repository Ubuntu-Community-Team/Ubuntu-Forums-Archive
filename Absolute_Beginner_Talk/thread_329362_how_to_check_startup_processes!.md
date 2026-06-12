---
title: "how to check startup processes?!"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by Mazen on 2007-01-01
what is the terminal command to check the processes that startup?

---

### Post by taurus on 2007-01-01
You mean when Ubuntu boots!  You can remove the **quiet** from the kernel entry in /boot/grub/menu.lst...

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Mazen on 2007-01-01
no no this will give me the list of OS i can boot with grub !! i want to know what processes are running in Ubuntu, other than ```
top
```

---

### Post by autocrosser on 2007-01-01
How about Menu>System>Administration>System Monitor & tic the tab for all processes--then View>All Processes?

---

### Post by Solver on 2007-01-01
For currently running processes, you'll want ps.

Executing

```

ps
```

will show processes from the same user and the same terminal.

Doing

```

ps -A
```

will give you all processes on the machine.

---

### Post by Frank Golden on 2007-01-01
Go to Synaptic and enter bootchart into the search field.
Install bootchart.
When you reboot and everytime after a small .pmg file will be created in /var/log/bootchart that in addition to showing boot time will also show
processes and programs started at boot. You can create a launcher to this folder using the
command [gksudo nautilus /var/log/bootchart] without the brackets. This will allow 
root access to this folder to view the latest file and delete them. Bootchart does not overwrite older files so they will accumulate.

Also the previous suggestion about removing quiet from the boot entry in /boot/grub/menu.lst is partially correct. What you do is replace quiet splash
with verbose. You will then be treated to a realtime scrolling list of your boot processes.
If you click on "I" at the right time you are allowed to interact.

---

