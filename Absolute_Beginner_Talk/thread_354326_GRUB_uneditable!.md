---
title: "GRUB uneditable!"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by i-am-me on 2007-02-05
I dual boot Windows as my main OS and Kubuntu as a secondary OS. I want to use Windows as the the OS that boots by default, so I tried to edit my menu.lst file. I changed "default 0" to "default 4" so that Windows would boot by default so I wouldn't constantly have to select it. The problem :mad: is that it won't let me save my edits. It says that either there isn't enough space (I gave it 24 gig) or that I have insufficient privileges. :confused: :confused: :confused: Yes, I'm logged in as the root (the one that I created during installation is root right?), so don't tell me that I should log in as root to do this. What is a guy supposed to do (I even tried to reinstall Kubuntu, so that's out of the question and I checked the Live CD and it doesn't have any defects)?!:confused: :confused: :confused:

---

### Post by aidanr on 2007-02-05
the user you create when you install is not root

you want to open a terminal and type 
```
sudo gedit /boot/grub/menu.lst
```
and type in your password

edit:// of course #-o, kate/kwrite instead of gedit

---

### Post by shareMenaPeace on 2007-02-05
Hi, 
root is root.
During install you created a user account which you should use.

When you edit a file you can do this as root.

One way is use

```
sudo gedit /path/to/the/file  
```
Now you need to type your password and can edit/save.

And see that you type case sensitive eg. /etc/X11/
 
Incase you mess up grub make a BACKUP of the file before you edit it.

---

### Post by i-am-me on 2007-02-05
> **shareMenaPeace said:**
> Hi, 
root is root.
During install you created a user account which you should use.

When you edit a file you can do this as root.

One way is use

```
sudo gedit /path/to/the/file  
```Now you need to type your password and can edit/save.

And see that you type case sensitive eg. /etc/X11/
 
Incase you mess up grub make a BACKUP of the file before you edit it.

Wait... where do I type my password? In the terminal?

---

### Post by shareMenaPeace on 2007-02-05
Yes all this commands ... boot login and choose 

Applications -> Asseccoires -> Terminal (right click terminal and choose "Add this launcher to panel" to see it on top panel).

When you run the gedit editor with sudo it will ask you for the password than. Type it in (not visible) and hit enter.

---

### Post by i-am-me on 2007-02-05
> **shareMenaPeace said:**
> Yes all this commands ... boot login and choose 

Applications -> Asseccoires -> Terminal (right click terminal and choose "Add this launcher to panel" to see it on top panel).

When you run the gedit editor with sudo it will ask you for the password than. Type it in (not visible) and hit enter.

Sorry to ask again, but since I use Kubuntu, things work differently and the sudo gedit ... command doesn't work for some reason. Do you know what to do in Kubuntu?

---

### Post by ardchoille42 on 2007-02-05
You should never use sudo with GUI apps, use gksudo. Or I think it's kdesu gedit in kubuntu

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Using sudo with GUI apps can break things.

---

### Post by shareMenaPeace on 2007-02-05
> **ardchoille42 said:**
> You should never use sudo with GUI apps, use gksudo. Or I think it's kdesu gedit in kubuntu

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Using sudo with GUI apps can break things.

Thanks!

So use than

ALT + F2 and type 

[HTML]gksudo nautilus[/HTML] now you need to browse with nautilus to the file and rightclick edit.

or use in terminal

```
nano -B /etc/X11/xorg.conf
```

-B to make a backup file

---

### Post by shareMenaPeace on 2007-02-05
Or use 

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by RomeReactor on 2007-02-05
Sinc you're running Kubuntu, that should be:

```
kdesu kwrite /boot/grub/menu.lst
```

or

```
kdesu kate /boot/grub/menu.lst
```

---

### Post by i-am-me on 2007-02-06
:) Thanks all of you, especially the one that posted the link. I successfully edited grub and now I can boot to Windows directly.):P

---

