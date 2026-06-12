---
title: "Starting the GUI on Ubuntu Server 7.04"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Horrortubby on 2007-06-07
Hi all,
I just installed the Ubuntu Server 7.04 with LAMP, DNS Server and so on. Also i installed the "ubuntu-desktop" and now i wanted to know how to start the desktop? 

And do you have an advise for some good beginner tutorials for ubuntu server?

thanks,
Jan

---

### Post by Malibu Illusion on 2007-06-07
Type:

```
startx
```

Into the CLI.

---

### Post by Horrortubby on 2007-06-07
thanks, but i already tried and here is the answer :(
"xstart: command not found"

---

### Post by Malibu Illusion on 2007-06-07
"startx" not "xstart".

---

### Post by Ken_Lewis81 on 2007-06-07
I'm not sure if this will let you automatically load GNOME each time you start up, but the command is:
```
sudo etc/init.d/gdm start
```

Take care.
Ken.

---

### Post by Horrortubby on 2007-06-07
i tried startx also... but it didnt work. Then i tried to install again with "apt-get install ubuntu-desktop". After the installation i tried startx again and then he said that he cant log the authoriy file in /home/username/.Xauthority

---

### Post by Horrortubby on 2007-06-07
> **Ken_Lewis81 said:**
> I'm not sure if this will let you automatically load GNOME each time you start up, but the command is:
```
sudo etc/init.d/gdm start
```

Take care.
Ken.

Thanks, but it returns the command "sudo: etc/init.d/gdm: command not found"

---

### Post by hillbilly on 2007-06-07
he would have meant > /etc/init.d/gdm start

startx would should have worked too.  I assume you are on the Virtual Terminals. So press > Alt+F7 and I think that should take you to the GUI screen. Plus if you had installed ubuntu-desktop, if you reboot, it should have automatically taken you to the GUI login screen. Can you let us know what your default run level is ?

---

### Post by Horrortubby on 2007-06-10
Thanks for your help guys, but nothig works :(  I setted up the system again an and splitted it this way:
    
* boot-Partition (/boot): 50 MB, ext3, primary
* LVM-Partition 
LVM:

    * root-Partition (/): 300 MB
    * /usr: 2 GB, (500 MB)
    * /var: 1 GB, 
    * /tmp: 200 MB
    * /home: 10GB
    * swap: 2000MB
    * /usr/local: 100 MB 
    * /opt: 100 MB 

After installation i typed "apt-get update" (works fine), and "apt-get install ubuntu-desktop". Than the system began to Download the needed files and began to extracting it. After a few minutes he throws an error that he get to much errors. Also i tried "apt-get install gdm" here he throws the error: "No fullfiled relations. Try "apt-get -f install" without packeges" (i traslated this error message from german, don't know the correct english expression)
Of course "startx" or "sudo /etc/init.d/gdm start" doesen't work :(

---

### Post by handaxe on 2007-06-10
You seem essentially to be doing the right thing!

Try these steps

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-update
sudo apt-get install ubuntu-desktop
```

That should install gdm and metacity (the window manager) but check this

```
sudo apt-get install gdm metacity
```

HA

---

