---
title: "help with xorg.config"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by hempa on 2008-02-19
hello i need some help with what commands i should use if i want to backup my xorg.config file. and i would also need some help with a command to use for logging in with the xorg.config backup file if the new one crashes( it has happend before and since i did not know how to login with the backup i had to reinstall )  thanx

---

### Post by billgoldberg on 2008-02-19
You can use "sudo nautilus" and then navigate to the file and copy it the gui way. It's easier to remember.

---

### Post by jken146 on 2008-02-19
> **billgoldberg said:**
> You can use "sudo nautilus" and then navigate to the file and copy it the gui way. It's easier to remember.

This should be ```
gksudo nautilus
```  For an explanation, see [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)


Here's the command line way:

First, make a backup of xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Then edit xorg.conf to your heart's content, knowing that when you mess up you can reboot into Recovery Mode and restore the backup.
```
cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

Then reboot.
```
reboot
```

---

### Post by hempa on 2008-02-19
ok but how do i use the backup xorg.config when i login asuming that the new one crashed my graphics and i can only use the terminal?

---

### Post by Tatty on 2008-02-19
cp is the copy command, so

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

will make a copy of xorg.conf called xorg.conf.backup

and

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

will restore the origional.

Of course you could call the backup whatever you want, but i always use xorg.conf.backup to keep it simple.

**Edit: Beaten to it! :)**

---

### Post by hempa on 2008-02-19
thanx did not se your first reply before posting my last question. thats the commands i was looking for you saved my day. now im gonna go crazy on my xorg.config

---

### Post by erfahren on 2008-02-19
back up your current with the command:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_back

```
(which just means: copy the file and name the copy "xorg.conf_back") - the backup can be named whatever you want of course - I sometimes number mine "_back1", "_back2", and so on - I go and clean them out periodically

so to restore the backup in recovery mode - I usually change directory to the /etc/X11 directory first (saves on typing)
```

cd /etc/X11

```
then you can list the contents (in case you don't remember the file names)
```

ls 

```
you should see your backups in there - if the good one is "_back1" just copy it back over the original
```

sudo cp /etc/X11/xorg.conf_back1 /etc/X11/xorg.conf

```
(if you are in the recovery mode (text only) where it asks for the root password - you get the root prompt "#" - then using "sudo" isn't necessary)

if you ever get in a real fix and don't have a backup of a file you edited you can use "nano" (the command line text editor) to undo the changes (if you can remember them!) - so for example, as root
```

nano /etc/X11/xorg.conf

```
and to save the file and exit you press Ctrl+X

more on basic terminal usage:
[Terminal for Beginners](http://ubuntuforums.org/showthread.php?t=73885)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[Know Your Terminal Commands, Terminal references](http://ubuntuforums.org/showthread.php?t=171507)
this site is good as well
[Linux Online - Linux Courses](http://www.linux.org/lessons/index.html)

---

