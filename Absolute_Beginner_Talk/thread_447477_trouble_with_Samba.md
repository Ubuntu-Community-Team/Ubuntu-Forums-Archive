---
title: "trouble with Samba"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by jabbapam on 2007-05-18
I'm very new to linux and have installed Ubuntu 7.04 on a pc that has xp on another partition.

I had gsambad 0.1.4-2 setup and working when I first trialled it on an old disk, but now it wont work, when i start it comes up with:


'Could not launch menu item'
Failed to execute child process "su-to-root" (No such file or directory)


Can anyone help?
Please if you can, could describe what I need to do in the most basic way as I have no idea about command usage. 

I have reinstalled it 3 times via synaptic with no change.

I downloaded samba from their website but have no idea how to install it.

---

### Post by RichGuk on 2007-05-18
Just get samba via apt-get..

```
sudo apt-get install samba smbfs
```

There are plenty of guides in the forums, or here.. [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server)

---

### Post by jabbapam on 2007-05-18
used that but still get the error

---

### Post by RichGuk on 2007-05-18
The same errors as above?

---

### Post by jabbapam on 2007-05-18
yes

---

### Post by RichGuk on 2007-05-18
Apparently the problem with su-to-root is the menu entry containing the wrong sudo call, edit the menu item and change su-to-root to gksudo -S


Tried remove it, and its config files?


```
sudo apt-get remove --purge samba smbfs
```

Then installing

```
sudo apt-get install samba smbfs
```

Make sure its started

```
sudo /etc/init.d/samba start
```

?

---

### Post by jabbapam on 2007-05-18
Just tried your remove and reinstall suggestion. It returned with...

* Starting Samba daemons...                                             [ OK ] 

Now the menu item is gone.

---

### Post by RichGuk on 2007-05-18
That sounds like Samba is running, you can now set about setting up your shares by editing the samba config file..

```
sudo gedit /etc/samba/smb.conf
```

Use the guide I linked to setup the type of share you want..

:)

---

### Post by jabbapam on 2007-05-18
When i try to connet from my xp laptop to my ubuntu pc. it keeps asking for a password. i tried the password change but it came up with...


joe@joe-desktop:~$ sudo smbpasswd -a system_joe
New SMB password:
Retype new SMB password:
Failed to modify password entry for user system_joe
joe@joe-desktop:~$ 


any ideas?

---

### Post by RichGuk on 2007-05-18
```
sudo smbpasswd -a joe
```

Is most likely what you'll want :)

---

### Post by jabbapam on 2007-05-18
Thank you, that worked great.

Now all I have to do is setup remote printing from XP laptop to ubuntu pc that has the printer on it....

Then setup the wireless LAN...

---

### Post by RichGuk on 2007-05-18
Have fun :D

You can do the printer via Samba :), not to sure about the wireless (sorry :))

---

### Post by jabbapam on 2007-05-19
Thank you, you have been a great help.

However I've done something so that when I go Administration>Printing

I get a warning = " CUPS server could not be contacted"

I've removed and reinstalled cups with no change.

---

