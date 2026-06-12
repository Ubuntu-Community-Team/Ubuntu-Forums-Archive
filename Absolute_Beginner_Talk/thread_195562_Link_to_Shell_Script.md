---
title: "Link to Shell Script"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by michaeljb2005 on 2006-06-13
How do I create a link to shell script or in starterbar in gesklets?  When I create a link it does nothing unless it's in the same directory as the item it links to.  I know in kde it lets you specify the directory in the launcher and then do ./application.  Is there something like that in gnome?

---

### Post by aysiu on 2006-06-13
Maybe check "run in terminal" and forget the ./ in the beginning?

---

### Post by michaeljb2005 on 2006-06-13
[QUOTE=aysiu]Maybe check "run in terminal" and forget the ./ in the beginning?[/QUOTE]

checked run in terminal, the terminal shows up for a brief second and then goes away.  I don't put the ./ in front of the command.  I only specify the directory and of course the file I want to execute in the directory.  That doesn't seem to work.  I used kde before and it allowed me to designate the directory and then execute the command within that directory from the launcher.  Sometimes I had to do that for this very reason.  For some reason /home/mike/PCGames/nwn which is the command to execute the shell does nothing if it isn't executed within the directory the shell file is in.

---

### Post by 23meg on 2006-06-13
What exactly does your script do? When you click it and the terminal appears and disappears, does it actually do its job? If it has terminal specific functions try appending the following command to its end```
read
```to make it wait for user input before exiting.

---

### Post by michaeljb2005 on 2006-06-13
[QUOTE=23meg]What exactly does your script do? When you click it and the terminal appears and disappears, does it actually do its job? If it has terminal specific functions try appending the following command to its end```
read
```to make it wait for user input before exiting.[/QUOTE]

Ok all i'm trying to do is create links to shell script.  I don't want to have to enter in commands when I double click on the icon.  Double clicking should start the program.  The game neverwinter nights uses a shell script for it's primary executable and I want to create a link on the desktop or gdesklets to click on and start the program.  When I create a link to the program the link does nothing unless it's within the same directory.  This happens with many shell scripts for some reason.  I know this isn't a bug because it's happened when I used suse and other linux desktops.  It's a problem with the execution of shell scripts in general.  I just want to know if there's a way around it?  Maybe I should create a link within a bin directory and then I should be able to excecute the file via a single word?  None of you have ever experienced this?  

edit:  I solved the problem.  It was created to execute the file within the specified directory assuming it was in that directory.  I had to specify the directory within the shell script so that it could do it from any location.  Thanks for your input.  Sorry if I seem frustrated.

---

