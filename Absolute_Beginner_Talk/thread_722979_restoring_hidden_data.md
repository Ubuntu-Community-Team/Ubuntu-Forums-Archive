---
title: "restoring hidden data?"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by RyviusRan on 2008-03-13
I just reinstalled ubuntu and found in the lost+found folder that it hides over 95 GB of files.

that led me to believe that is where all my old data is but it won't let me access the file at all.

when I used windows before I remember having to go through profile settings and somehow unlock it that way.

Does anyone know how to do it with Ubuntu?

---

### Post by joshrobinson on 2008-03-13
95bg of files!? wow, wonder how they all got in there.. you can look through the folder and copy out what files you want

```
sudo nautilus
``` 
this will open a root version of nautilus, and will let you look through the lost and found folder, then just copy and paste what you want out of the folder to wherever you want it
you will probably need to change the permissions of the files you copy though, as they will be root files

---

### Post by RyviusRan on 2008-03-13
and how do i change the permissions?

---

### Post by RyviusRan on 2008-03-13
wait a sec sorry I guessed wrong. it says I have 95 gb of free space.

all in all I should have 215 gb of free space with it clean.

that means the rest is hiding somewhere.....hmmm

I wonder where i can find it?

---

### Post by joshrobinson on 2008-03-13
while in root nautilus, right click the file and go to the permissions tab, and set the user to your username

---

### Post by RyviusRan on 2008-03-13
is there any program that can search for folders by amount of data alone.

I have about 120 gb of space taken up and I can't find where all that data is?

---

### Post by oedha on 2008-03-13
you can see the hidden things from nautilus by pressing ctrl+h
if you can delete or do something on it.....you can change the permission or the owner of those........by using chmod and or chown :)

---

### Post by RyviusRan on 2008-03-13
but I believe when my HDD was supposed to be wiped clean it wasn't and the old data is hidden somewhere know I need to find out where it went....

that is what I need help with I need somehow to be able to find the folder with 120gb

---

### Post by joshrobinson on 2008-03-13
it all depends on how you partitioned the drive try this..
 system > administration > system monitor
click the file systems tab

it should say /dev/hda1 then total free and avail. space
is /dev/hda1 your only drive listed there? (besides nfsd)

---

### Post by RyviusRan on 2008-03-13
i have 2 

/dev/sda1 

/dev/sda3

looks like that is what split my memory 

anyway I can combine them or use them both?

---

### Post by RyviusRan on 2008-03-13
I can't seem to access one of them

---

### Post by joshrobinson on 2008-03-13
what are the mount points for /dev/sda1 and /dev/sda3?
it should say in the directory column

sda1  / ?
sda3 /home?

---

### Post by RyviusRan on 2008-03-13
one is dev/sda1/

the other is dev/sda3/media/disk

---

### Post by joshrobinson on 2008-03-13
> **RyviusRan said:**
> one is dev/sda1/

the other is dev/sda3/media/disk

click places on your top panel, is "disk" in that list? click that, and see if anything on that drive/partition. you can always use that to store personal files. it will stay safe from reinstaling your system as long as you dont chose to format it

---

### Post by RyviusRan on 2008-03-13
ok I guess I have two spots with free space they are just separated.

though while I am still posting here and to safe space I will ask one more question.

I recently updated my ubuntu with 199 files 

compiz was one there.

only problem is that it doesn't show up in system

I even tried 

sudo apt-get install compiz

---

### Post by joshrobinson on 2008-03-13
compiz is an application that you really dont see in the menu's etc. but is probably installed, linux applications are mostly small in size, so your personal data will take up more space then the programs you have installed

---

### Post by RyviusRan on 2008-03-13
but i am saying compiz seems not to be working becuase when I go into appearance it doesn't show up I don;t have the customize option

---

### Post by joshrobinson on 2008-03-13
so compiz was running before the update ? have you restarted after the update? maybe something went goofy?

i never actually the custom options in appearance  i always started it with my own script, or now [fusion-icon]("http://neoaddict.wordpress.com/2007/11/03/getting-fusion-icon/")

you can always try installing fusion icon at the link above and starting it that way

---

### Post by RyviusRan on 2008-03-13
I found that compiz is in the other drive labeled disk.

for some reason my computer isn't picking it up though

---

### Post by RyviusRan on 2008-03-13
actually let me give you a better story.

I did already have ubuntu installed once, but I received a kernel panic error and was too lazy to try to fix it.

so I re installed ubuntu

I guess when I reinstalled ubuntu it seperated my old data from the newly installed version.

now I wonder how i can get it so the computer reads that it is in that separate area.

---

### Post by joshrobinson on 2008-03-13
anything on your /media/disk    drive/partition isnt being noticed by ubuntu, its just sitting there as files

---

### Post by RyviusRan on 2008-03-13
yes and i need to find out how to either combine them or make them get noticed

---

### Post by forestpixie on 2008-03-13
if you've reinstalled then I would guess that the files in the 'old' partition that you can see are always going to be unused - they're just files now

if you haven't got the custom desktop effects - you need to make sure you have 
1 - got the graphic driver installed
2 - install the compiz settings manager

sudo apt-get install compizconfig-settings-manager

Edit - do a whereis in terminal
whereis compiz

what does it say - should be similar to 
compiz: /usr/bin/compiz.real /usr/bin/compiz /usr/lib/compiz /usr/include/compiz /usr/share/compiz /usr/share/man/man1/compiz.1.gz

---

