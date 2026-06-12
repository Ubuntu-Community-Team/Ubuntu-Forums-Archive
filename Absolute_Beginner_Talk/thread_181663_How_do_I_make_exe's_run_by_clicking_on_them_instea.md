---
title: "How do I make exe's run by clicking on them instead of through the terminal?"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by n00bWillingToLearn on 2006-05-24
I am setting up Ubuntu for someone else who is not very good with computers and I would like to make it easier for her to run windows programs without having to use the terminal. 
[edit] Using Wine of course.

---

### Post by patrick295767 on 2006-05-24
you could use rox .
  
1/ apt-get -f -y install rox-filer wine
  
2/ then, as user : 
rox &
  
3/ press * key of your keyboard
and type : 
wine "$@"
 
Enjoy Linux !!:KS

---

### Post by mostwanted on 2006-05-24
Right-click on an .exe, properties, open with, add "wine" to the top of the list.

Or just make a launcher for it:

[http://monkeyblog.org/ubuntu/videos/Creating_launcher.gif](http://monkeyblog.org/ubuntu/videos/Creating_launcher.gif)

---

### Post by youthforlinux on 2006-05-24
when i click on a .exe it runs it with wine for me.

---

### Post by Lord Illidan on 2006-05-24
Before you jump the gun, may I ask what kind of windows applications?

---

### Post by youthforlinux on 2006-05-24
iexplorer

---

### Post by n00bWillingToLearn on 2006-05-24
Sorry I wasn't sure about what you meant by some of your instructions and it didn't work. this is what I typed / the output given:

```
 sudo apt-get -f -y install rox-filer wine
Password:
Reading package lists... Done
Building dependency tree... Done
wine is already the newest version.
Suggested packages:
  menu
The following NEW packages will be installed
  rox-filer
0 upgraded, 1 newly installed, 0 to remove and 118 not upgraded.
Need to get 1341kB of archives.
After unpacking 3740kB of additional disk space will be used.
Get: 1 http://us.archive.ubuntu.com dapper/universe rox-filer 1:2.4-1ubuntu1 [1341kB]
Fetched 1341kB in 18s (72.2kB/s)
Selecting previously deselected package rox-filer.
(Reading database ... 76990 files and directories currently installed.)
Unpacking rox-filer (from .../rox-filer_1%3a2.4-1ubuntu1_i386.deb) ...
Setting up rox-filer (2.4-1ubuntu1) ...
***
* Updating MIME database in /usr/share/mime...
Wrote 478 strings at 20 - 27a8
Wrote aliases at 27a8 - 295c
Wrote parents at 295c - 331c
Wrote literal globs at 331c - 3380
Wrote suffix globs at 3380 - 66c8
Wrote full globs at 66c8 - 66ec
Wrote magic at 66ec - bd38
Wrote namespace list at bd38 - bd48
***

 rox &
[1] 5475
** (rox:5476): WARNING **: mkdir(/home/whitney.choice): Permission denied


** (rox:5476): WARNING **: mkdir(/home/whitney.choice): Permission denied


** (rox:5476): WARNING **: mkdir(/home/whitney.choice): Permission denied


** (rox:5476): WARNING **: mkdir(/home/whitney.choice): Permission denied


** (rox:5476): WARNING **: mkdir(/home/whitney.choice): Permission denied


** (rox:5476): WARNING **: mkdir(/home/whitney.choice): Permission denied

*wine "$@"
bash: *wine: command not found
[1]+  Done                    rox
 * wine "$@"
bash: Desktop: command not found
 *
bash: Desktop: command not found

```

---

### Post by mostwanted on 2006-05-24
[QUOTE=n00bWillingToLearn]Sorry I wasn't sure about what you meant by some of your instructions and it didn't work. this is what I typed / the output given:

```
 sudo apt-get -f -y install rox-filer wine
Password:
Reading package lists... Done
Building dependency tree... Done
wine is already the newest version.
Suggested packages:
  menu
The following NEW packages will be installed
  rox-filer
0 upgraded, 1 newly installed, 0 to remove and 118 not upgraded.
Need to get 1341kB of archives.
After unpacking 3740kB of additional disk space will be used.
Get: 1 http://us.archive.ubuntu.com dapper/universe rox-filer 1:2.4-1ubuntu1 [1341kB]
Fetched 1341kB in 18s (72.2kB/s)
Selecting previously deselected package rox-filer.
(Reading database ... 76990 files and directories currently installed.)
Unpacking rox-filer (from .../rox-filer_1%3a2.4-1ubuntu1_i386.deb) ...
Setting up rox-filer (2.4-1ubuntu1) ...
***
* Updating MIME database in /usr/share/mime...
Wrote 478 strings at 20 - 27a8
Wrote aliases at 27a8 - 295c
Wrote parents at 295c - 331c
Wrote literal globs at 331c - 3380
Wrote suffix globs at 3380 - 66c8
Wrote full globs at 66c8 - 66ec
Wrote magic at 66ec - bd38
Wrote namespace list at bd38 - bd48
***

 rox &
[1] 5475
** (rox:5476): WARNING **: mkdir(/home/whitney.choice): Permission denied


** (rox:5476): WARNING **: mkdir(/home/whitney.choice): Permission denied


** (rox:5476): WARNING **: mkdir(/home/whitney.choice): Permission denied


** (rox:5476): WARNING **: mkdir(/home/whitney.choice): Permission denied


** (rox:5476): WARNING **: mkdir(/home/whitney.choice): Permission denied


** (rox:5476): WARNING **: mkdir(/home/whitney.choice): Permission denied

*wine "$@"
bash: *wine: command not found
[1]+  Done                    rox
 * wine "$@"
bash: Desktop: command not found
 *
bash: Desktop: command not found

```[/QUOTE]


Honestly, I have no idea what Patrick is trying to do. It seems overly complicated to me. Just go with what I said. You can make a launcher that launches the command "wine /path/to/ie6" (replace with the real path). I even provided a nice GIF video for it.

Have you installed using this script? It should have made nice clickable icons for you when you used it:

[http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html)

---

### Post by n00bWillingToLearn on 2006-05-24
[QUOTE=mostwanted]Right-click on an .exe, properties, open with, add "wine" to the top of the list.
[/QUOTE]
That workes fine and is probably better than setting all exe's to run automatically in wine. Thank you.

---

### Post by Lord Illidan on 2006-05-24
You don't need rox.

Now that wine is installed, .exes should launch with wine automatically.

---

### Post by n00bWillingToLearn on 2006-05-24
I have decided to just use your solution but since I don't know exactly what I did in the terminal could you just confirm that I didn't break anything?

---

### Post by patrick295767 on 2006-05-24
> **mostwanted]Honestly, I have no idea what Patrick is trying to do. It seems overly complicated to me. Just go with what I said. You can make a launcher that launches the command "wine /path/to/ie6" (replace with the real path).[/QUOTE]
   
My girlfriend found this also complicated, ... :-) 
  if it's too complicated try the way of mostwanted..
  that's why I always recommand kde or gnome desktop : it's made EASY  for starting with Linux !!
  
(  btw, 'Permission denied' looks strange ... with the permissions of your machine said:**
>  ls -la ~/)
  
Hope you'll manage, Greetz

---

### Post by mostwanted on 2006-05-24
[QUOTE=n00bWillingToLearn]That workes fine and is probably better than setting all exe's to run automatically in wine. Thank you.[/QUOTE]

Actually, that is exactly what that method does. The launcher method that I also described would only do it for the single instance.

---

### Post by n00bWillingToLearn on 2006-05-24
[QUOTE=Lord Illidan]You don't need rox.

Now that wine is installed, .exes should launch with wine automatically.[/QUOTE]

I have wine installed and it runs fine from the terminal but exe's are not run in wine by default and I would personaly prefer to explicitly set a program to run in wine as opposed to having any exe run so I am fine with just setting it in the properties.

---

### Post by mostwanted on 2006-05-24
[QUOTE=n00bWillingToLearn]I have wine installed and it runs fine from the terminal but exe's are not run in wine by default and I would personaly prefer to explicitly set a program to run in wine as opposed to having any exe run so I am fine with just setting it in the properties.[/QUOTE]

Please see my previous post.

---

