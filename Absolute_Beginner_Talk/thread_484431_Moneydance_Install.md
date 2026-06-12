---
title: "Moneydance Install"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by RaidV92C on 2007-06-25
Hi Everyone,

My first post and of course it seems to have been covered ad nauseum.  Sorry.  I have downloaded Moneydance (both with and without Java).  Firefox put it on the desktop, but I have moved to home/ken.  I tried to move it to usr but said I don't have permission.  Don't know why but that's what it said.  When I tried to install from desktop I get message that archive manager says 

Could not open "moneydance_linux_x86.sh"

Archive type not supported.

I am a complete Linux nube, but am very proficient with Windows and even back to DOS.  I have read the posts regarding others problems installing this program, but frankly don't follow the suggestions.  My impression is that this file type is similar to a zip file or other and I don't have the right program to launch it.  Is that correct?  Did I move the archive files to the correct place or is there the equivalent of "Program Filess" from Windows?  Can I get some step by step help in installing this?  I learned about the "Terminal" window last night, but not sure how to change directories etc...

Thanks in advance for your help.

RaidV92C (Ken)

---

### Post by cogadh on 2007-06-25
A .sh file is a script file, not an archive. Think of it like a batch file in Windows. To run it, do this in a terminal:
```
sh moneydance_linux_x86.sh
```
Not sure if you should sudo it, if the script complains it can't access certain directories/files, then do this:
```
sudo sh moneydance_linux_x86.sh
```

BTW- You don't have access to /usr because only root or a "sudoer" has access to it.

---

### Post by mikehvorup on 2007-06-25
from the terminal cd to the location you have the file then:

chmod 777 moneydance_linux_x86.sh

then

sh moneydance_linux_x86.sh

---

### Post by RaidV92C on 2007-06-25
Wow, too easy.  Thanks a million.  It is at least trying to work.  Now I get to choose the location.  I tried leaving the default location which is usr/local, but it says I don't have "write permission".  If I am the one who installed the operating system, I am the only one who logs in why don't I have permission?  How can I change this?

---

### Post by cogadh on 2007-06-25
You don't, it's a safety feature built in to protect the OS from user accidents. Using the "sudo" command will give you access to the necessary files/directories temporarily. The command "sudo" is short for "**s**uper**u**ser **do**".

---

### Post by RaidV92C on 2007-06-25
Thanks for your help, cogadh .  Got it working right away.

---

