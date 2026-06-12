---
title: "Lots of different questions"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-08-10
I have a lot of questions, which I would like to know the answers of, some maybe much simpler then others, but ill just type them down. This will be my first post with questions, coz ive got too many to put into 1 topic, in my opinion atleast.

1. I have amsn installede, and I have made it to start automaticly when I log on my account. But It doesent log in to my account automaticly. Is it possible to do so?

2. I have some files in my garbage bin, which I just cant delete. When I try and delete them it gives me an error saying i do not have permessions to modify its parents folder.

3. Whats the difference in programing and scripting?

4. Is it possible to change the default firefox globe in ubuntu to the real icon? The fox around a globe or what it is :D

5. How do I get tv-out to work in ubuntu? Do I need to download a program?

6. I have downloade som skins for amsn, but how do I get them installed?

7. I have installede Diablo 2 demo through wine, just becouse I wanted to try, now I want to uninstall it. How can I do this?

I think thats enough for now.

Thanks :D

---

### Post by MaximB on 2006-08-10
2. you need to become a root to delete thouse files
from therminal type "sudo nautilus" (if that is the name of your browser).
then fin the .bin directories (you should have at least 2 of them) and delete to content (every user has a .bin).
3.scripting is much more simple then programing , if you know windows/dos - scripting is making a .bat (batch) file.
it includes several commands that you can type seperatly
programing is very hard work - you can't make one like work seperatly from the program you've made (I mean you can't type it in the command line). - you need a program for programing (like c++ and pascal).
4.didn't understand your question , but you can change themes.

---

### Post by Titus A Duxass on 2006-08-10
There is a search function you know!

Most of your queries can be answered by searching.

---

### Post by arjun.shankar on 2006-08-10
> **jincast90 said:**
> 1. I have amsn installede...

No idea.

> **jincast90 said:**
> 2. I have some files in my garbage bin...

The hard way is:

Check your **.Trash-username** directory's permissions.

There is one such file in each mount point. For example if **/home** is a seperate partition, you will find **.Trash-user1**,**.Trash-user2** and so inside **/home**. You can see it's permissions and with the following command in the **/home** directory:

"ls -la"

The first column will have entries like:

drwxr-xr-x (may not be the same)

In the above line:

the 'd' means directory.

the first set of  rwx is read, write, and execute permission for the owner.

the second set of  rwx is read, write, and execute permission for the owner's group members.

the third set of  rwx is read, write, and execute permission for others.

dashes in a position mean that the permission is not granted. Only the owner or root can change these permissions.

Make sure that you have read, write and execute permissions for your trash directory (namely .Trash-username)

If you don't, then you can change it using the chmod command:

**chmod u+w .Trash-username**

here, the "u+w" will give you write permission.

"u-w" will remove it.

similarly, a "g+x" gives execute permissions to the group members, and so on.

The easier way is:

> **MAXDDARK]"sudo nautilus"[/QUOTE]

[QUOTE=jincast90 said:**
> 3. Whats the difference in programing and scripting?

Well, as far as I know, when you write  program, it is compiled into machine language in one go, and converted to machine code. If you make an error in the 20th line, it's rejected. In ce of a script, you write in a hig level language (examples are perl scripts, python scipts, and so on... even bash scripts!), and an "interpreter", understands them line by line (much like an actual interpreter) and executes them. They can't run on their own, like machine code can. This means, that you can run a precompiled C program (the executable that comes out of it), even if you dont have a C compiler. But for a scrit, you need the interpreter each time you run it.

> **jincast90 said:**
> 4. Is it possible to change the default firefox globe in ubuntu to the real icon? The fox around a globe or what it is :D

Yes. Right click the 'Applications' menu and select the 'Edit Menus' option. After that, you'll see yourself how easy it is.

> **jincast90 said:**
> 5. How do I get tv-out to work in ubuntu? Do I need to download a program?

No idea.

> **jincast90 said:**
> 6. I have downloade som skins for amsn, but how do I get them installed?

Ditto.

> **jincast90 said:**
> 7. I have installede Diablo 2 demo through wine, just becouse I wanted to try, now I want to uninstall it. How can I do this?

Try running the uninstaller. I will be there somewhere in your "~/.wine/drive_c" directory. If that doesn't work, you can always delete the installation directrory. Which defaults to a subdirectory of "~/.wine/drive_c"

> **jincast90 said:**
> I think thats enough for now.

Sure!

---

### Post by Beggar Su on 2006-08-10
You can change the firefox (or thunderbird) icons to their original design by following the steps in this thread [Take back the firefox and thunderbird logo]("http://ubuntuforums.org/showthread.php?t=34354")

---

### Post by steve.horsley on 2006-08-10
> **arjun.shankar said:**
> Well, as far as I know, when you write  program, it is compiled into machine language in one go, and converted to machine code. If you make an error in the 20th line, it's rejected. In ce of a script, you write in a hig level language (examples are perl scripts, python scipts, and so on... even bash scripts!), and an "interpreter", understands them line by line (much like an actual interpreter) and executes them. They can't run on their own, like machine code can. This means, that you can run a precompiled C program (the executable that comes out of it), even if you dont have a C compiler. But for a scrit, you need the interpreter each time you run it.

I think that's the common view, but I saw a different idea that I quite agree with: 

That scripting is promarily concerned wit automating what a user would otherwise do manually - launching processes, collecting the results, feeding those results into other processes and so on. Bash is very much aimed at this - its ability to launch subprocesses, pipe processes etc are very much concerned with controlling and supervising other processes. 

Programming on the other hand is more involved with calculations and algorithms within a certain problem, doing one possibly very complex job for the user. C and the like are aimed at this application.

Obviously, almost any programming language can be put to use either as an application or as a utility that automates user actions, and there is lots of overlap, but the idea that a "script" is a description of a series of user actions carries some logic.

---

### Post by Frank Golden on 2006-08-10
> **MAXDDARK said:**
> 2. you need to become a root to delete thouse files
from therminal type "sudo nautilus" 

When opening GUI based programs it is recomended to use gksudo
instead of sudo. "gksudo nautilus" will open your file browser
with full root priveleges for that nautilus session.
Omit the quotation marks. That is if you are using gnome (Ubuntu). If using KDE (Kubuntu) I don't know what the proper command is.

---

### Post by jincast90 on 2006-08-10
> **Frank Golden said:**
> When opening GUI based programs it is recomended to use gksudo
instead of sudo. "gksudo nautilus" will open your file browser
with full root priveleges for that nautilus session.
Omit the quotation marks. That is if you are using gnome (Ubuntu). If using KDE (Kubuntu) I don't know what the proper command is.

Good thing I use gnome then :D

---

### Post by jincast90 on 2006-08-10
Bump

---

### Post by arjun.shankar on 2006-08-11
steve.horsley, you are right too! It depends how one looks at it.

And I noticed a lot af mied characters in my post... keyboard trouble ;)

---

