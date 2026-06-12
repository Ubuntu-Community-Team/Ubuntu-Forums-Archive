---
title: "wireless problems"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by dark22horse on 2006-05-10
hi, i have just managed to install linux, im not sure how i managed it, but i dont know how to do any thing, ive tried looking, but im feeling stupid and cant find it. Can any1 take me through step by step. how to install my wireless card so i can use the net on it! 

thanks

---

### Post by dark22horse on 2006-05-10
says e: couldnt find package ndiswrapper 

its on the desktop on linux

---

### Post by relevantrhino on 2006-05-10
how do you "type in the console".  I am a windows user that  understands the concept of running commands when going to START>RUN and typing in a command such as CMD, but don't see anything like this in ubuntu.

---

### Post by dark22horse on 2006-05-10
far as i know, its called terminal appl>acc>terminal

---

### Post by relevantrhino on 2006-05-10
I am seeing nothing called terminal under Applications, places or System?

---

### Post by dark22horse on 2006-05-10
u need to open appl> then accesories> terminal is there

---

### Post by relevantrhino on 2006-05-10
What in the world is APPL?

---

### Post by sefs on 2006-05-10
Hi I have the CNET CWD-584 which uses the rt73 Ralink chipset.  And this is what I did to get my card working with ndiswrapper.  You can probably do the same but substitue your network card.

Assumption: that your usnername is myusername (substitute for your own username)


1) I created a driectory in my home directory like so:
   $ mkdir /home/myusername/drivers
   $ mkdir /home/myusername/drivers/wireless-drivers

2) some how you have to get the windows drivers off the cd that came with your card.  I installed
   mine on a windows machine and copied them off ... the files you should be looking to get are 2
   files in particular.  a .inf file and a .sys file.  but to be on the safe side i also copied over
   the .cat and .bin file from the installation on the windows machine.  Copy all these files
   to the /home/myusername/drivers/wireless-drivers

4) Install ndiswrapper.  Go to: system -> Administration -> Synatic Package Manager 
   Click on the searh button and type in ndiswrapper.
   if it is installed already (the squre next to it would be green) then uninstall it.
   if it is not installed then do not install it.

5) go here... [http://www.ubuntuforums.org/showthread.php?t=104539&highlight=ndiswrapper+1.7](http://www.ubuntuforums.org/showthread.php?t=104539&highlight=ndiswrapper+1.7)
   read the post by foxy123 and follow it exactly. (it's the first post)

6) after you successfully installed ndiswrapper go here ... [http://users.ox.ac.uk/~orie1330/linuxnotes.html](http://users.ox.ac.uk/~orie1330/linuxnotes.html)  and follow the steps under wireless. 

7) That should get you a pretty good way up and running I hope.  You may need to play around after that.

---

### Post by dark22horse on 2006-05-10
k mate will try, cheers for the help, post soon to tell if it worked

---

### Post by dark22horse on 2006-05-10
cant get the files, i got a linksys wusb54gv4 ive installed it, but i cant find the fikles

---

### Post by sefs on 2006-05-10
You must get to the device driver manger in 2000 or xp or whaterever you did your install on.

next look down to see the network card branch

expand it

identify your card under this branch

right click on it and properties i think

a box pops up

click on drivers tab in this box

then somewehre in there it should show you the files installed for this device and where they are installed.

look for the bin, sys and inf file to see if they are listed there then go get um, and copy them to diskette or something.

I am speaking from memormy so you'll have to fiddle.

let us know how you get thru.

---

### Post by dark22horse on 2006-05-10
k, got the files, but now stuck on the next bit, 

1. Install kernel headers:

Code:
sudo apt-get install linux-headers-$(uname -r)and dependencies:

Code:
sudo apt-get install dh-make fakeroot gcc-3.4 build-essential

do i type these in one after another? or type then enter?

---

### Post by sefs on 2006-05-10
After each command you have to hit enter... so one at a time.

First command to enter at prompt
------------------------------------------
sudo apt-get install linux-headers-$(uname -r)

Second command to enter at prompt
------------------------------------------
sudo apt-get install dh-make fakeroot gcc-3.4 build-essential


Download ndiswrapper from link in that post to a directory in your home direcorty of your choice


change to direcotry you downloaded nidwarpper too


Third command 
-------------------------------------------------
tar xvfz ndiswrapper-[current version].tar.gz

Fourth command
--------------------------------------
cd ndiswrapper-[current version]


fifth command
-------------------------------------------
fakeroot debian/rules binary-modules

sixth command
-----------------------------------------------
fakeroot debian/rules binary-utils

seventh command
------------------------------------------------
cd ..

8th command
----------------------------------------
sudo dpkg -i ndiswrapper-modules-[your kernel]_[current version]-1_i386.deb ndiswrapper-utils_[current version]-1_i386.deb



That should be it for installing ndiswrapper.

---

### Post by dark22horse on 2006-05-10
how do u change directory? got the first bits workign

---

### Post by sefs on 2006-05-10
use the cd command 

for instance if you had a directory in your home directory calle abra you could change to it by going

cd /home/myusernamehere/abra

something like that....

thats just one of the many examples of using cd though.

like you can go up one directory by going ...

cd ..

ect ... its almost similar to the dos cd command

---

### Post by dark22horse on 2006-05-10
i think i mite give up, i typed cd/home/keith/drivers no such file or dir

---

### Post by sefs on 2006-05-10
did you use the mkdir command to create the directories ahead of time?

you have to 

mkdir /home/keith/drivers

cd /home/keith/drivers

mkdir wireless-drivers

(just so things are organised nicely)

so then you can copy all files to /home/keith/drivers/wireless-drivers

also were currently are the wireless driver files that you got from windows?

---

### Post by dark22horse on 2006-05-10
i didnt, but they have been created, i got a few more now, in the same place

---

### Post by dark22horse on 2006-05-10
k got that working, but still no luck with the commands, 

cd /home folder/keith/ndiswrapper-1.16

is where it is, is that rite, cause it isnt working

---

### Post by sefs on 2006-05-10
[QUOTE=relevantrhino]What in the world is APPL?[/QUOTE]

Applications -> Accessories -> Terminal

---

### Post by sefs on 2006-05-10
[QUOTE=dark22horse]k got that working, but still no luck with the commands, 

cd /home folder/keith/ndiswrapper-1.16

is where it is, is that rite, cause it isnt working[/QUOTE]

what have you done so far?

Are you trying to find out where you have downloaded the ndiswrapper too?

or have you untared it alread?

To be sure we are moving logically here they are 3 giant steps

1) get the windows drivers unto the ubuntu machine in a directory

2) download and install ndiswrapper

3) confirgure the network card

Have you done 1) and are now at 2) ?

---

### Post by dark22horse on 2006-05-10
well ive dled it to /keith/home folder/ndis......

but i havent untarred it yet

i havetried running the command after goign to keith/home folder/ndis.....

stuck on installing it

cheers for ur help, im rubbish!

---

### Post by sefs on 2006-05-10
[QUOTE=dark22horse]well ive dled it to /keith/home folder/ndis......

but i havent untarred it yet

i havetried running the command after goign to keith/home folder/ndis.....

stuck on installing it

cheers for ur help, im rubbish![/QUOTE]


you have to be specific .....

/keith/home folder/ndis......  <--- i doubt this location exists anywhere on your computer.

you more like mean /home/keith/<somediretory here>

you need to 

cd /home/keith

ls

and look at the files in there to see if thats where you downloaded the nidswrapper file too.

or you can search for it by going....

places -> search for files

and in the "Name contains" field put ndis and click on find.

if you have yahoo messenger you can send me a message at cliffhangerbb

---

### Post by dark22horse on 2006-05-10
i have the file ndis.. in a folder named ndiswrapper-1.16, this is in home folder/keith/ndiswrapper-1.16

---

### Post by sefs on 2006-05-10
[QUOTE=dark22horse]i have the file ndis.. in a folder named ndiswrapper-1.16, this is in home folder/keith/ndiswrapper-1.16[/QUOTE]

the command to get to that directory is ...

cd /home/keith/ndiswrapper-1.16


in there should be your tar file

---

### Post by dark22horse on 2006-05-11
any one else like to help me? still having problems

---

