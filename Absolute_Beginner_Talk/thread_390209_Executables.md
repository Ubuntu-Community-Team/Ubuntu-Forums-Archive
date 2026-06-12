---
title: "Executables"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by Hrundi on 2007-03-21
I'm completely new to ubuntu and therefore rather lost about how I should deal with the following problem:
I have a program that runs on executables, which is fine. I run the executable ./mName and it starts doing its thing. 
The issue is, the thing it's doing is starting other executables, and it does so like this:
mName <arguments>
without having a ./ infront. The command is not recognized and therefore the whole process terminates in an error claiming that there's no child executable.

How can I make this work? Is there a way to make ubuntu start executables in shell without the ./?

Sorry if this is a rather dumb question.

---

### Post by bulldog on 2007-03-21
If you're trying to install a .exe I have to disappoint you,it will not work.
This kind of files are windows install files and not suitable for Linux.

---

### Post by Hrundi on 2007-03-21
not .exe
x-executable I believe. 
They work, I can run them manually by ./executablename but the programs themselves call up other executables without the ./ which is causing the problem.

---

### Post by sessine on 2007-03-21
You need to set your PATH environment variable to include the current directory ".".  It is best to put this after the main directories such as /usr/bin.

try adding the following to your .bashrc file:

export PATH=$PATH:$HOME:.:

This appends your home directory ($HOME), and then the current working directory(.) to the search path for commands.  This way you will not have to use ./*executable* to run programs and the subsequent executions should work.  If they don't then you will need to add the directory containing the executable to your PATH also.

---

### Post by enharrin on 2007-03-21
If you want to always be able to execute files in your current directory, add something like this to the end of your ~/.bash_profile:

export PATH=$PATH:.


You will have to open another terminal for it to take affect.

---

### Post by Hrundi on 2007-03-21
I'll try a better explanation.
I cd to the directory, and there are about 50 executable files there.
I run one ./mProjExec with the arguments following. It follows through for awhile, and then starts calling up other executables in the folder.
mProjectPP <arguments>
And as far as I understand, this is where it terminates, because it doesn't place a ./ infront of the executable name. I can copy the command, put the ./ infront myself and it'd work, but the program itself needs to run several of these in a row, and I can't copy the other commands since it terminates right after the first one.

edit: Thanks! I'll try the PATH things, but I might not succeed since I'm rather clueless about em.

---

### Post by enharrin on 2007-03-21
The solution sessine and I gave should work.

You could also just add that specific path to your $PATH variable like this:

export PATH=$PATH:/the/directory/with/all/those/executables

---

