---
title: "How do I get access to my root?"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by Flamez on 2006-04-04
Im installing NDISwrapper, but without axcess to my root it cant install the drivers.

---

### Post by shyopstv on 2006-04-04
In Ubuntu, sudo replaces root for security measures. You have to type sudo at the beginning of each command to get root access it will then ask you for your password

---

### Post by carlosqueso on 2006-04-04
Just use ```
sudo <command>
``` to temporarily become root.  When it asks for your password, just use your regular password.  If you want to know more about why, go to [https://wiki.ubuntu.com/rootsudo](https://wiki.ubuntu.com/rootsudo)

---

### Post by dalyraptor on 2006-04-04
how do you open a conf file as root to edit it?

---

### Post by tappad on 2006-04-04
"sudo nano /path/to/config"
or
"sudo gedit /path/to/config"

You can also use "sudo su" to act as root on all commands, then you dont have to do sudo all the time..

---

### Post by dalyraptor on 2006-04-04
thanks for the tip. when i run gedit from the terminal i get:

(gedit:9174): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

and now i can't type commands, is there a way around this?

---

### Post by tappad on 2006-04-04
No idea why you got that error.. :(
However, you could try: sudo nautilus
Then locate your file and open it as usual (double click on it)

---

### Post by Mustard on 2006-04-04
[QUOTE=dalyraptor]thanks for the tip. when i run gedit from the terminal i get:

(gedit:9174): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

and now i can't type commands, is there a way around this?[/QUOTE]

That error is fairly common when opening graphical applications from command line, but doesnt always stop the editor from working.  Also the issue of 'not being able to type in more commands' would be because it is running gedit from that terminal, so to run more commands you would need to open another terminal, or you could close gedit and release that terminal so that you can type commands in it again.

There is a problem that occurs on occasion in which the ICE/X authority files become corrupted when using the command 'sudo gedit /path_to_file'.  It is recommended that when you start graphical apps from the command line that you use 'gksudo' instead.  This does make editing with gedit a bit more cumbersome though, as you would have to use this syntax...

An example of editing your /etc/fstab.

```
gksudo 'gedit /etc/fstab'
#note the single quotations around the command
#and the pathname are necessary

#if you skip these single quotations
#it will open up a blank new file called fstab'
#which will be the wrong file, because
#gksudo will add a single quote to the end of the filename.
```

I have to admit to being quite lazy myself and I still use just...

```
sudo gedit /path_to_file
```

:)

---

### Post by Mustard on 2006-04-04
[QUOTE=tappad]No idea why you got that error.. :(
However, you could try: sudo nautilus
Then locate your file and open it as usual (double click on it)[/QUOTE]
Again the syntax for this command should be..

```
gksudo nautilus
```

This will avoid possible corruption of the .ICEauthority and .Xauthority files (which can happen on occasion and will muck up your login until you delete these files from your Home folder)

---

### Post by gr0kzer0 on 2006-04-04
BE VERY CAREFUL WIT THIS: in users/groups, u can change root pw to what ever u want. then in a terminal (tho not xterm i dont think) u will be root. just change back asap and dont make any foulups. use root sparingly, sudo's ok for most things. but sometimes, longs u got yr brain on, root is extremely useful. i use it -sometimes - but DONT USE ROOT ON THE NET!

---

