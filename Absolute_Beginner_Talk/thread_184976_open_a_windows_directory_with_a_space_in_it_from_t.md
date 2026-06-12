---
title: "open a windows directory with a space in it from terminal"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by joshrobinson on 2006-05-30
i need to copy 2 folders off a hard-drive onto another via terminal, not using xwindows

the folders are Old stuff and Real Estate.. the problem is i cant get to it with cd Old stuff, becuase the space is throwing it off.. how can i copy the folders, or get into them to copy them?

i tried cp *.* /media/ex but it wouldnt copy the folders, just what was in the directory below them

---

### Post by catlett on 2006-05-30
I was in this thread before .[http://www.ubuntuforums.org/showthread.php?p=905052#post905052](http://www.ubuntuforums.org/showthread.php?p=905052#post905052)   He said to use cp -r. The  -r being recursive. I don't know if you already know that but I thought I would mention it.
P.S. Scroll up when you hit the link. It starts with my response, which you don't want:-D

---

### Post by jimrz on 2006-05-30
[QUOTE=joshrobinson]i need to copy 2 folders off a hard-drive onto another via terminal, not using xwindows

the folders are Old stuff and Real Estate.. the problem is i cant get to it with cd Old stuff, becuase the space is throwing it off.. how can i copy the folders, or get into them to copy them?

i tried cp *.* /media/ex but it wouldnt copy the folders, just what was in the directory below them[/QUOTE]

Try using cp "Old stuff" and cp "Real Estate". The quote marks should allow it to work.

---

### Post by joshrobinson on 2006-05-30
[QUOTE=catlett]I was in this thread before .[http://www.ubuntuforums.org/showthread.php?p=905052#post905052](http://www.ubuntuforums.org/showthread.php?p=905052#post905052)   He said to use cp -r. The  -r being recursive. I don't know if you already know that but I thought I would mention it.
P.S. Scroll up when you hit the link. It starts with my response, which you don't want:-D[/QUOTE]

ok thanks, i did cp -r /media/sda5 /media/ex

how would you enter one of those folders though? since it has a space in it.. dont you have to do something along the lines of Old~1.. at least thats how dos was back in the day
program files was always something like Progra~1

---

### Post by joshrobinson on 2006-05-30
[QUOTE=jimrz]Try using cp "Old stuff" and cp "Real Estate". The quote marks should allow it to work.[/QUOTE]

ahh there we go, that answerd my how to get into that folder question.. thanks both of you, catlett's command let me copy them

thanks jimrz also for letting me know how to get into the folders

---

### Post by user1397 on 2006-05-30
just so you know, in the future you should name folders "folder_foo"  so with an underscore or a dash or something, just anything but a space.  this saves a lot of trouble (i've been there before, trust me :D

---

### Post by joshrobinson on 2006-05-30
[QUOTE=erik1397]just so you know, in the future you should name folders "folder_foo"  so with an underscore or a dash or something, just anything but a space.  this saves a lot of trouble (i've been there before, trust me :D[/QUOTE]

well these folders came from a windows machine, and then i partitioned the drive, and want to format the whole drive now.. but i had to get that data off first.. so they are old folders

my dapper broke due to some updates causing hell and xwindows wont work right, so i wanted to mount and copy them to my external hard-drive so i can format the entire drive.. its got alot of partitions on it

---

### Post by Randomskk on 2006-05-30
Doing this is easy:
cd folder\ name
the backslash escapes the space.

edit: also, if you just type fol then press tab, BASH will auto-complete the name, and adds in the backslash.

---

### Post by joshrobinson on 2006-05-30
[QUOTE=Randomskk]Doing this is easy:
cd folder\ name
the backslash escapes the space.

edit: also, if you just type fol then press tab, BASH will auto-complete the name, and adds in the backslash.[/QUOTE]

ahh i was so close then.. i tried Old\stuff not Old\ stuff

---

### Post by Randomskk on 2006-05-30
It took me a while to figure that too, eventually I only got it because of the auto-completion thing :P
If you don't already use auto complete, I highly reconmend it - it freaking rocks!
Just start typing the name of a file or folder and press tab. If nothing happens there's another similar folder, press tab twice for all possibilities.

---

### Post by joshrobinson on 2006-05-30
[QUOTE=Randomskk]It took me a while to figure that too, eventually I only got it because of the auto-completion thing :P
If you don't already use auto complete, I highly reconmend it - it freaking rocks!
Just start typing the name of a file or folder and press tab. If nothing happens there's another similar folder, press tab twice for all possibilities.[/QUOTE]

nice i just tried it out :-p the name of the folder was Type name of new folder
and it added in a bunch of slashes and went right to it.. nice tip!

---

### Post by catlett on 2006-05-30
Just a tip about folder paths. If I'm unsure of a path. I browse to it in Nautilus, then I drag the folder  into the terminal and the terminal types in the path of the folder. So I enter cd then put a space, drag over the folder, drop it in the terminal line, the path is written out in text and then I hit enter to get there. Just a tip.

---

### Post by joshrobinson on 2006-05-30
[QUOTE=catlett]Just a tip about folder paths. If I'm unsure of a path. I browse to it in Nautilus, then I drag the folder  into the terminal and the terminal types in the path of the folder. So I enter cd then put a space, drag over the folder, drop it in the terminal line, the path is written out in text and then I hit enter to get there. Just a tip.[/QUOTE]

thats a nice tip too.. didnt know that one either.. woulda came in handy if xwindow / gnome worked at the time :-/

---

