---
title: "Untar Question"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Daergeth on 2007-02-05
I just got a game from Tux Games in the mail yesterday (NWN and Doom 3), got all excited and put the tuxgames installer cd in, I do like the instructions suggest and "source ./setup" the term pops up and says that it cannot find a lib file and to manually untar all the files to read the readme. Well, Im a total newb, and the tar command is still confusing to me, I'm not sure which letters to use, could I get some help here?

---

### Post by Ryan450 on 2007-02-05
tar -xvzf <filename>

that'll untar it for ya and tell what its doing :).

---

### Post by deadgobby on 2007-02-05
A simple way is to left click on the tar file and scroll down to extract here. It will make new new folder after the tar is unpacked and you can read the READ ME file.
Gobby

---

### Post by Daergeth on 2007-02-05
Ah, thanks guys appreciate the help. :) Im sure Ill be having more questions later when I get home and unpack everything. Stupid games better work! ):P

---

### Post by deadgobby on 2007-02-05
Some times all you need to is click on the blue diamond shape icon. Like if it has Chaos Caverns for sample. When you unpack the tar and open up the folder you see Chaos Caverns with a blue diamond shape icon. Or like Action Cude. After you unpack the tar. You'll see actioncube.sh and you click on that and the program opens right up. Yet some games after getting it build from source. All you do is type the name in the terminal. 
Gobby

---

### Post by Daergeth on 2007-02-05
Ok here is my problem guys, and if this is totally obvious, then I do apologize :)

My NWN install CD from Tux Games tells me to source ./setup. I do that and I get this...

> 
xfce@xfce:/media/cdrom1$ source ./setup
xfce@xfce:/media$ Initialising files
Extracting archive from CD
Uncompressing archive
If you do not see a popup window, then please simply 
untar the files in the install directory and read the 
appropriate README files
/tmp/tuxsetup: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory

Although, I do have the libX11.so.6 file, any suggestions? :(

---

### Post by bruenig on 2007-02-05
perhaps try
```
sudo apt-get install libx11-6 libx11-6-dbg
```
And then try again.

---

