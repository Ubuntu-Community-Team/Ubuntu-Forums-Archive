---
title: "Trouble installing swiftfox onto xubuntu"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by muggins on 2007-05-23
How do you download the swiftfox installer into your home directory, I can get it on to my desktop but when I type "sh install-swiftfox.sh" into the terminal it  "Can't open install-swiftfox.sh".

---

### Post by Terl on 2007-05-23
Usually you have to put sudo in front of the command.  Give that a try.

---

### Post by Happy_Man on 2007-05-23
Ok, dowload the .tar.bz2 file corresponding to your version to your Desktop. Extract it there, and then open up a terminal (Applications --> Accessories --> Terminal):

```
cd <name of extracted folder>
./install-swiftfox.sh

```

and follow the steps it shows!

---

### Post by muggins on 2007-05-23
Thanks for the replies, however none of them worked. Terminal said - sh: Can't open install-swiftfox.sh

---

### Post by Terl on 2007-05-23
Happy_Man's was right though, but I think it needed sudo.  Did you try:

```
sudo sh ./install-swiftfox.sh
```

You should run this one from the folder the .sh file is in.

[EDIT] cd to folder with file and do ```
ls -l
``` that is a small L

See if the last letter is an x.  If not do ```
chmod o+x ./install-swiftfox.sh
```

Then run the first commands.

---

### Post by Pobega on 2007-05-23
sudo -i
chmod ug+rwx install-swiftfox.sh
sh install-swiftfox.sh

Sounds to me like you have insufficient permissions to execute the program. These commands should work, just make sure you're in the same directory as the install-swiftfox.sh file.

---

### Post by muggins on 2007-05-23
Here is the output from terminal:

helge@helge-desktop:~$ sudo sh install-swiftfox.sh
sh: Can't open install-swiftfox.sh
helge@helge-desktop:~$ sudo sh ./install-swiftfox.sh
Password:
sh: Can't open ./install-swiftfox.sh
helge@helge-desktop:~$ sudo -i
root@helge-desktop:~# chmod ug+rwxinstall-swiftfox.sh
chmod: missing operand after `ug+rwxinstall-swiftfox.sh'
Try `chmod --help' for more information.
root@helge-desktop:~# sh install-swiftfox.sh
sh: Can't open install-swiftfox.sh
root@helge-desktop:~# 

Does this help at all?

---

### Post by muggins on 2007-05-24
Still haven't been able to install swiftfox.

Pobega  	sudo -i
chmod ug+rwx install-swiftfox.sh
sh install-swiftfox.sh

Sounds to me like you have insufficient permissions to execute the program. These commands should work, just make sure you're in the same directory as the install-swiftfox.sh file.

How do I know if I am in the same directory as the install-swiftfox.sh file?

---

### Post by ahmatti on 2007-05-24
Use the swiftfox debian package from the website. You can install it by double clicking it or typing "sudo dpkg -ti swiftfox-xxxx.deb". Or better yet add the swiftfox repos to your sources.list and get automatic updates too. Here: [http://getswiftfox.com/debian.htm](http://getswiftfox.com/debian.htm)

---

### Post by muggins on 2007-05-24
How do I add something to my sources.list? 

Thanks for reply.

---

### Post by ahmatti on 2007-05-24
> **muggins said:**
> How do I add something to my sources.list? 

Thanks for reply.

Open your sources.list in a text edit e.g.

```
$gksu gedit /etc/apt/sources.list 
```

Add the repo you want to a new line in the file, for swiftfox add line:

deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free

Then go to synaptic and search for swiftfox -> install

---

### Post by muggins on 2007-05-24
That worked like a charm, thanks again for your help.

---

