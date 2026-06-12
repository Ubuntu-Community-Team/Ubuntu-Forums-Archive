---
title: "Error trying to run KTorrent in Gnome"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by Westies on 2006-12-05
I installed KTorrent and it shows up in Apps>Internet>KTorrent, but if you click on it, it does nothing. Opening the terminal and trying to run it gives me this error:

jeff@JeffLinux:~$ ktorrent
trying to create local folder /home/jeff/.kde/share: Permission denied
trying to create local folder /home/jeff/.kde/share: Permission denied
trying to create local folder /home/jeff/.kde/share: Permission denied
trying to create local folder /home/jeff/.kde/socket-JeffLinux: Permission denied
trying to create local folder /home/jeff/.kde/socket-JeffLinux: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/jeff/.kde/socket-JeffLinux/kdeinit__0'
ERROR: KUniqueApplication: Can't setup DCOP communication.

I can open it if I do a "sudo ktorrent", but that's a bit inconvenient...

---

### Post by dbd on 2006-12-05
Does the folder .kde exist, you could try making it.
(to see if it exists use the command "ls -a" to show hidden folders)

---

### Post by Westies on 2006-12-05
Yeah, it's there. The other folders it mentions are there as well.

---

### Post by Westies on 2006-12-05
bump

---

### Post by jordanmthomas on 2006-12-05
```
sudo chmod 666 ~/.kde
```
Then try to run ktorrent again maybe?

---

### Post by Shinoda on 2006-12-23
The same happened to me, and it turned out [FONT="Courier New"]~/.kde[/FONT] was owned by and grouped in [FONT="Courier New"]root[/FONT]. It would have probably worked to [FONT="Courier New"]sudo chown -R[/FONT] and [FONT="Courier New"]sudo chgrp -R[/FONT] it to my username, but I just removed the folder with [FONT="Courier New"]sudo rm -rf ~/.kde[/FONT] (careful, it might have needed stuff inside) and then recreated it manually using [FONT="Courier New"]mkdir ~/.kde[/FONT] (without [FONT="Courier New"]sudo[/FONT]).

---

