---
title: "Amsn"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by TJB on 2006-03-05
How do I install amsn? I'm new to ubuntu and its the first time to have a linux but i know a lot about windows.

---

### Post by NoWhereMan on 2006-03-05
search the forum :D

---

### Post by Mustard on 2006-03-05
[QUOTE=TJB]How do I install amsn? I'm new to ubuntu and its the first time to have a linux but i know a lot about windows.[/QUOTE]

Firstly you need to enable the 'Universe' repository, as that is where the amsn package is found.  While you are doing that, you might as well enable the 'Multiverse' repository as well.

Please read over this link for instructions....

[http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse](http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse)

---

### Post by s6dalane on 2006-03-05
You can download the .deb file from aMSN's [homepage]("http://amsn.sourceforge.net/index.php") and install it with that.
After downloading the file, simply type in terminal:
> sudo dpkg -i file_name.deb

---

### Post by TJB on 2006-03-05
[QUOTE=s6dalane]You can download the .deb file from aMSN's [homepage]("http://amsn.sourceforge.net/index.php") and install it with that.
After downloading the file, simply type in terminal:[/QUOTE]
I downloaded amsn and I chose amsn-0.95-1.linux-installer.x86_64.bin . is that the right one?:confused: 

I copyed and pasted it and typed it but got this error:

dpkg: error processing file_name.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 file_name.deb

---

### Post by altonbr on 2006-03-05
Oh man... when it says 'file_name' you replace that with the actual filename... so it'd be something like:

sudo dpkg -i amsn-0.95-1.linux-installer.x86_64.deb

and you download the wrong file... download the .deb file

---

### Post by patrick295767 on 2006-03-05
THis is good nfo to install it : [http://www.ubuntuforums.org/showthread.php?t=133777&highlight=amsn](http://www.ubuntuforums.org/showthread.php?t=133777&highlight=amsn)

Greetz

pat

---

### Post by TrendyDark on 2006-03-05
automatix :)

---

### Post by IYY on 2006-03-05
It's in the Universe repositories. Just get it using Synaptic.

---

