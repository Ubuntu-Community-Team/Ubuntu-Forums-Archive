---
title: "Ups. Deleted my rootshell - Where are the settings?"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by johsw on 2005-12-16
I tried to add a new user, and since I dont know what I'm doing, I accidentally edited the file where there's a pointer to my root shell. So now when I try to change to the root shell it says "Ingen skal", which means no shell i Danish.

Can you help me? What file did I change?

Thanx

/J.

---

### Post by bscbrit on 2005-12-16
Depending on which editor you were using, you might find a reference to the file in the recent file list.  For example, if you were using the default text editor, open it, click on Files, and towards the bottom of the list should be your file

**STOP !!!  DO NOT OPEN IT!!!**

If you have used the default editor, it will have made a backup of the original file, which is the same filename with a '~' character attached.  Copying this file back over your new (but incorrect) file will restore you earlier settings.

You can then try again, but I would recommend that you add and delete users using SYSTEM - ADMINISTRATION - USERS AND GROUPS if you have a GUI installed.  If you are at the command line then you will not have used the default editor and you may or may not have a backup copy of the original file.

---

### Post by johsw on 2005-12-16
I'm at the commandline. And the thing is I don't know which file I edited.

I know - it's really stupid :-(

---

### Post by bscbrit on 2005-12-16
In which case, on the command line, start pressing the up arrow.  It should scroll through the previous commands until you can see which command you used to open the editor.  I presume you also named the file to be edited there?

---

### Post by bscbrit on 2005-12-16
Why do you think that you have done something stupid? - I'll bet there is no-one reading this forum who has been using linux for any length of time who hasn't made a similar mistake.  Mistakes happen, errors happen, but I don't think that either you, or I, are stupid.
I have done this sort of thing more times that perhaps I ought to have done, which is why I keep a working copy of /etc backed up somewhere else.  Too late for you in this instance, but it might be worth thinking about for the future.

---

### Post by johsw on 2005-12-16
[QUOTE=bscbrit]In which case, on the command line, start pressing the up arrow.  It should scroll through the previous commands until you can see which command you used to open the editor.  I presume you also named the file to be edited there?[/QUOTE]

Yeah, but i did it from the root, which i now can't access, and therefore cannot find the previous commands for.

---

### Post by bscbrit on 2005-12-16
have you tried rebooting into recovery mode - that makes you 'root' by default.  I'm not sure if it will work in this case because I am not sure what has been corrupted.  But if it is something like /etc/sudoers then you will still be able to use recovery mode.

---

### Post by kalin on 2005-12-16
The history is kept in a ".bash_history" file in the user's home folder. For root you want to look in /root/.bash_history.

---

### Post by bscbrit on 2005-12-16
Can you recall which directory you were in when you edited the wrong file?  I guess it was /etc.  And what exactly were you trying to do?  If I knew what sort of file you were editing, I might be able to guess the likely culprits for corruption.

---

### Post by bscbrit on 2005-12-16
kalin - you are correct but I think that he can no longer get access to /root (But many thanks for your contribution - I hadn't thought of that!)

---

### Post by johsw on 2005-12-16
[QUOTE=kalin]The history is kept in a ".bash_history" file in the user's home folder. For root you want to look in /root/.bash_history.[/QUOTE]

Can't find anything, but dbootstrap_settings, there.

---

### Post by johsw on 2005-12-16
[QUOTE=bscbrit]have you tried rebooting into recovery mode - that makes you 'root' by default.  I'm not sure if it will work in this case because I am not sure what has been corrupted.  But if it is something like /etc/sudoers then you will still be able to use recovery mode.[/QUOTE]

This works, but I would like to know which file i messed up, so I can return it to the previous state without reinstalling.

...and BTW - Thanx for helping me out

---

### Post by bscbrit on 2005-12-16
use the 'find' command to discover which files have been changed in the last hour or so.  The details can be found using 'man find'.  That should give you a clue.
Thanks not necessary - but gratefully acknowledged.

---

### Post by bscbrit on 2005-12-16
Try

find  / -cmin -60

to find files that have changed in the last 60 minutes.

---

### Post by johsw on 2005-12-16
[QUOTE=bscbrit]Try

find  / -cmin -60

to find files that have changed in the last 60 minutes.[/QUOTE]

This one returns more that 5000 lines :-)

---

### Post by johsw on 2005-12-16
[QUOTE=bscbrit]Can you recall which directory you were in when you edited the wrong file?  I guess it was /etc.  And what exactly were you trying to do?  If I knew what sort of file you were editing, I might be able to guess the likely culprits for corruption.[/QUOTE]

I got access to .bash_history, but I still can't figure it out. But it msut a a sort of file, that contains a reference to the directory where information about root can be found ?!?!

---

### Post by bscbrit on 2005-12-16
Well, if you know which directory you were in you can shorten the list by replacing / with the appropriate path.  You can probably discount quite a few lines by looking at where they are.  Can you build a list using find for files changed more than 1 hour ago but less than, say, 90 minutes?  The start time of this thread will help to pinpoint the likely time of your mistake.  Without going into some fairly advanced 'grep', I cannot think of any easier way of shortening the list - perhaps someone else can?

---

### Post by bscbrit on 2005-12-16
SORRY - I may have given you a wrong suggestion. Try replacing -cmin with -mmin to identify modification time.  My mistake, apololgies again.

---

### Post by bscbrit on 2005-12-16
Even better, the following should find files modified between 2 specific times:

'find /path/to/search -mmin -60 -mmin -90

[Adjust to bracket the time that you estimated that you changed the file]

---

### Post by johsw on 2005-12-16
[QUOTE=bscbrit]SORRY - I may have given you a wrong suggestion. Try replacing -cmin with -mmin to identify modification time.  My mistake, apololgies again.[/QUOTE]

No problem - I'm just pleased that you help me. But I think I've found out, what i did wrong - I used chsh on root to change i to / 

I did sudo chsh -s /bin/bash root

and now it works ! Thank you for helping me out !!

---

### Post by bscbrit on 2005-12-16
No problems - see you around.

---

