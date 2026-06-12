---
title: "Running your own scripts"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by apjone on 2005-11-21
Hi just a quick word.when writting a script remmeber to put
#! /bin/bash

if you want to run the script like you run 'ls' or 'cd' then 

chmod 755 myscript

sudo cp myscript /usr/local/bin

i always cp, this is because you have a copy of the script to work on and test before having others use it. below is a quick script i use to play music on my text online terminal. 


 #! /bin/bash
#PLAY - apjone
#plays music from Music on disk 1 using music123 and mpg123

#jump to home Dir
cd

#looks to see if the file '.test' exists

if [ -f .test ] ; then
#if file exist then
        echo "music123 is already playing. If not then run 'rm /home/username/.test"
        exit 1; # exit 1 denotes error 
else
#if it dosen't exist
        nohup music123 -r -q -z /media/hdb1/Music &
        touch .test
        exit 0; # exit 0 denotes no errors
fi # ends the if statement

---

### Post by davmac on 2005-11-26
Hi apjone,

Instead of copying the script to /usr/local/bin, I create a symbolic link by typing "sudo ln -s myscriptname /usr/local/bin".

Aside from taking up less space it means that any changes to your original script immediately get picked up.

Of course the advantage of your way is that you can independently work on enhancing your script without impacting on the earlier version you know you've got working.

Regards,

Dave Mac

---

