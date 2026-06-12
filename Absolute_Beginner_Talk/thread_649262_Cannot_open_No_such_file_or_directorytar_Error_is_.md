---
title: "Cannot open: No such file or directory
tar: Error is not recoverable: exiting now"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by goldencj on 2007-12-24
tlc@tlc-desktop:~$ tar -xjf xmltv-0.5.50.tar.bz2
tar: xmltv-0.5.50.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
tlc@tlc-desktop:~$

---

### Post by Afkpuz on 2007-12-24
First of all, make sure that you are in the same directory as the tar ball you're trying to extract.  By default, the terminal starts in your home folder.  If you saved the tar ball to your desktop, you can change directories to the desktop with
 ```
cd Desktop
```
Then try your code.  Also, you want to use the "-jxvf" option.  so it would look like
```
tar -jxvf xmltv-0.5.50.tar.bz2
```



Alternately, you can extract the tar ball graphically.  Right click on the archive and click "extract".

---

### Post by goldencj on 2007-12-25
Thanks that worked!

---

### Post by trugreg on 2007-12-25
This helped me with a simular problem - NOW what is command to get back to my main directory

---

### Post by unarmedninja on 2007-12-25
just type > cd or > cd ~/ 

if that doesnt work you can type the full path > cd /home/(username)

---

### Post by trugreg on 2007-12-25
tried all those still in desk top

greg@greg-desktop:~$ cd /home/greg
greg@greg-desktop:~$ cd
greg@greg-desktop:~$ cd ~/
greg@greg-desktop:~$ cd /home/greg
greg@greg-desktop:~$

---

### Post by unarmedninja on 2007-12-25
which directory are you trying to get to? your actually at the home directory right now.

greg@greg-desktop:~$

greg                -> username
@greg-desktop -> computer name
~                    -> current directory (~ = home directory )
$                     -> command prompt

---

### Post by zvacet on 2007-12-25
You can be in any directory or subdirectory and just type** cd** and you will be back in your** home directory**.

---

### Post by oldos2er on 2007-12-25
> **trugreg said:**
> tried all those still in desk top

greg@greg-desktop:~$ cd /home/greg
greg@greg-desktop:~$ cd
greg@greg-desktop:~$ cd ~/
greg@greg-desktop:~$ cd /home/greg
greg@greg-desktop:~$

 You're in your home directory. For some reason, Ubuntu calls "home" "user@user-desktop." To get to your actual desktop, type cd Desktop (your actual desktop directory uses a capital D).

---

### Post by goldencj on 2007-12-26
Thanks All, great info

---

### Post by satishdounde on 2007-12-31
satish@ubuntu:~$  satish 

    No such file or directorytar

---

