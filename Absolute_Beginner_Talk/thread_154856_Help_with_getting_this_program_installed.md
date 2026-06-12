---
title: "Help with getting this program installed"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by slipk487 on 2006-04-04
I need help getting this installed for notMD i already know that linux reconies the Net MD Device i have a MZ-N420D


Im told to do this and i dont know what NotMD is better

```
  Here you can download the stable releases and find instructions how to do a CVS checkout of NotMD
Releases:

NotMD 0.50902-unfinished
Drivers included: Aiwa XR-MD201
Technologies supported: NotMD, NetMD, FunkyMD (all unfinished)

NotMD 0.1.1
Drivers included: Aiwa XR-MD201
Technologies supported: NotMD

Download



CVS:

Step 1. Check the dependencies
Go here and ensure each of these dependencies is correctly installed on your PC, if not, install them and go on.

Step 2. Check out the source

Run the following commands in a directory that you have write access to (such as your home directory):

cvs -d ':pserver:anonymous@cvs.sourceforge.net:/cvsroot/notmd' login

(Just hit enter for the password)

cvs -z3 -d ':pserver:anonymous@cvs.sourceforge.net:/cvsroot/notmd' checkout unstable

You should see it listing all the source files.

Step 3. Test it

Now you should have a file called notmd.py, make it executable by running

chmod +x notmd.py

When you run the file, hopefully everything works and you're happy. If you aren't, there are several places where you can find help:

    *  the documentation
    *  the list of bugs
    * If you still need help, you can try and contact the mailing list.


```

---

### Post by Pragmatist on 2006-04-04
Besides checking that you have all the dependencies (required additional software), you just follow their instructions.  You go into a terminal and type the commands, one-by-one, waiting for each one to finish before running the next one.

Please be specific about what part of the instructions are giving you trouble.

---

### Post by slipk487 on 2006-04-04
i never found anything about installing this program pygtk-2.8.5.tar.gz from there site so im not sure how to

---

### Post by Pragmatist on 2006-04-04
>  Originally Posted by: [B]slipk487

[/B]CVS:

Step 1. Check the dependencies
Go here and ensure each of these dependencies is correctly installed on your PC, if not, install them and go on.

Step 2. Check out the source

Run the following commands in a directory that you have write access to (such as your home directory):

cvs -d ':pserver:anonymous@cvs.sourceforge.net:/cvsroot/notmd' login

(Just hit enter for the password)

cvs -z3 -d ':pserver:anonymous@cvs.sourceforge.net:/cvsroot/notmd' checkout unstable

You should see it listing all the source files.

Step 3. Test it

Now you should have a file called notmd.py, make it executable by running

chmod +x notmd.py

When you run the file, hopefully everything works and you're happy. If you aren't, there are several places where you can find help:

    *  the documentation
    *  the list of bugs
    * If you still need help, you can try and contact the mailing list. 

These are the directions you posted.  I don't see anything about pygtk-2.8.5.tar.gz

Did you do this yet:
>  Step 1. Check the dependencies
Go here and ensure each of these dependencies is correctly installed on your PC, if not, install them and go on.


---

### Post by slipk487 on 2006-04-04
i dont have pygtk-2.8.5 installed and i need to install it

---

### Post by Pragmatist on 2006-04-05
Ok, I just downloaded the package you attached with your original post.  Try this in a terminal:

First copy pygtk-2.8.5.tar.gz into your home directory.  Then, in your home directory, type this:
```
tar xvzf pygtk-2.8.5.tar.gz
```

Now switch into the new directory that was created:
```
cd  pygtk-2.8.5
```

Now read the INSTALL file:
```
gedit INSTALL
```

Try those instructions and come back with specific questions/problems.

---

### Post by slipk487 on 2006-04-05
i can do everything up to make but i get a 

bash: make: command not found

error

---

### Post by slipk487 on 2006-04-05
i can never get the make command to work

---

### Post by meborc on 2006-04-05
do you have the build-essential package installed?

if not:
**sudo apt-get install build-essential**

---

### Post by slipk487 on 2006-04-05
i got this error

```
make: *** No targets specified and no makefile found.  Stop.

```

---

### Post by Pragmatist on 2006-04-05
Go into the directory that was created after you used the **tar** command.  Then type: **ls**  and give us the output here.

---

