---
title: "Help with CLI"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by tdol002 on 2007-07-25
Hi,

I'm looking to copy an image and convert it into the current working directory, this is being done in a c file.
At the moment I have as follows:

cd /afs/ele/projects/2007/compsys202/Images/Today; convert `ls | tail -1` ~/compsys/test_folder/input.bmp

What i want is to change ~/compsys/test_folder/input.bmp so that the file is converted and saved onto the current working directoryso that it will work on whatever computer it is on (of course within the local network) I tried some noob stuff like slotting in pwd and such but it doesnt work.  Any help is greatly appreciated.

---

### Post by trent dillman on 2007-07-25
...

---

### Post by tdol002 on 2007-07-25
> **trent dillman said:**
> Is this in c or a shell script?

This is within c using the gedit program

i.e Within the file i have

System("cd /afs/ele/projects/2007/compsys202/Images/Today; convert `ls | tail -1` ~/compsys/test_folder/input.bmp")

---

### Post by p_quarles on 2007-07-25
First off, I've never used the "convert" command, so others are probably more qualified to speak on that. I'll just help with the the command-line syntax.

To copy into the working directory, type:
```
sudo cp /path/to/files .
```To convert, you would type something like (again, I'm unsure of the specifics here):
```
sudo convert *.jpg *.png
```You can also "pipe" these commands into one function by separating them with the bar, like so:
```
sudo cp /path/to/files . | sudo convert *.jpg *.png
```EDIT: According to your second post, you're not using the Linux command line. You need to either compile the script or run it through a c interpreter.

---

### Post by tdol002 on 2007-07-25
Thanks for all the input :)

I suppose i should explain that im trying to copy a constantly changing file, i.e. updating security images so I cant input filenames.  So yeah i thought there may be a kind of working directory shortcut.  The following is purely an example:

cp /somefolder/example.jpg to /thecurrentworkingdirectory

---

### Post by p_quarles on 2007-07-25
Yes, but this works in bash, and not in C:
```
 cp/somefolder/example.jpg .
```
The "." stands for the working directory.

---

