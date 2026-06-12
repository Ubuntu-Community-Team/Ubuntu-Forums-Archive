---
title: "need help on copying folder &amp; help on cd command"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by s1baker on 2006-11-20
I am using Ubuntu 6.06


 I am trying to copy a folder from the desktop to a system 
folder (  /etc/init.d  ) by draging it from the desktop to 
the folder opened in  the file browser, but I get the error
message "Error while copying to "/etc/init.d" you do not have permission to write to this folder." I have opened a terminal and entered the command sudo -i with my password but still get this message. How can I copy files to the system folders and is there a way to turn off the permissions on the computer as I am the only one that uses it ?

 Also, I have a question about moving around the file structure 
using commands while in the terminal. In DOS, one could type CD..
and they would be taken back up 1 level in the directory structure. Is there a command in Linux to allow the user to back up 1 level in the directory structure instead of going all the back to the root using  "CD /"    ?

Thanks
s1baker

---

### Post by Aberrix on 2006-11-20
```
sudo cp /home/user/folder /target/folder
```

---

### Post by Henry Rayker on 2006-11-20
"cd .." will take you up one level in the structure. My guess is perhaps you weren't using the space?

---

### Post by i8bugs on 2006-12-03
> **Aberrix said:**
> ```
sudo cp /home/user/folder /target/folder
```

root@i8bugs-desktop:/home/i8bugs# cp /mnt/cdrom/Quake3/baseq3/* /usr/local/games/quake3/baseq3
cp: cannot stat `/mnt/cdrom/Quake3/baseq3/*': **No such file or directory**
root@i8bugs-desktop:/home/i8bugs# 

Why can't terminal see my CD ROM when the file manager can??
bugs

---

### Post by Mimsy on 2006-12-03
> gksudo nautilus

Type that in a terminal, and it opens Nautilus (the Gnome file manager) in root mode. That lets you drag and drop files with root privileges. I copy things that way when I'm in a hurry. :)

/Mimsy

---

