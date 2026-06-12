---
title: "Creating a launcher"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by browny254 on 2008-01-21
Hi, Im trying to create a launcher for a program I use, but Im not sure how to fill it in in the command box.

Currently to start the program i have to navigate to the directory
[INDENT]cd Programs/SRT/IBMJava2-142[/INDENT]

then to run the app I have to type
[INDENT]./bin/java srt 1 1[/INDENT]

the 1 1 at the end of the name starts the program in different modes, ie 1 1 is a simulation mode, where 0 0 is full operational mode...i want to create a few different launchers for each combination.

If its not possible to create a launcher is it possible to set it up so I dont have to navigate so far to start it? eg to start firefox, you just have to type Firefox.

---

### Post by Majorix on 2008-01-21
You can of course create different launchers for each combination - why shouldn't you be able to? Just make sure you use "xterm -e" (after installing xterm) infront of them if you get stuck.

---

### Post by browny254 on 2008-01-21
yeah im not sure what to type in the command line of the screen to create a launcher...do i type cd Programs/SRT/IBMJava2-142/ ./bin/java srt 1 1
because i tried that and it doesnt work...its like i need 2 lines to enter the command

---

### Post by banewman on 2008-01-21
You just need to enter the path to the file. If I'm correct it should be
Programs/SRT/IBMJava2-142/bin/java srt 1 1
I guess that folder "Programs" is one you made?
:)

---

### Post by Majorix on 2008-01-21
I would go like this:
```
sudo apt-get install xterm
```
to make sure it's installed.
Then in the launcher menu, type this for the command:
```
xterm -e "the commands go here. don't forget to put a ; or && between trailing commands. quotes are necessary"
```

---

### Post by browny254 on 2008-01-21
yeah Programs is a folder I made...wanted to keep all my programs in the 1 spot.

I tried what you said and nothing happens...when i double click the icon that is made there is no response. should something appear in the terminal to say its working or not?

---

### Post by banewman on 2008-01-21
Sorry my bad - should be
/Programs/SRT/IBMJava2-142/bin/java srt 1 1
forgot the first / < oops :)

---

### Post by Perfect Storm on 2008-01-21
Another way around would be creating a script

script.sh

```
#!/bin/bash

<commands>
<commands>
```

chmod+x it.

---

### Post by browny254 on 2008-01-21
when i type this 
/Programs/SRT/IBMJava2-142/bin/java srt 1 1 
i get "There was an error launching the application. Failed to execute child process "/Programs/SRT/IBMJava2-142/bin/java" (No Such file or directory)"


Majorix - thanks, i will try that later, my linux computer has no internet access at the moment because im at uni so i will have to wait until im home to download xterm

---

### Post by Perfect Storm on 2008-01-21
Where is this program directory? When you do /programs you are referring to that there's a directory in root called /programs.

---

### Post by browny254 on 2008-01-21
Artificial Intelligence - 

can you elaborate a bit more on that, im really new to linux.

what i did was create a file called script.sh which contained
 #! /bin/bash
cd Programs/SRT/IBMJava2-142
./bin/java srt 1 1


not sure what to do next then with the chmod+x

---

### Post by browny254 on 2008-01-21
there is a directory in home called Programs

---

### Post by banewman on 2008-01-21
I copied and pasted the command I gave you from your comments so you need to browse to the file you need to run
/home/YOU/Programs/SRT/IBM/Java2-142/bin/java srt 1 1 might be it
But you need to enter the path to the file
:)

---

### Post by Perfect Storm on 2008-01-21
Yes of cause.

To use a directory in your home, use the **~** in front
eg.

~/Programs/SRT/IBMJava2-142


If you do

/Programs/SRT/IBMJava2-142

it assume your looking for something in root.

structure
[img]http://bp3.blogger.com/_Vbsj-yhipTw/RvaiatPBPBI/AAAAAAAAABs/yjx3hPlEUNw/s1600/linux_file_structure.jpg[/img]

---

### Post by browny254 on 2008-01-21
just tried that and got no response again. without the /home/ME part i would get an error

---

### Post by browny254 on 2008-01-21
with the ~ i get the error about no such file or directory.

with the ./bin/java srt 1 1 it is to launch the application which is a java program so is this where the problem with not finding the file or directory would be?

---

### Post by Perfect Storm on 2008-01-21
```

#! /bin/bash
cd ~/Programs/SRT/IBMJava2-142
./bin/java srt 1 1

```

chmod+x <name of the script file>


By the way shouldn't it be

~/Programs/SRT/IBMJava2-142/bin ?

---

### Post by browny254 on 2008-01-21
maybe if i give you a link to the program you can see the instructions on how to start it and can give me more help than me trying to explain it all...

[http://www.haystack.mit.edu/edu/undergrad/srt/SRT%20Software/linuxdl.html](http://www.haystack.mit.edu/edu/undergrad/srt/SRT%20Software/linuxdl.html)

---

### Post by browny254 on 2008-01-21
ok running the script works if i double click on it and choose run in terminal, but typing chmod +x didnt do anything...?

---

### Post by erfahren on 2008-01-21
> **browny254 said:**
> ok running the script works if i double click on it and choose run in terminal, but typing chmod +x didnt do anything...?you can just right-click on it - go to Properties > Permissions tab and check "Allow executing as a program"

---

### Post by browny254 on 2008-01-21
ok i did that but i still get a pop up asking if i want to run the script or display its contents.

is there some way to bypass this?

---

### Post by RomeReactor on 2008-01-21
Hi. Try filling out the 'Command' section of a launcher like this:
```
sh -c "cd /home/YOUR_USERNAME/Programs && ./bin/java srt 1 1"
```

Just make sure to substitue YOUR_USERNAME for your actual username.

---

### Post by erfahren on 2008-01-21
> **browny254 said:**
> ok i did that but i still get a pop up asking if i want to run the script or display its contents.

is there some way to bypass this?
yes - this is what I do

you can create a directory named "bin" in your home folder and put it in there. see: [http://www.linuxcommand.org/wss0010.php#path](http://www.linuxcommand.org/wss0010.php#path)

that path is already set up by default in Ubuntu (in your ~/.profile ) - sometimes I needed to initially set the path (see link) but worked after logging out and back in 

if you did that you could create the different script for the different options of the program and name them accordingly (they don't necessarily need to end with ".sh" - just "start_srt" or whatever).

then to create a launcher for them the command is just "start_srt"

---

### Post by browny254 on 2008-01-21
> **RomeReactor said:**
> Hi. Try filling out the 'Command' section of a launcher like this:
```
sh -c "cd /home/YOUR_USERNAME/Programs && ./bin/java srt 1 1"
```

Just make sure to substitue YOUR_USERNAME for your actual username.

that worked perfectly! cheers!

---

### Post by Majorix on 2008-01-21
BTW why don't you execute the program from the working directory? Just do a
```
sh -c "/home/USERNAME/Programs/bin/java srt 1 1"
```
It is not absolutely necessary, but will help you understand the bash :)

---

### Post by mivo on 2008-01-21
> **RomeReactor said:**
> ```
sh -c "cd /home/YOUR_USERNAME/Programs && ./bin/java srt 1 1"
```

Thank you. I was looking for the same solution after manually installing a commercial chess program (the auto-installer failed), Shredder 11.

---

