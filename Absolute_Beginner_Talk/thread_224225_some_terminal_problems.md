---
title: "some terminal problems"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by m0nkey_magic on 2006-07-27
im very very very new to linux and have just installed ubuntu 6.06 LTS Dapper Drake.
I have a DWL-G520+ D-link wireless card whic isnt working , so ive got the correct drivers but when im trying to navigate to the location where they are saved thats where the problems start.
ive saved them on the desktop & copy&pasted to /home/m0nkey . the folder is called ndiswrapper-1.21.tar.gz

when i open the console it starts at 
m0nkey@m0nkey-desktop:~s
if i type ls
i just get the items 
desktop examples 
i doesnt show the folder i want , so i try getting to the other folder within home
i can cd /home
and ls gives me "m0nkey" listed there
but i cant cd to m0nkey , 
i get a no such file or directory error ...
how can i get to the folders ive saved and try to install he drivers???
as i said im very very new to linux but am pc literate so will be able to understand any info given to me ....
sorry if i seem stupid but ive never used linux before and am impressed to a point ..but really would like to ditch windows full stop ///
many thanks for reading this ,,,,

=:-)

---

### Post by gingermark on 2006-07-27
Your problem is that ndiswrapper-1.21.tar.gz isn't a folder, it's a compressed file (much like a zip file). If you want to access the contents you'll need to extract it.

Right click on the file in your file manager, and there should be an option to extract it.

---

### Post by ovimunt on 2006-07-27
Can you copy and paste the command line output of ls in each of those folders you were navigating through?

And by the way, ndiswrapper is NOT a driver! It's just an application that allows you to install Windows drivers in linux.

---

### Post by aysiu on 2006-07-27
Have you tried this? ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ndiswrapper-utils
```

---

### Post by m0nkey_magic on 2006-07-28
> **gingermark said:**
> Your problem is that ndiswrapper-1.21.tar.gz isn't a folder, it's a compressed file (much like a zip file). If you want to access the contents you'll need to extract it.

Right click on the file in your file manager, and there should be an option to extract it.

lol ..sorry my bad ...i was copying it from my cdrom ...
i have extracted the file ...its labelled ndiswrapper-1.21 
so when i read the install file 
it advises changing to the ndiswrapper directory and 
typing 
make unistall
make
then login as root 
make install
but its the chanign to directory bit that eludes me !!
@OVIMUNT
heres those outputs you wanted 
1.Desktop gives me 
Desktop Examples
2.Home gives me m0nkey
but i cant cd to m0nkey ...
although i can navigate using GUI and go to HD1>Home>M0nkey>ndiswrapper
and yes im aware that ndiswrapper isnt actually a driver as such ...sorry i worded that a little wrong i guess.
@ aysiu

sudo apt-cdrom add - mounts the cdrom and displays the zipped file in another window called cdrom.
sudo aptitude update - that doesnt work as i have no internet connection , but it does go through a whole process of reading , building etc until it tries accessign the net.
sudo aptitude install ndiswrapper-utils - again that goes through the reading, building process until i get an error stating it cannot find any package whose name or description matched "ndiswrapper-utils" i even tried it with the ndiswrapper-1.21 but same error appeared, the funny thing is tho that i can see the utils folder when i browse the ndiswrapper folder !!!

help :sad:

---

### Post by 3rdalbum on 2006-07-28
The /home folder is not your user's home directory, it's actually the folder that contains the home directories of all users. Your home directory is actually at the location /home/m0nkey

To get to your home directory, just type "cd" at any time.

I think you may be making a little mistake I used to make when I first started. If you're in /home/, and you want to cd to "/home/m0nkey", you just type "cd m0nkey", not "cd /m0nkey". If you put a slash before the directory name, it means "look for this directory in the root filesystem, not in the current directory".

I hope you understand what I'm trying to explain, and let us know if that solves your problem!

---

### Post by m0nkey_magic on 2006-07-28
i understand what your saying but if just do cd 
then i get 
m0nkey@m0nkey-desktop:~$

how do i get from here to ndiswrapper-1.21
which is actually now on my desktop ....
ive tried all combinations of 
cd /ndiswrapper-1.21
cd ndiswrapper-1.21

all im getting is no such file or directory & a lot more confused by the minute !!!

---

### Post by gingermark on 2006-07-28
from your home directory do ```
cd Desktop/ndiswrapper-1.21
``` And keep in mind these things are case sensitive in Linux.

---

### Post by jayemef on 2006-07-28
When you first open a terminal, it will default to your home directory (/home/m0nkey). At any time, to see where you are in the directory tree, issue the command **pwd**, which stands for "print working directory". Doing this right after opening a terminal, you will see /home/m0nkey. Next you need to understand where things reside. Your desktop is simply a directory in your home directory, ie /home/m0nkey/Desktop. So to get to it, you could use any number of methods:
```
cd Desktop  # This is relative

# OR  
cd ~/Desktop  # This is direct

# OR
cd /home/m0nkey/Desktop  # This is direct
```
To get to ndiswrapper, you would then just append ndiswrapper-1.2.1 after Desktop.

So some notation you might not be familiar with. If you start the path with a **~**, that is a shortcut for your home directory (in this case, /home/m0nkey). So as is written in the example, ~/Desktop would be equivalent to /home/m0nkey/Desktop.

If you start the path with a /, this means you are starting at the root directory, /. Therefore, you are nolonger using relative addressing (relocating in relation to where you are). You are using direct.

I hope that sheds some light. For more info, check out this link: [http://www.talug.org/events/20030813/cmdline_tips_n_tricks_aug03.html]("http://www.talug.org/events/20030813/cmdline_tips_n_tricks_aug03.html")

---

### Post by m0nkey_magic on 2006-07-28
@jayemef

so much light infact in need shades :cool: 
many thanks ...

and @ gingermark 

works a treat m8 ...
all i was doing wrong was typing desktop without the capital D
i was typing it as it was displayed in the console as a small d

oooh well ...live & learn 

thanks for everyones help 

much appreciated 

 :D

---

### Post by punx45 on 2006-07-28
if you are still curious about how the file system works...

[http://www.december.com/unix/tutor/filesystem.html]("http://www.december.com/unix/tutor/filesystem.html")

---

