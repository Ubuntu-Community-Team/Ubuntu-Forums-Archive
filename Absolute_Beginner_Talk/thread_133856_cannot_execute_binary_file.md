---
title: "cannot execute binary file"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by cheezit on 2006-02-20
I downloaded and tried to install Conesxant's modem driver. 

These are Conexant's instructions:

* Download the installation program (cnxtinstall.run)
* Open a terminal window. (If you don't know how to do this, press ALT-F2 and in the dialog box that will appear, try entering one of the following commands: xterm or konsole or gnome-terminal)
* Use the cd command to access the directory where the cnxtinstall.run file was downloaded.
* Finally, enter the sh cnxtinstall.run command to run the installer.

I copied the file from my CD to Desktop then...

root@ubuntu:/home/randy# bash install cnxtinstall.run
/usr/bin/install: /usr/bin/install: [COLOR="Red"]cannot execute binary file[/COLOR]
root@ubuntu:/home/randy#

Randy

---

### Post by gord on 2006-02-20
make sure you are in the directory that the file is in and 
```

chmod +x cnxtinstall.run
./cnxtinstall.run

```

you might need to do "sudo ./cnxtinstall.run", it depends on what the installer wants to do (for example, if it starts saying it doesn't have permition to do things)

---

### Post by qferret on 2006-02-20
Also, make sure the "Execute" permissions are set...

---

### Post by gord on 2006-02-20
that is what "chmod +x cnxtinstall.run" does

---

### Post by cheezit on 2006-02-21
Desky

I have a copy of this file in 2 places: one is on a CD and the other is on my Ubuntu Desktop.


sudo chmod u+x cnxtinstall.run
chmod: cannot access 'cnxtinstall.run": no such file or directory

./cnxtinstall.run
bash: ./cnxtinstall.run: No such file or directory

Randy

---

### Post by gord on 2006-02-21
first of all, my name is gord not desky ;) thats just a link to my desktop in my sig. you need to make sure you follow my instructions exsacly, you typo'ed a bit in the chmod bit. copy and paste if you need to

also your not in the right directory. if you want to get into your desktop directory from the command line (which is where the file is held) type this first. 
```

cd ~/Desktop

```

then re-type what i posted previously

---

### Post by qferret on 2006-02-22
[QUOTE=gord]that is what "chmod +x cnxtinstall.run" does[/QUOTE]

DOH!


/me writes:

Thou shalt read carefully before postin....thou shalt read carefully before posting...shou shalt read care......   :-#

---

