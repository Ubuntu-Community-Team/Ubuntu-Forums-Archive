---
title: "Need to write files to a folder and I have no permissions"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by jpangamarca on 2007-10-28
Hi, I am relatively new to Linux and Ubuntu, I have this problem and I would love if someone can help me.

I need to write files to a folder in a FAT32 partition. When I try to save documents from any program to that folder, I cannot do it. For example, with gedit I get this message:

*"Can't save the file: /media/hda5/Documentos/Juan Pablo/directions.txt. You don't have the necessary permissions to save the file. Check that the path has been correctly typed and try again."*

I can't copy files to that folder either.

When I go to the folder properties, in the permissions tab it says: Owner: root -- You are not the owner, you can't change those permissions. How can I change permissions so I can write files to that folder?

I tried this too, but did not work::

[FONT="Courier New"]juanpablo@fmg-m001:~$ sudo chmod 777 /media/hda5/Documentos/Juan Pablo/
chmod: can't access `/media/hda5/Documentos/Juan': The file or folder doesn't exist.
chmod: no se puede acceder a `Pablo/': The file or folder doesn't exis[/FONT]t..

I think this last thing happens because there is a blank space in the folder name, but I would prefer not to rename that folder: I use it in Windows too.

Any help is greatly appreciated. :)

---

### Post by akiratheoni on 2007-10-28
Try putting quotation marks around the address, so it would look like this:

sudo chmod 777 "/media/hda5/Documentos/Juan Pablo/"

---

### Post by Billy_McBong on 2007-10-28
[COLOR="Blue"]```
sudo nautilus "/media/hda5/Documentos/Juan Pablo/"
```
that will give you nautilus in that folder with root permissions

or you could change the permissions of it
```
 sudo chmod 777 "/media/hda5/Documentos/Juan Pablo/"
```
[/COLOR]

---

### Post by jpangamarca on 2007-10-28
Thanks for the quick reply. That worked for that particular folder, but not for the subfolders. It'd be great to have permissions for all the subfolders too, any ideas about how can I do that? :)

---

### Post by akiratheoni on 2007-10-28
You could try:

sudo chmod -r 777 "/media/hda5/Documentos/Juan Pablo/"

---

### Post by jpangamarca on 2007-10-28
mmm, I get this:

juanpablo@fmg-m001:~$ sudo chmod -r 777 "/media/hda5/Documentos/Juan Pablo/"
chmod: can't access `777': The file or folder doesn't exist.

Sorry I'm so newbie... :P

---

### Post by akiratheoni on 2007-10-28
Hm. 

Well, seeing as I'm not very experienced with Bash (only a little) I guess I did something wrong there. Sorry. I don't know what else. :(

Nevermind, use a capital R instead, so it will look like

sudo chmod -R 777 "/media/hda5/Documentos/Juan Pablo/"

---

### Post by jpangamarca on 2007-10-29
Thanks akiratheoni, it seems like it worked with the capital R. I hope I don't have any more problems with it. :D

---

