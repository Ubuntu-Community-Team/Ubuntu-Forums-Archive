---
title: "I blew up ubuntu"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by blackmajik2021 on 2007-05-08
I broke the x server and now i cant use the GUI. Im sure i can fix it if someone can explain to me how to undo what i did. 

i put this in the terminal 

cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
gksudo gedit /etc/X11/xorg.conf

and then i added this to the document 

Section "ServerFlags"
Option "Xinerama" "true"

EndSection

if someone can explain to me how to edit the xorg config with no gui im sure i can delete what i added and get it back up and running (i hope). i posted this is the original topic so i hope you dont mark me for a double post because its a different topic than the topic that i posted it in. ok thanks.

byee

---

### Post by heimo on 2007-05-08
On terminal, type:
```
sudo cp /etc/X11/xorg.conf_bak /etc/X11/xorg.conf
```
That should replace your edited file with the backup file you created. Then restart Xorg.
```

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

---

### Post by blackmajik2021 on 2007-05-08
this didn't work, i did exactly what you said, it said they weren't commands or something like that, or files not found. I'm not sure. maybe it was command not found. either way it didn't work, and i spelled everything right.

---

### Post by rsambuca on 2007-05-08
Keep in mind that linux filename and folder names are case sensitive.

You can also try```
sudo nano /etc/X11/xorg.conf
``` to edit the file.  The nano command just allows you to edit the file directly in the terminal window.  Just comment out the two lines you added by putting a number sign "#" in front of them.  Then restart X.

---

### Post by blackmajik2021 on 2007-05-09
i typed that in EXACTLY with case sensitivity and all and i keep getting "no such file or directroy"

am i supposed to type in 

cp/etc/X11/xorg.conf_bak /etc/X11/xorg.conf

or am i supposed to type in 

cp/etc/X11/xorg.conf_bak 

then press enter

/etc/X11/xorg.conf

then press enter again

also, i did it both ways, about 10 times and every time i get "no such file or directory", but when i ask for the diagnosis it tells me the error is in that location(xorg.conf). I really really dont get why this is not working. I also tried the nano cp thing but it confused me. I tried sudo cp also.

---

### Post by pillu on 2007-05-09
there is a space after cp
as in 
```
sudo cp /etc/X11/xorg.conf_bak /etc/X11/xorg.conf
```
There is a space after sudo, cp and after the backup file path name
Also to get a temporary gui, you could boot from the live CD and work through that.

pillu

---

### Post by drowner on 2007-05-09
edit: duplicate!

---

### Post by blackmajik2021 on 2007-05-09
ok, so that helped a little, now it says "cp cannot stat '/etc/X11/xorg.conf_bak' no such file or directory exists but it now picks up that ive typed it in right. i think i may have typed the first code in wrong and not created a backup. what should i do in that case.

---

### Post by Sef on 2007-05-09
> I never created a backup file is that whats wrong?

Yes, you can't copy a back up file if you never created it.

Read [Psychocat's Nox]("http://www.psychocats.net/ubuntu/nox") for help on how to get X.org back up.

---

