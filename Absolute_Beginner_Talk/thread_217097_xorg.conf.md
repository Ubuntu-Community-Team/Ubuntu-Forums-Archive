---
title: "xorg.conf"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by jrjr on 2006-07-16
I need to edit xorg.conf but its read only. I assume this is due to ownership by root. What do I do to edit it or replace it with a test file?
In terminal I know to do sudo -i
Ive tried all kinds of commands to open gedit with command line and edit this file but nothing has worked for me so far. Things shouldnt be this hard to find out how to do... its been hours

---

### Post by Iandefor on 2006-07-16
try ```
gksudo gedit
``` You might also try ```
sudo nano
``` With nano, just remember that the "^" preceding the commands listed just means [ctl]. Also, it's just sudo, not sudo -i.

---

### Post by jrjr on 2006-07-16
> **Iandefor said:**
> try ```
gksudo gedit
``` 

Gtk-WARNING **: cannot open display


> **Iandefor said:**
> 
You might also try ```
sudo nano
``` With nano, just remember that the "^" preceding the commands listed just means [ctl]. Also, it's just sudo, not sudo -i.

This changes terminal to something strange, not sure what to do with it

sudo -i   gives me a prompt as root though. sudo itself does nothing at the prompt except bring up the command suggestions

---

### Post by Jagot on 2006-07-16
From Terminal you could try:

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by jrjr on 2006-07-16
Yep that worked...  thank you!! (I was running out of hair to pull out) ](*,) 
I was doing the sudo -i first
Without doing that your command worked ok

NOW....  If I want to just rename the original xorg.conf and place a trial version in there how would I get that done?? 

I have backed it up by doing this:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

In case I screw things up I have printed instructions on how to replace the backup.

---

### Post by Iandefor on 2006-07-16
> **jrjr said:**
> This changes terminal to something strange, not sure what to do with it

sudo -i   gives me a prompt as root though. sudo itself does nothing at the prompt except bring up the command suggestions That's nano. It's a text editor. You use sudo before a command, not on it's own.

---

### Post by jrjr on 2006-07-16
Ok, I have edited my file, rebooted and it didnt work. Replacing the file with the backup at terminal worked ok so now all I need to do is figure out how to get the correct language in my xorg.conf file. Thanks!!

---

