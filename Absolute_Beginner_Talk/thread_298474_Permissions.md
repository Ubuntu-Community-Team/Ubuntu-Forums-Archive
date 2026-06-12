---
title: "Permissions"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2006-11-12
I am trying to move a theme to a folder and am getting the following error:  You do not have permissions to write to this folder.  How do I give my self permissions so I can copy this file over.

---

### Post by LLRNR on 2006-11-12
Hi there!

How exactly did you get this error? By trying "mv /path/to/source /path/to/destination" ? If you don't use "sudo" before the move/copy command and you're trying to write to a location which only has root permissions, then you'll be prompted with this kind of messages.

So try a "sudo" before the command you give. BTW I can't figure out how to do this through the drag-n-drop method (using Nautilus or Konqueror), but I tell ya - I think it's even faster through the command line. :-D 

HTH,

LLRNR

---

### Post by gentlemanmasher on 2006-11-12
sudo mv/home/caippers/Desktop/aero/usr/share/apps/kdm/themes is what i tried and it give me command not found.  What is wrong in this?

---

### Post by LLRNR on 2006-11-12
You have to pun in a SPACE between the command (in this case **mv**) and the path, and also you have to put a space between the source path and the destination path.

For example, if I want to move a file called xyz from my desktop to a folder called let's say "Personal" right under root (/), i'd then issue
```
mv ~/Desktop/xyz /Personal
```
Remember to use sudo if you get an error regarding permissions.

Note : ~ is equivalent to /home/MyUserName ... it's just a lot easier to type in, and also kind of failsafe :)

LLRNR

EDIT : Sorry I forgot to tell you, Unix-based systems ARE case-sensitive.

---

### Post by gentlemanmasher on 2006-11-12
ok so mine is a folder named aero that is in my home director.  So I would put mv ~/aero and I want to move it to /usr/share/apps/kdm/themes. so my command in the terminal should be like this 
**sudo mv ~/aero usr/share/apps/kdm/themes**

but I get no such file or directory.  I see the folder under my home.  What is wrong with my entry?

---

### Post by professor_chaos on 2006-11-12
> **gentlemanmasher said:**
> ok so mine is a folder named aero that is in my home director.  So I would put mv ~/aero and I want to move it to /usr/share/apps/kdm/themes. so my command in the terminal should be like this 
**sudo mv ~/aero usr/share/apps/kdm/themes**

but I get no such file or directory.  I see the folder under my home.  What is wrong with my entry?

Two problems with your command.
1. you need a foward slash before the "usr"  ie /usr/share/apps/kdm/themes
2. the command your issuing will infact result in the removal of the folder "themes" at /usr/share/apps/kdm/themes    If you want the folder ~/aero to exist inside the folder "themes" then you need to add a foward slash to the end of themes. ie ```
sudo mv ~/aero /usr/share/apps/kdm/themes/
```

---

### Post by gentlemanmasher on 2006-11-12
Thanks I appreciate your help and patience.

---

### Post by LLRNR on 2006-11-12
Hey it's ok! You're on the right way. I think [this](http://ubuntuforums.org/showthread.php?t=298469) thread can help you, and also if you want to know more about what a command does, you can in short: **command --help | more** or **man command** (and in either case, simply press '**q**' to exit (quit) the manual pages.

Good luck !

LLRNR

---

### Post by bobromeo on 2006-11-14
Tip: the permissions thing starts with downloading stuff to a directory you don't have permissions to.
So download (or move) to /tmp 
(save the file name in the paste buffer)
Then cd to the dir that you want your file to go to.
Then enter
mv /tmp/file.ext . {. means here}
if you get permission errors then get the command back and precede it by sudo ;)

---

