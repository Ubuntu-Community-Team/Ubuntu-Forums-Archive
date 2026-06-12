---
title: "Easy Dangerous Command Protection (to come extent)"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2008-01-18
[COLOR=DarkRed]**Introduction:**[/COLOR]
[COLOR=Black]I am sure you have all seen and read the [excellent article on dangerous commands]("http://ubuntuforums.org/announcement.php?f=73"), and since I liked it, I'm learning python, and I wanted something to do,  I decided to build a python script that basically *becomes* your terminal, but checks for commands that could be dangerous! :D

If you enter a command that is potentially dangerous, it will warn you and only continue if you enter "y" or "yes"!

My source of dangerous commands is the list from the article, and thus, as it says, is not complete - there are many more things that could be dangerous, but for a little extra protection, I think this is pretty good![/COLOR]

[B][COLOR=DarkRed]Basic Operation:[/COLOR]
[/B][LIST=1]
[*][COLOR=Black]Download, extract, and "run in terminal"
[/COLOR]
[*][COLOR=Black]You will see the familiar prompt, and it functions much like a regular terminal[/COLOR]
[*][COLOR=Black]From here you can do almost anything you can from the normal terminal, but just with more protection
[/COLOR][/LIST][LIST]
[*][COLOR=Black]To exit the script and go back to the normal terminal, just type "exit" like you would in the normal terminal![/COLOR]
[*][COLOR=Black]It is known at the time that commands containing brackets, as in "(" and ")", and the "cd" command appear to be non-functional[/COLOR]
[*][COLOR=DarkRed]Users should be notified that this will only check *commands*, not *scripts!*  The contents of any scripts you run will NOT be scanned![/COLOR]
[*][COLOR=DarkRed]For protection against *scripts*, use the included "scriptScanner"[/COLOR]
[*][COLOR=Black]**[COLOR=Red]This is not fool-proof!  [COLOR=DarkRed]Harmless files might be labeled as bad, and yet some very harmful files might slip though as clean![/COLOR][/COLOR]**[/COLOR][/LIST][COLOR=DarkRed][B][SIZE=4][COLOR=Blue]NEW!!:[/COLOR][/SIZE]
[/B][/COLOR][LIST]
[*]The second attachment, "bashrc.tar.bz2", is a file for the terminal - just download, extract, put it in your home folder (and root too for maximum protection) and then rename it ".bashrc".
[*]Once again, it is not fool proof, but it is very nice when it comes to easy protection.
[*]There is no further setup required, just put it in your home folder, rename it ".bashrc", and *any* potentially dangerous command run in the terminal will be intercepted! (some it just blocks, some it will warn, wait 4 seconds and continue, and some it will just allow, but it will add safety options!:D)[/LIST]*any as in, most of the common ones, but there will always be strange ways to do things, and the user will just have to be careful!

---

### Post by ryanVickers on 2008-01-18
I would have expected some kind of comments by now... good? bad?

I realize that without the functionality of being able to change directories, its rather useless, but if I can get that working and add more to the list of dangers, I think this will be nice to help new users feel more comfortable...

---

### Post by p_quarles on 2008-01-18
How does this script handle passwords? Since many of the "dangerous" commands require that the user gain root privileges, I'm just curious about how this script would accept and check a password against /etc/shadow without sending it to plain text.

---

### Post by ryanVickers on 2008-01-18
I'm not sure... I have my computer setup to not ask every time, so I'll see about that now, but how it works is the python script just executes the command inside itself, and since sudo, gksudo, and all the like do not actually print the password, I do not believe this to be a worry.

EDIT: I have proof this is fine - it does allow you to switch and run stuff as root like normal, and it does not print any passwords!

---

### Post by wormser on 2008-01-19
Something like this should be built into the shell.  Dangerous commands should have a yes to confirm.  It could be design where it can be turned off for experienced users.

---

### Post by asmoore82 on 2008-01-19
```
#~/.bashrc
...
alias cp='cp -iv'
alias rm='rm -iv'
alias mv='mv -iv'
...
```
:KS

---

### Post by ryanVickers on 2008-01-19
IDK, If anyone thinks up a better idea, please, go ahead and work on a project like this!  In the mean time however, I just wanted to get the idea out there...

---

