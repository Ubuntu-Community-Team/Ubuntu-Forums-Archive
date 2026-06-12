---
title: "Directories Vanish from USB External HD"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by mikelucasiscool on 2007-08-05
Several of my directories just suddenly disappeared from my external HD and i have no idea how to recover them in linux, i do not believe they were deleted, rather i believe that partition table lost track of them or something, they are still there eating up data because i have checked the file sizes and there is the unaccounted for memory usage that matches up with the missing directories, (over 30gb) how can i tell linux to try to auto correct this issue something like a chkdsk for linux? any ideas? i am a complete noob to the linux command line :( please help

- T4ct1cs

---

### Post by jnorthr on 2007-08-05
Can you see any of your directories with a command line 'ls -al' the 'ls' shows directory contents so do this from the root of your usb mount point. The  -a should show all folders and files withinh your directory. Have you changed the permisisons of any folders recently, say to make them read-only ?

---

### Post by mikelucasiscool on 2007-08-05
Yes yes i can see them all there! 

No i have not changed permissions on them though :S. 

How can i recover them?

- T4ct1cs

---

### Post by mikelucasiscool on 2007-08-06
Some one anyone are you listening? Help i know this is a simple command, i'm sure of it i just don't know any linux based command line commands :S arghhh!

- T4ct1cs

---

### Post by lgambett on 2007-08-06
The command you are looking for is fsck, but I don't think that a thing like "partition table lost track of them" can really happen. I do not understand; you said that  ls -la shows your directories and files ? Check it again...

---

### Post by zxccvb on 2007-08-06
Did you use ntfs-config. It happens to me too.
Still don't know ahow to solve it beside unmount and remount the external drve.
Pretty annoying.

---

### Post by mikelucasiscool on 2007-08-06
Per everyones advice this is what i get

The files do not show up under Konqueror, or under windows explorer they only show listed under ls -a in console but are still using memory, i want these folders and the files in them back :S

I got this window by opening my HD under Konqueror and right clicking the background and choosing open terminal window here...

t4ct1cs@Ph34rTh3P3ngu1n:/media/My Book$ ls -a
.                        For Others            Programs and Installation Files
..                       Ktorrent back         Projects
Anime                    LucasG.ico            Recycled
a.txt                    Memory stick          System Volume Information
a.txt~                   memstick2             Thumbs.db
ccna                     MUSIC UNFILTERED YET  Unsort
DEMONIOD LIST TO DL.txt  My Movies             Updates.txt
Favorites                My Music Videos       Updates.txt~
Fedora-7-i386            My Pictures           $vault$.avg
t4ct1cs@Ph34rTh3P3ngu1n:/media/My Book$ cd anime

// as you can see anime is still a working directory (it also shows up under konqueror//
//now to try a dir that only shows up in the terminal window//

t4ct1cs@Ph34rTh3P3ngu1n:/media/My Book/anime$ cd ..
t4ct1cs@Ph34rTh3P3ngu1n:/media/My Book$ cd memstick2
bash: cd: memstick2: Input/output error

//ok so that didn't work//
//trying the fsck command...//

t4ct1cs@Ph34rTh3P3ngu1n:/media/My Book$ fsck
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/sda2 is mounted.

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.

//ok that looks scarey lets save that as a last option//
//try the ntfs config option..//

t4ct1cs@Ph34rTh3P3ngu1n:/media/My Book$
t4ct1cs@Ph34rTh3P3ngu1n:/media/My Book$ ntfs-config

** (ntfs-config:5807): WARNING **: Error : This programm need to be run as root.


X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

//ok since i opened this the way i did, i have no clue how to open one in the same place as root, i tried to open a root console and then navigate my way to the dir, however the name "My Book" has spaces in it... so it kept telling me there was no /media/my dir... finally gave up on that also.//

Any ideas anyone?

- T4ct1cs

ps this looks great in the comments window, sorry about the folder names being mashed together in the final product don't know how to fix that :S

---

### Post by mikelucasiscool on 2007-08-06
Oh yes the mount and unmount thing, closest i could try to that was to right click my drive and click safely remove, it does it unmounting thing then i unplug and replug the usb hd, doesn't seem to make any difference though.

- T4ct1cs

---

### Post by mikelucasiscool on 2007-08-09
Anyone alive? i haven't gotten any response since i posed the exact issue, i still don't have any way to get at my files... help :(

- T4ct1cs

---

