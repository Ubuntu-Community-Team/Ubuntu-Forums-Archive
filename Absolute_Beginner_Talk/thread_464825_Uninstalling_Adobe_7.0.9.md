---
title: "Uninstalling Adobe 7.0.9?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by Alan O'Regan on 2007-06-05
I installed adobe from a tar.gz using "run in terminal" option on the install file.  In trying to terminate the resulting job (it usually failed with permission error) I hit <ctrl>C when it was asking for location.  This installed it successfully into my downloads directory!  I would prefer a 'normal installation' into usr/local (which I subsequently did with sudo <....targ.gz>.

However, now I cannot find a way to remove either installation.

Ideas anyone (this is my first day with ubuntu).

---

### Post by Kobalt on 2007-06-05
Ususally, you do it this way : open up a Terminal and go into you "adobe" directory using the command *cd* : ```
cd /path-to-folder
```
Then run ```
sudo make uninstall
sudo make clean
```

---

### Post by Alan O'Regan on 2007-06-05
> **Kobalt said:**
> Ususally, you do it this way : open up a Terminal and go into you "adobe" directory using the command *cd* : ```
cd /path-to-folder
```
Then run ```
sudo make uninstall
sudo make clean
```

Thanks Kobalt

I tried that - but I don't know which 'Adobe' directory you mean, and "sudo make uninstall fails in all the possibilities.  See:

alan@alan-dell4150:~$ cd Downloads
alan@alan-dell4150:~/Downloads$ cd Adobe
alan@alan-dell4150:~/Downloads/Adobe$ sudo make uninstall
Password:
make: *** No rule to make target `uninstall'.  Stop.
alan@alan-dell4150:~/Downloads/Adobe$ cd AdobeReader
alan@alan-dell4150:~/Downloads/Adobe/AdobeReader$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.
alan@alan-dell4150:~/Downloads/Adobe/AdobeReader$ cd ^[/
]0;alan@alan-dell4150: ~/Downloads/Adobe/AdobeReader/alan@alan-dell4150:~/Downloads/Adobe/AdobeReader/$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.
]0;alan@alan-dell4150: ~/Downloads/Adobe/AdobeReader/alan@alan-dell4150:~/Downloads/Adobe/AdobeReader/$ 

You will notice that when I typed <ctrl>C in the script I got the directory ^[/

Any ideas?

---

### Post by taurus on 2007-06-05
If it installed to your download directory in your $HOME, just remove it with the rm command.  Then, install it again but this time, use **sudo** so you can install it to /usr/local/bin.

---

### Post by Alan O'Regan on 2007-06-06
Thanks, Taurus, that seems to have worked.  I could not seem to zap just the directory it created - "\033", I had to zap the parent directory - but that was OK.

thanks!

Alan

---

