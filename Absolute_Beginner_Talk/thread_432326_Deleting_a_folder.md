---
title: "Deleting a folder"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Ahunt on 2007-05-03
I seem to have created a puzzle that I can't solve, so I am hoping someone can suggest a cure.

In transferring some files to my new Ubuntu computer from my XP computer via a USB device I seem to have installed a folder that I can't delete. The folder was one containing a few music files. On XP it is a normal folder. I brought it over the the Ubuntu box and copied it from the jump drive to my home folder and it created it as a locked folder for some unknown reason. I was able to copy the files I wanted out of the folder. 

Now I want to delete it, but when I try to use Nautilus to do so it says"Cannot move "/home/adam...th's Music" to the trash because you do not have permissions to change it or its parent folder." 

I have some instructions on deleting files using sudo, but I obviously don't have the syntax right as I just get errors.

The file is located at "/home/adam/Ruth's Music". 

What causes folders to be installed as "locked" and how do I get rid of it?

Thank you for any help you can provide

Adam

---

### Post by nanotube on 2007-05-03
run a nautilus as root, and delete it. to run a root nautilus, run
```
gksudo nautilus
```

of course, you could also do the same with commandline, but it seems that a root nautilus is easier. :)

---

### Post by Billy McCann on 2007-05-03
> **Ahunt said:**
> What causes folders to be installed as "locked" and how do I get rid of it?
I'm not sure what caused your folder to be "locked", other than the fact that it's locked because "root" (the computer administrator) is the owner of the file.  Root may have owned the USB drive that you copied the folder from.  

Opening Nautilus using alt-f2 and then entering "gksudo nautilus" works but it can be dangerous.  Become familiar with the command line.  There are man pages and help displays for nearly every command.  

To learn more about the rm (remove) command, simply type (in the terminal) ...

```
man rm
```

or you can get the quick version with 

```
rm --help
```

If root owns the folder then root is the one who must delete the folder, or change the permissions to give the folder to someone else.  

To remove a folder that root owns, simply use the rm command with the -r flag (recursive; read the man page for more info).  Since root owns the folder, you must place a "sudo" before the command to be given root priviledges.  Something like "sudo rm -r /path/to/directory".  

In your case the command will be 
```
sudo rm -r ~/Ruth's\ Music
```

The ~ is a quick way of writing /home/yourusername.  ~ = /home/yourusername.  So ~/Ruth's Music = /home/adam/Ruth's\ Music.

You place a \ after "Ruth's" to indicate that what follows is appended to the name.  Otherwise the terminal will think you want to remove (recursively) the folder named Ruth's and the folder named Music.  The \ puts them both together.  DOS allows you to use quotations, which is nice. 

Also, instead of typing out "Ruth's\ Music" in it's entirety you can simply type "Ru" amd then press the tab key.  Pressing tab will autocomplete anything in the terminal.  Even DOS does this.  It's totally freakin' awesome.

You can also change who owns the folder.  Read the chown man pages for more help on this.

```
man chown
```

or simply type "chown --help" in the terminal.

---

### Post by Ahunt on 2007-05-04
Thanks for the detailed reply!

The "folder properties" indicates that I own the folder, not root, but still will not let me delete it.

I tried running

sudo rm -r ~/Ruth's\ Music

but the terminal responded just with 

">"

and nothing else. The folder was not affected.

Next I tried your suggestion to open Nautilus using alt-f2 and then entering "gksudo nautilus". That allowed me to find the file and remove it just fine.

Thank you both for your help on this. As usual this forum has proven a great resource. On Monday I start a Linux course, so maybe that will cut down the questions I find myself asking!

Now I just wish I had known how I created the locked folder in the first place. I am assuming that it was some characteristic of the folder that was transferred from Windows XP. I have transferred many folders to mirror my XP PC onto the Ubuntu one, but this is the first one that has done that!

Adam

---

### Post by Mrs. G on 2007-05-07
Hello there,

Some files were deleted from my computer at work. What do I need to do to trace the user who did it? I contacted the IT department and they said there is no way we can find this out. I simply do not accept that. Can anyone help me to find this out?

Thank you....

---

### Post by nanotube on 2007-05-07
first of all, you should have started a new thread with your question - this thread was completely unrelated to your query.

but, while we are here... can you give us some more information of your environment. what OS are you running? under what circumstances were the files deleted (i.e. did you walk away from your desk, leaving the computer logged in, and someone did it that way, or was the box hacked remotely? are there multiple user accounts on the computer and was one of those likely used? were the files in your user directory, or in a system dir? were they owned by root or by your user?

and of course, in the meantime, try not to do anything on your comp, to make sure no logs or traces get overwritten, if there are any in the first place.

---

