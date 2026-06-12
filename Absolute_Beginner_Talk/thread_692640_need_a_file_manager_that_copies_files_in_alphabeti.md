---
title: "need a file manager that copies files in alphabetic order"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by kaiju on 2008-02-10
i have a flash-based ums music player that displays files in a directory in the exact same order they were copied to the device.
i have been using rsync to copy files to it, because it first builds a cache and then transfers the files in perfect alphabetic order. to launch it, i made a custom command in thunar. however, this solution is not that handy as i first have to mount the disk manually before being able to copy, and also because there is always an xterm popping up as thats the only solution i could figure out for progress feedback.
i would like to know if there is a file manager that can do this sort of thing or if i could somehow integrate rsync better into thunar.

any ideas are very welcome :)

---

### Post by julian67 on 2008-02-10
Try emelfm2, a dual pane file manager which accepts terminal commands and displays the output. It can also mount/unmount disks. 

An easy solution to flash mp3 players which don't sort the tracks by name or number is to first create a folder on the player and then copy the tracks into that folder, they will automatically be sorted by name/number.   (It isn't thunar which is sorting the tracks by disk position, it's the mp3 player; lots of old flash devices do the same).

btw why do you have to mount the player manually?

---

### Post by kaiju on 2008-02-11
thanks for your reply, julian67

emelfm2 looks good, however - because of the player displaying songs in the order they were created - id need something that can actually create files in alphabetical order.
to be able to get this specific order, im using
```
xterm -e rsync -rvtW --delay-updates --modify-window=1 --progress --include='*.mp3' --include='*.ogg' --exclude='*.*' %F /media/disk/Music
```
as a custom command in thunar, thats available by clicking on directories or audio files.

this solution is fine (because i can also apply filtering, and the path to multiple files is given through a single %F) - except for the fact that i have to run rsync in an xterm for feedback. i dont know if it is possible to redirect rsyncs output to a more progress-bar like utility, e.g. using something like gmessage (but that would certainly be wicked cool) ;)

as some volume-manager-thingy automatically recognizes plugged in drives and pops them up in thunar, what i meant by having to mount manually is that i have to go for those two extra clicks in thunar to get to "mount volume". i know this is extremely lazy, but i was thinking maybe i could somehow integrate this into my rsync command and with all the little additions make it into a nice little script :)

as before, any ideas are appreciated.


edit:
i should learn to be more specific...

i need either
1) a file manager (preferably dual pane) that can create files in alphabetic order (in which case i still need to resolve filtering though), or
2) some information on how i could build on my rsync command to make it a nifty little script that integrates better with thunar.

---

### Post by kaiju on 2008-02-22
as it seems that there are no file managers respecting the order of file names in a directory when reduplicating its content on a different volume, i'm sticking with rsync.
the farthest i've gotten this far is using zenity to redirect rsync's progress output to a progress bar (the lousy part is that i haven't found a way to display file names or information on how many files are left to copy).

i'm thinking it would also be useful to read in the free space on the flash drive and compare it with the size of the rsync cache before anything gets copied, so that i can make zenity display a warning/error about there not being enough space left on the drive.
for the free space, i'm thinking of using df and then grep on the line for /media/disk (this is where the player gets mounted), filtering out the fourth field of the df output (available).
too bad that i don't know how to get rsync to report the size of its cache to be able to compare the two values :(

---

### Post by justleen on 2008-02-22
nifty solututions here! I was gonna propose Zenity, but you've already figured that out..

as for the space, i'd start splitting the command.. 
- get the size of what you've selected
- get the free space on the drive
- IF  fits on disk (rsync)    ELSE throw some more zenity around the screen

you could you "wc -l" to get the amount of files, then run a counter next to it, and you know how many files left

---

### Post by kaiju on 2008-02-22
thanks for your ideas.
i am by no means an it guy, so this will take me a couple more days to chew upon and figure out :)

---

