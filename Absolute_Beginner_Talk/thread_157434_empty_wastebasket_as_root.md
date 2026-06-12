---
title: "empty wastebasket as root"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by joshrobinson on 2006-04-09
hey i have some files in my wastebasket that have root only permissions on them, and i cant delete them from the wastebasket.. how can i empty it with root permissions?

i switched to root user but i guess thats the root's wastebasket and its not shared through the users

i tried changing the permissions on the files that wont leave the wastebasket but i cant change permissions on them either

can i login as root and find the wastebasket on the hard-drive?
or can i dump it by the terminal with a certain command?

---

### Post by gazj on 2006-04-09
Yeah this happens quite frequently to me aswell, there is a quick fix in terminal though

```
 cd .Trash
sudo rm -Rv *
```

Hope this helps

---

### Post by Mustard on 2006-04-09
I always hesitate to give instructions that include rm commands, because they are so permanent and mistakes in syntax can be disasterous.  Please be careful with what you are typing in and think twice before hitting the enter key.

I would do it this way...

```
sudo rm -iv ~/.Trash/*
#I've included the -i option for interactivity
#and the -v option for verbose output (it tells you what its doing)

#I'm adding this command below after the fact, but it might help someone in the future
#this version below will delete all folders and files in those folders as well.

sudo rm -Riv ~/.Trash/*

#the -R option is a recursive option that tells rm to
#delete all files and folders underneath the current directory as well
```

---

### Post by joshrobinson on 2006-04-09
[QUOTE=gazj]Yeah this happens quite frequently to me aswell, there is a quick fix in terminal though

```
 cd .Trash
sudo rm -Rv *
```

Hope this helps[/QUOTE]


its still there :-/ the folder name is Recycled

what does the -Rv * mean after the remove command>

so i want sudo rm -Rv Recycled?

---

### Post by joshrobinson on 2006-04-09
ok weird thing now.. in terminal when i do ls it doesnt bring back the directory that cant be deleted.. but when i open the wastebasket it's clearly in there

any ideas?

---

### Post by Mustard on 2006-04-09
[QUOTE=joshrobinson]ok weird thing now.. in terminal when i do ls it doesnt bring back the directory that cant be deleted.. but when i open the wastebasket it's clearly in there

any ideas?[/QUOTE]

Try ctrl + r to refresh the wastebasket view?

---

### Post by joshrobinson on 2006-04-09
[QUOTE=Mustard]Try ctrl + r to refresh the wastebasket view?[/QUOTE]

yeah i did that a few times.. i finally found out what was happening

instead of moving the files to my trash folder, it hid the files on my vfat usb drive in a trash folder there(instead of the one in my home directory)..
so i had to delete them from that drive instead of the actual trash folder

but the commands worked right thanks!

now it just thinks 2 things are in my wastebasket when i mouse-over it. open it and there is nothing in it.. i hope a reboot will take care of that

---

### Post by Mustard on 2006-04-09
[QUOTE=joshrobinson]its still there :-/ the folder name is Recycled

what does the -Rv * mean after the remove command>

so i want sudo rm -Rv Recycled?[/QUOTE]

-R is the recursive option for deleting folders and files that occure beneath the current directory structure

the -v option is the verbose output, so rm tells you what it is doing.

the * is a wildcard argument.  On its own it means **any** file/folder

Basically the way the command is structured that you executed its saying rm any files and folders in this current working directory and every directory that exists below this one.  So it's quite a destructive version of the command. :)

You can type this command to see the manual on rm

```
man rm
```

Hit the 'q' key to exit the manual.

---

### Post by joshrobinson on 2006-04-09
[QUOTE=Mustard]-R is the recursive option for deleting folders and files that occure beneath the current directory structure

the -v option is the verbose output, so rm tells you what it is doing.

the * is a wildcard argument.  On its own it means **any** file/folder

Basically the way the command is structured that you executed its saying rm any files and folders in this current working directory and every directory that exists below this one.  So it's quite a destructive version of the command. :)

You can type this command to see the manual on rm

```
man rm
```

Hit the 'q' key to exit the manual.[/QUOTE]

so its just like del *.* in dos?
but the verbose gives you a listing of whats getting deleted?

---

### Post by Mustard on 2006-04-09
[QUOTE=joshrobinson]so its just like del *.* in dos?
but the verbose gives you a listing of whats getting deleted?[/QUOTE]

Yes, that's basically it. :)

If you add the -i option it will ask you whether you want to delete each file as it executes.  For a large number of files this could be tedious, but its definitely a safer option.  Deletion is permanent and non-recoverable.  It's possible to create an 'alias' for the rm command in the bash shell (command line), which will allow all rm commands to be executed with the -i option, to avoid really disasterous errors in syntax leading to system destruction.

---

### Post by dcstar on 2006-04-09
[QUOTE=joshrobinson]hey i have some files in my wastebasket that have root only permissions on them, and i cant delete them from the wastebasket.. how can i empty it with root permissions?
.......[/QUOTE]
```
gksudo "nautilus --browser %U"
```
Then you have a Nautilus browser with root permissions.

---

### Post by dnccnd on 2006-04-14
[QUOTE=Mustard]I always hesitate to give instructions that include rm commands, because they are so permanent and mistakes in syntax can be disasterous.  Please be careful with what you are typing in and think twice before hitting the enter key.

I would do it this way...

```
sudo rm -iv ~/.Trash/*
#I've included the -i option for interactivity
#and the -v option for verbose output (it tells you what its doing)

#I'm adding this command below after the fact, but it might help someone in the future
#this version below will delete all folders and files in those folders as well.

sudo rm -Riv ~/.Trash/*

#the -R option is a recursive option that tells rm to
#delete all files and folders underneath the current directory as well
```[/QUOTE]
I have used the same command:

sudo rm -Riv ~/.Trash/*

and it worked perfectly! thanks!

The first command didn't work (sudo rm -iv ~/.Trash/*)

I have a related problem though. In my File Browser on the left, just below the icons of Home, Desktop, etc., I can still see a folder that I deleted a long time ago. The icon is like a blue dot with a yallow question mark inside. If I try to open it I get this message:

Couldn't find "/home/mauro/.Trash/Music"

Music is the name of the folder that I deleted from my desktop.

Do you know how I can remove this as well?

Thank you in advance...

---

### Post by Mustard on 2006-04-14
[QUOTE=dnccnd]I have used the same command:

sudo rm -Riv ~/.Trash/*

and it worked perfectly! thanks!

The first command didn't work (sudo rm -iv ~/.Trash/*)

I have a related problem though. In my File Browser on the left, just below the icons of Home, Desktop, etc., I can still see a folder that I deleted a long time ago. The icon is like a blue dot with a yallow question mark inside. If I try to open it I get this message:

Couldn't find "/home/mauro/.Trash/Music"

Music is the name of the folder that I deleted from my desktop.

Do you know how I can remove this as well?

Thank you in advance...[/QUOTE]

Which directory is this folder actually in?  I can't visualise where it is from your description.

---

### Post by dnccnd on 2006-04-14
The folder actually doesn't exist! It was on my desktop, and I can only see it when I open File Browser.

According to the message that I get when I double-click on its icon, it should be in the wastebasket/trash, but I cannot see it there...

Very weird! Thanks for helping...

---

### Post by Mustard on 2006-04-14
[QUOTE=dnccnd]The folder actually doesn't exist! It was on my desktop, and I can only see it when I open File Browser.

According to the message that I get when I double-click on its icon, it should be in the wastebasket/trash, but I cannot see it there...

Very weird! Thanks for helping...[/QUOTE]

Ok, so lets try looking at the output of this command...

```
ls -al ~/Desktop
#shows all files/folders (including hidden files)
#on Desktop in long format
```

Paste the output of that command in here and show which file you want to get rid of in the output.

---

### Post by dnccnd on 2006-04-14
This is the output:

total 8
drwxr-xr-x   2 mauro mauro 4096 2006-04-15 00:19 .
drwxr-xr-x  43 mauro mauro 4096 2006-04-15 00:07 ..

On the desktop there is just the icon of hda1. Any idea?

---

### Post by Mustard on 2006-04-14
[QUOTE=dnccnd]This is the output:

total 8
drwxr-xr-x   2 mauro mauro 4096 2006-04-15 00:19 .
drwxr-xr-x  43 mauro mauro 4096 2006-04-15 00:07 ..

On the desktop there is just the icon of hda1. Any idea?[/QUOTE]

Is it a filed that you deleted from your other drive (hda1)?  I don't have much of an idea of whats going on atm.  Maybe you could try a screenshot.

---

### Post by dnccnd on 2006-04-15
No, the file was on the desktop. Hda1 should be my other Windows partition, as far as I have understood :-k 

I hope the screenshot is attached...

---

### Post by Mustard on 2006-04-15
Wow. I have no idea what that is. :D

I would create a new thread and include the screenshot and see if anyone else knows what that thing is.

---

### Post by dnccnd on 2006-04-15
Thank you anyway Mustard!

It was kind of you trying to find out....

---

