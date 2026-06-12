---
title: "Cant empty deleted items folder"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Troca on 2008-04-18
Hi i installed Kiba-Dock some days ago. Couldnt customise it the way i wanted to desided to remove it so i kinda followed the instructions i found here 

[http://ubuntuforums.org/showthread.php?t=545529](http://ubuntuforums.org/showthread.php?t=545529)

i first typed in console mode 

then i vent to my home folder, click ctrl+h (shows hidden files) and delete the kiba-dock folder.

didnt read the entire thing i then noticed that i was supose to use console cuz i used console to install it quickly reinstalled it again with the same method i did the first time. now i have a Kiba-Dock folder in my deleted items folder that i cant empty. what should i do ?

this is the error i get [http://www.mediahump.com/image/83273/](http://www.mediahump.com/image/83273/)

thanks for reading / troca

---

### Post by Oldsoldier2003 on 2008-04-18
```
gksudo nautilus
```

then you can delete the files. like normal from within nautilus

---

### Post by sisco311 on 2008-04-18
```
sudo rm -fr ~/.Trash/*
```or
```
gksu nautilus
```to run nautilus with root-level privileges and delete the directory from /home/<your_username>/.Trash

The Trash in Hardy is in ~/.local/share/Trash/files/
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Troca on 2008-04-18
when i type gksu nautilus the trashbin is empty
and the sudo rm -fr ~/.Trash/* dosent do anything

any outher ideas ?

---

### Post by Danikar on 2008-04-18
Sounds like it is empty.

---

### Post by Troca on 2008-04-18
i dont think it is check this screenshoot 

[http://www.mediahump.com/image/83275/](http://www.mediahump.com/image/83275/)

---

### Post by Troca on 2008-04-19
still need some help with this :(

---

### Post by Rocket2DMn on 2008-04-19
Try
```
sudo rm -rf ~/.Trash/kiba-dock/
```
Be careful with the rm command, it is very powerful and if executed incorrectly, can cause irreparable damage to your system.  Be sure to use it exactly as I showed.

---

### Post by TeoBigusGeekus on 2008-04-19
If you are using Hardy Heron, navigate to folder

/home/yourusername/.local/share/Trash/files

and delete it from there.

---

### Post by Troca on 2008-04-23
Thanks TeoBigusGeekus that did the trick

---

