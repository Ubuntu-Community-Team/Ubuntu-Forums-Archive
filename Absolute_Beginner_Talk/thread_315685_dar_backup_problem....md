---
title: "dar backup: problem..."
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by fantasmino on 2006-12-09
Hi,
First af all sorry for my English, I'm italian and I'm noob... :-D 
I wrote this thread in the italian forum, too, but no answer...
So I try here...

I would like to backup my ubuntu system and my home with dar. I found this good *how to*:
[http://gradha.sdf-eu.org/textos/dar-differential-backup-mini-howto.en.html](http://gradha.sdf-eu.org/textos/dar-differential-backup-mini-howto.en.html)
(I use the italian version, of course, well translated...)
but I encounter a problem with the parameter -R
When I type my string:
```
sudo dar -m 256 -y -s 4300M -D -R /home/fantasmino 
-c /media/Linux/backup/backup_home_`date -I` -Z "*.gz" -Z "*.bz2" 
-Z "*.zip" -Z "*.png" -Z "*.jpg" -Z "*.jpeg" -Z "*.rar"
```
it return to me this message:
```
Parse error on command line (or included files): Cannot add an absolute path
```
I can backup everything with this string using another path (for example -R /home/fantasmino/.mozilla-thunderbird) everything works fine, but I can't use the home directory... why?:confused: 
In the *How To* he use this directory...

Also I can't use "cd" command for the home directory...:confused: 
this is the result using cd for the home:
```
fantasmino@fantasubunt:~$ cd /home/fantasmino
fantasmino@fantasubunt:~$ 
```
this is the result using another directory:
```
fantasmino@fantasubunt:~$ cd /home/fantasmino/Desktop
fantasmino@fantasubunt:~/Desktop$ 
```
Is this normal?

---

### Post by NESFreak on 2006-12-09
cant help you tith dar wit i can with cd

> **fantasmino said:**
> Hi,
Also I can't use "cd" command for the home directory...:confused: 
this is the result using cd for the home:
```
fantasmino@fantasubunt:~$ cd /home/fantasmino
fantasmino@fantasubunt:~$ 
```
this is the result using another directory:
```
fantasmino@fantasubunt:~$ cd /home/fantasmino/Desktop
fantasmino@fantasubunt:~/Desktop$ 
```
Is this normal?

see the small ~ before the $. ~ means /home/<current users homedir>
so for you ~ means /home/fantasmino
and ~/Desktop means /home/fantasmino/Desktop

you can even use ~ in your commands
for instance ```
cd ~/Desktop
``` goes to your desktop dir/

NESFreak

---

### Post by fantasmino on 2006-12-09
Great!
Thanks Nes, very clear!:mrgreen: 
1 problem is resolved.

---

### Post by fantasmino on 2006-12-10
Anyone can help me?
If I remove from my string (because I'm already in my home directory):
```
-R /home/fantasmino
```
the return message is the same:
```
Parse error on command line (or included files): Cannot add an absolute path
```

Can't I backup all my home folder?:confused: 
Any ideas?

---

