---
title: "Deleting desktop icons"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by cpeachey on 2008-04-21
I cannot delete icons on my desktop because the "owner" is root. How do i change this?
Ubuntu 7.1 (new user!
Chris:frown::frown::frown:

---

### Post by atomkarinca on 2008-04-21
Open up a terminal and type this:

```
cd ~/Desktop
sudo rm whatever_you_want_to_delete
```

---

### Post by lizzard on 2008-04-21
```
sudo rm ~/Desktop/*iconyouwannaremove*
``` should do it.

---

### Post by y-lee on 2008-04-21
Type

```
gksudo nautilus
``` 

Into a terminal and enter your password right click the icon and choose delete.

Note: the methods posted above also work :)

---

### Post by sisco311 on 2008-04-21
or you can change the owner of the file

type:
```
sudo chown -R username\: /home/username/Desktop
```Replace username with your user name.
for exemple:
```
sudo chown -R cpeachey\: /home/cpeachey/Desktop
```

---

### Post by y-lee on 2008-04-21
Also note some icons such as Computer document and trash can be controlled from the Configuration Editor. you can open this application by

```
gconf-editor 
```

go to apps-->nautilus-->desktop and then check or uncheck options there.

---

### Post by cpeachey on 2008-04-21
No go
This is what I typed with the responses...

chris@chris-desktop:~$ sudo rm ~/Desktop/"Samsung Unified Driver Configurator"
rm: cannot remove `/home/chris/Desktop/Samsung Unified Driver Configurator': No such file or directory
chris@chris-desktop:~$ sudo rm ~/Desktop/Samsung Unified Driver Configurator
rm: cannot remove `/home/chris/Desktop/Samsung': No such file or directory
rm: cannot remove `Unified': No such file or directory
rm: cannot remove `Driver': No such file or directory
rm: cannot remove `Configurator': No such file or directory
chris@chris-desktop:~$ 
chris@chris-desktop:~$ sudo rm ~/Desktop/install_flash_player_9_linux
rm: cannot remove `/home/chris/Desktop/install_flash_player_9_linux': Is a directory
chris@chris-desktop:~$ 


Are the icons called something else? Do I need the " " around separated words?
Chris:(

---

### Post by Nepherte on 2008-04-21
For directories you need to add the recursive option to the remove command:
```
rm -r <directory>
```

But as said before: if it's an icon like a hard disk or trash icon
```
gconf-editor
```
go to apps-->nautilus-->desktop and then check or uncheck options there.
__________________

---

### Post by jken146 on 2008-04-21
For the others, put the whole path in "" quotes.

---

### Post by aparigraha on 2008-04-21
/bla/bla/Samsung Unified Driver Configurator

should be 

/bla/bla/Samsung\ Unified\ Driver\ Configurator

as stated above:
rm -r <directory>


the easiest way is absolutely:

gksudo nautilus

after that
right-click and remove the folder you wish

---

### Post by _mOrgoth_ on 2008-04-21
tipe in terminal : sudo nautilus
navigate to: File System(on left under Places), home, your username folder, Desktop and delete what you want to delete..

---

### Post by stchman on 2008-04-21
> **cpeachey said:**
> I cannot delete icons on my desktop because the "owner" is root. How do i change this?
Ubuntu 7.1 (new user!
Chris:frown::frown::frown:

You could try this:

```
sudo chown -R $USER:$USER ~/Desktop
chmod -R 755 ~/Desktop

```

This will change the ownership of all the shortcuts to the user currently logged in and allow you to delete them.

---

### Post by cpeachey on 2008-04-21
Thanks friends...Windows was never this much fun!!:guitar:
Chris

---

### Post by jeffbray on 2008-04-26
Man, that chown command is just what I needed.

I love these forums, hahaha.

Thanks a lot!

---

