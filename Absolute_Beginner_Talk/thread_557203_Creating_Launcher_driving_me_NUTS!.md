---
title: "Creating Launcher driving me NUTS!"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by Tony3286 on 2007-09-22
I'm new to creating lunchers in Ubuntu - I've tried to read every post concern this topic
so I wouldn't have to create a post but I'm lost.

I downloaded a program called "ATTIC" a home inventory program, and uncompressed it in its own directory. The path is:

/home/tony/attic inventory/attic-1.01-i386.tar.gz_FILES/attic-1.01-i386/run-attic.sh

I create a luncher using this path and I can not execute the file. I get the message-

Details: Failed to execute child process "/home/tony/attic" (No such file or directory)


If I go into the directory and click on run-attic.sh, the program runs.

The Readme file for the program states:

To run the program, unpack this archive to some directory and then start

run-attic.sh

If you do it from shell, it goes something like this:

tar -xzvf attic-1.0-i386.tar.gz
cd attic-1.0-i386
./run-attic.sh

I know its going to be a simple addition to the string, but I've tried everything, putting  **sh** in front of the string, put **sh** before run-attic.sh and nothing.
I'm so use to Windows that I must still be in Windows mode when it comes to shortcuts.
Would really appreciate any help

Thanks 
Tony

---

### Post by Linux_Man on 2007-09-22
If its a shell script you would most likely need to make it have the "run from terminal" on the launcher. Try that.

---

### Post by walkerk on 2007-09-22
> **Tony3286 said:**
> I'm new to creating lunchers in Ubuntu - I've tried to read every post concern this topic
so I wouldn't have to create a post but I'm lost.

I downloaded a program called "ATTIC" a home inventory program, and uncompressed it in its own directory. The path is:

/home/tony/attic inventory/attic-1.01-i386.tar.gz_FILES/attic-1.01-i386/run-attic.sh

I create a luncher using this path and I can not execute the file. I get the message-

Details: Failed to execute child process "/home/tony/attic" (No such file or directory)


If I go into the directory and click on run-attic.sh, the program runs.

The Readme file for the program states:

To run the program, unpack this archive to some directory and then start

run-attic.sh

If you do it from shell, it goes something like this:

tar -xzvf attic-1.0-i386.tar.gz
cd attic-1.0-i386
./run-attic.sh

I know its going to be a simple addition to the string, but I've tried everything, putting  **sh** in front of the string, put **sh** before run-attic.sh and nothing.
I'm so use to Windows that I must still be in Windows mode when it comes to shortcuts.
Would really appreciate any help

Thanks 
Tony

its not reading the space in "attic inventory".. use nautilus to rename the "attic inventory" folder to "attic_inventory"

?

---

### Post by Tony3286 on 2007-09-22
Thanks for quick reply but just tried that and got:

There was an error creating the child process for this terminal

---

### Post by walkerk on 2007-09-22
in terminal do this
```
cd /home/tony/attic inventory/attic-1.01-i386.tar.gz_FILES/attic-1.01-i386/
```
```
sh run-attic.sh
```

did that work?

---

### Post by Tony3286 on 2007-09-22
Just changed the directory and now path is:

/home/tony/attic_inventory/attic-1.01-i386.tar.gz_FILES/attic-1.01-i386/run-attic.sh

And still doesn't open - I click and nothing - also made sure I check "allow executing file as program

---

### Post by Linux_Man on 2007-09-22
Open up the shell script in gedit and copy and paste the contents here so we can better help you and help identify the problem.

---

### Post by walkerk on 2007-09-22
> **Tony3286 said:**
> Just changed the directory and now path is:

/home/tony/attic_inventory/attic-1.01-i386.tar.gz_FILES/attic-1.01-i386/run-attic.sh

And still doesn't open - I click and nothing - also made sure I check "allow executing file as program

it runs when you double click it? 

would you open run-attic.sh with gedit and paste its contents here..

---

### Post by Tony3286 on 2007-09-22
Running in terminal didn't work with that string - I changed the directory to just attic
the string now is

/home/tony/attic/attic-1.01-i386.tar.gz_FILES/attic-1.01-i386/run-attic.sh

I used your example to try THIS string in terminal AND IT worked - so somehow the
attic_inventory was also causing a problem. Now that its working in terminal how do  get it to work with a launcher?

---

### Post by Tony3286 on 2007-09-22
Sorry guys for the delay - really new to this - just found gedit.
Heres the info:

#!/bin/bash
export FIREBIRD=.
export LD_LIBRARY_PATH=.
export ATTIC_DIRECTORY=`pwd`
./attic

---

### Post by walkerk on 2007-09-22
not too sure why it wont load directly.. i'd have to be there to see..

BUT, this is a work around. do the following in terminal:

```
gedit ~/attic.sh
```

insert the following, save and exit:
```
#!/bin/bash

cd /home/tony/attic/attic-1.01-i386.tar.gz_FILES/attic-1.01-i386/
sh run-attic.sh

```

```
chmod +x attic.sh
```

 now create a launcher:

Name: Attic
Command: /home/tony/attic.sh



though calling this **should** work:
Name: Attic
Command: /home/tony/attic/attic-1.01-i386.tar.gz_FILES/attic-1.01-i386/run-attic.sh

---

### Post by Tony3286 on 2007-09-22
OK got into gedit, then added your bash script - Do I save this now? and when do I save the Chmod string?  Told you I'm new - very sorry!

---

### Post by walkerk on 2007-09-22
> **Tony3286 said:**
> OK got into gedit, then added your bash script - Do I save this now? and when do I save the Chmod string?  Told you I'm new - very sorry!

yes save the file and exit..

now in terminal again:
```
chmod +x ~/attic.sh
```


now make a launcher:

name: attic
command: ~/attic.sh

---

### Post by Tony3286 on 2007-09-22
Did everything you said - step by step - when I click the icon I get:

Details: Failed to execute child process "/home/tony/attic/attic-1.01-i386.tar.gz_FILES/attic-1.01-i386/" (Permission denied)

the command line read:

home/tony/attic/attic-1.01-i386.tar.gz_FILES/attic-1.01-i386/
sh run-attic.sh

and I went into permission and checked allow executing and read and write for tony and still get permission denied

---

### Post by Tony3286 on 2007-09-22
Walkerk

I decided to go into the Attic directory - found the Bash script you had me save and clicked
on "Make Link" - then dragged that to desktop and BOOM program starts - Don't know why I can't do this from Desktop launcher but at least I now have a shortcut for the Attic program.
Thank you so much - without your script, even this wouldn't have worked.

Tony

---

