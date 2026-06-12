---
title: "seeing double?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-04-23
how come i have so many xorg.conf files?  can i get rid of some of them?  and if so then how?  and how do i make a new backup of my current one?  here's a screenshot.

[http://i159.photobucket.com/albums/t147/clipsandeggs/Screenshot-3.png](http://i159.photobucket.com/albums/t147/clipsandeggs/Screenshot-3.png)

there are two or three more outside the screenshot.

---

### Post by miggols99 on 2007-04-23
They are just backups created automatically. You can delete the others if you want.

---

### Post by locke.dragon on 2007-04-23
but it won't let me delete them.  and how do i create a backup?  i've done it before, just forgot what to put into terminal.

---

### Post by Cypher on 2007-04-23
the file "xorg.conf" is your current configuration file. Open up a terminal window and type "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup" and then you can do "sudo rm /X11/xorg.conf.2007*" and they'll be gone.

Regards

---

### Post by locke.dragon on 2007-04-23
when i try to remove it, it gives me this...

```

link@Ubuntu:~$ sudo rm /X11/xorg.conf.2007*
Password:
rm: cannot remove `/X11/xorg.conf.2007*': No such file or directory
link@Ubuntu:~$ 

```

and how to i replace my current xorg.conf with the backup?  thanks for the help!

---

### Post by sisco311 on 2007-04-23
to backup:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
to delete:
```
sudo rm /etc/X11/xorg.conf.2007*
```

---

### Post by Cypher on 2007-04-23
> **locke.dragon said:**
> when i try to remove it, it gives me this...

```

link@Ubuntu:~$ sudo rm /X11/xorg.conf.2007*
Password:
rm: cannot remove `/X11/xorg.conf.2007*': No such file or directory
link@Ubuntu:~$ 

```

and how to i replace my current xorg.conf with the backup?  thanks for the help!
Oopsie..forgot the "/etc" before X11..:)

Regards

---

### Post by locke.dragon on 2007-04-23
thanks!  it worked!

---

### Post by sisco311 on 2007-04-23
> and how to i replace my current xorg.conf with the backup? thanks for the help!
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```
if /etc/X11/xorg.conf_backup is your backup file name

---

### Post by Cypher on 2007-04-23
I'm glad..but a word of warning, always double check the commands that you get from people on the forums, it's very easy for any of us to mis-type and since you are doing all of these with ROOT priv's, you could very easily erase something necessary and have a borked OS. :)

Regards

---

### Post by locke.dragon on 2007-04-23
don't worry cypher.  i'll be careful.  thanks again!

---

