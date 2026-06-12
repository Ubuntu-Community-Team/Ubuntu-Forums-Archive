---
title: "Messed up a critical file?"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by johnnymo87 on 2006-01-13
I was trying to edit my /etc/sudoers file so that I could get firestarter to run without the root password. I messed up the line I was supposed to add, and saved it. How can I fix it? 

I can't seem to use the sudo command anymore, it says 
[i]>>> sudoers file: syntax error, line 23 <<<
sudo: parse error in /etc/sudoers near line 23[/i]

I tried to switch into root and open the file with gedit and nano, but both times it denied me permission.

Help?

---

### Post by AMD64_N_Linux on 2006-01-13
[quote=johnnymo87]I was trying to edit my /etc/sudoers file so that I could get firestarter to run without the root password. I messed up the line I was supposed to add, and saved it. How can I fix it? 

I can't seem to use the sudo command anymore, it says 
[I]>>> sudoers file: syntax error, line 23 <<<
sudo: parse error in /etc/sudoers near line 23[/I]

I tried to switch into root and open the file with gedit and nano, but both times it denied me permission.

Help?[/quote]

reboot.

when the grub menu comes up boot into the " Recovery mode" . Each kernel you have installed has a line for general purpose use, (regular  mode) and the 2nd line is a recovery mode.

I could be wrong, but I believe that recovery mode boots you into ROOT automatically, so that you can fix it. 

At least that is how I have managed to fix my MANY screwups.

Hope this helped. 

Anyone else ?

---

### Post by benplaut on 2006-01-13
If that doesn't work, it should be possible to boot into the LiveCD and remove the offending line... permissions should work out

---

### Post by johnnymo87 on 2006-01-13
Thanks, the recovery mode worked for me. :)

To avoid this problem in the future, I can back it up like this ...
```

sudo cp /etc/sudoers /etc/sudoers_backup

```
and restore it like this.
```

sudo cp /etc/sudoers_backup /etc/sudoers

```
Am I right?

---

### Post by AMD64_N_Linux on 2006-01-13
Looks right to me, and a good idea to backup everything. 


Somewhere ( ? ) there is a setting in the text editor to automatically back up files when you edit them.

Anyone ?

---

### Post by towsonu2003 on 2006-01-13
gedit will backup files (if you didnot change preference) such as: 

filename > filename~

the bad thing is, everytime you hit "save", it overwrites the previous backup (learnt it the bad way)... so if you add a line and hit save, than see a mistake, correct it and than hit save again, your backup will be the already tweaked + incorrect file... 

PS. Even when I recover a backup, I backup the incorrect / corrupt file just in case...

---

