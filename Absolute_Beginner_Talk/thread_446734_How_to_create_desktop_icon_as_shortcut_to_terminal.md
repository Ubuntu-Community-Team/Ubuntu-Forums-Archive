---
title: "How to create desktop icon as shortcut to terminal command"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by linuxnooby on 2007-05-17
Hi,

As you will have guessed from my username, I am completely new to Linux. The problem I have, is as follows :-

I have installed  Wine in order to emulate a third party windows program. I have copied the windows program to the Ubuntu desktop and I can get it to run satisfactorily from the terminal with the command "wine <program name>"

Instead of having to run a terminal command, I would like to create a desktop icon to achieve the same result.

Any guidance would be appreciated.

---

### Post by starcraft.man on 2007-05-17
Right click on desktop, select Launcher... At the top, select application in terminal and then name it in the next box and put in your wine command in the command section. That it, very easy to make :)

---

### Post by drs305 on 2007-05-17
And in the command line of the launcher the command you would type would be something like this:

```

wine "C:\Acerose\Acerose.exe" 

```

---

### Post by topsites on 2007-05-17
Drag-and-drop, voila, shortcut, then right-click and "Open with Wine".

---

### Post by linuxnooby on 2007-05-17
Thanks guys - That was quick !

---

### Post by Karl S. on 2007-05-17
This seems to be a good thread for this question....

I want to create a launcher to run this command in terminal

cd ~/Desktop/MusicMagicMixer; export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun/jre/; ./MusicMagicMixer

I tried the solution listed here (right click on Desktop, Create Launcher, changed to 'Application in Terminal.' and pasted the command in the Command section. 

I get this error message: "There was an error creating the child process for this terminal"

Not a new user, but *not* a computer person. Thanks for any help you can give me.

---

### Post by lazyart on 2007-05-17
Always best to create a new thread than hijack another.  If someone comes looking for an answer later it will be easier to find.

Your answer-

open gedit and put those three commands in seperate lines
save it in your home directory as mmm.sh (or whatever you want to name it, but give it an .sh extension).

Now browse to that file, right-click>properties and make it executable (don't remember which tab it is and I am at work on a windows box).

Now create a launcher that calls the mmm.sh script (or whatever you called it).

There is probably a more elegant solution but this works for me.

---

### Post by Karl S. on 2007-05-17
Thanks. Works well, and doesn't seem at all inelegant to me.

---

### Post by bcalder01 on 2007-06-01
I created a script to check the ink levels on my Epson CX3700, NOW it's happening!! Thank you! It was that "make the file excecutable" bit that I was leaving out.

---

### Post by daimaru on 2007-06-01
> **linuxnooby said:**
> Hi,

As you will have guessed from my username, I am completely new to Linux. The problem I have, is as follows :-

I have installed  Wine in order to emulate a third party windows program. I have copied the windows program to the Ubuntu desktop and I can get it to run satisfactorily from the terminal with the command "wine <program name>"

Instead of having to run a terminal command, I would like to create a desktop icon to achieve the same result.

Any guidance would be appreciated.

dont you have a wine folder in your applications menu ? showed up for me and all installed programs are listed there. could just drag one out to the desktop. but otherwise do what the guy above me said :9

---

