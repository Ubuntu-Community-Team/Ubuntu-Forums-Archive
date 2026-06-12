---
title: "unistalling tar.gz - make not found problem..."
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by andrewsco on 2006-01-25
I am trying to install a tar.gz file. I have managed to unzip in and it is on my desktop.

When i do the following commands:
> 
./configure
make
sudo make install

For some reason it says that make is not ./configure is not a command. I try just make and it says that is not a command. Is there something I am doing wrong?

Thanks
Andrew

---

### Post by Pablo_Escobar on 2006-01-25
What are You trying to compile ??
If it's CVS, it's probably ./autogen.sh
or sometimes it's ./install.sh
it doesn't have to be ./configure every time.
Look for a readme in that package, it'll probably tell You how to compile it properly.

---

### Post by ubuntuuser on 2006-01-25
Have you installed the build-essential package? If not, open a terminal and type ```
sudo apt-get install build-esential
```.

---

### Post by andrewsco on 2006-01-25
[QUOTE=ubuntuuser]Have you installed the build-essential package? If not, open a terminal and type ```
sudo apt-get install build-esential
```.[/QUOTE]

It doesn't ring a bell...

I'm at work, but I will try this when I get home. To answer the first question I was following a tutorial so it should have worked - hopefully this will resolve the issue.

Andrew

---

### Post by Who on 2006-01-25
Hiya,

Just so youn know, you aren't really 'installing' that tar.gz, you are compiling the code inside it in to a program on your PC - much more clever! :)

There is a _much_ easier way to install software on Linux, but not all programs are available. If you go to System-->Administration-->Synaptic (Package Manager) then you can search for software's name and description, right click on any software you want and choose to install it, then click apply on the toolbar to do the install. If you can't find it then go to Settings-->Repositories and add all the repositories you are comfortable with (legally, morally - etc, it is all explained) - and then search again. **This is by far the best way to install programs because it means all users can use them, they can be easily removed and that the libraries they depend on will be managed properly...**

If you can't find what you want there and you do _really_ want to compile this code of yours (Which app is it? there may be a similar one in the Synaptic database that we can point you to) then read on.

So - Because the make/compile process often causes lots of folders to be made,changed etc, I would suggest very strongly that you don't do this from the desktop! some of thos files are required for the program to run - so they will just clutter your desktop up! I would do it in a sub folder of my home directory - say /home/username/programname (otherwise denoted ~/programname). So..

Copy the .tar.gz to that location
then unzip/unpack it. 
Look inside the folder that this creates (using Nautilus, for example) for a readme - and if it exists follow that. IF not here are some vague general instructions that MAY help...

open a terminal
-here is the step you were probably missing-
use the cd command at a terminal to go to the folder that the .tar.gz created
(probably something like 'cd /programname/program_files')
use the ls command to look for files
if there is a file called configure then you are probably in the place you want to be in to run ./configure and make as descriped in the original post
otherwise, look at the directories listed and choose one tom look inside for a configure script - continue until you find the right folder, and then do configure and make (note: You can use Nautilus to do this hunting)

I hope that works - basically - there will almost certauinly be a readme or an install instructions file for you to follow, so find that first - it'll probably be in the same place as the configure script

Good luck!

Who

---

