---
title: "cant delete files with a lock"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by ac1240 on 2007-09-04
i am tring to delete a folder with a lcok on that and it said i dont have the premissions 
i tried 
sudo nautilus
but the files i want to delete is not in the root system its in other hd(i have nfts write enabled there) and i cant delete all the files without the locks 
also i cant delete locked files in the desktop it says i dont have the prmissions

---

### Post by Genecks on 2007-09-04
gksudo nautilus

---

### Post by ac1240 on 2007-09-04
after doing this command i can only see the root file system hd and not the other hds

---

### Post by rbprogrammer on 2007-09-04
as long as it is not a needed file/folder for the system to work, you could just do a:
```
$ sudo rm /path/to/file
```
or if it is a folder with contents in it:
```
$ sudo rm -R /path/to/folder
```
i suggest this because you are obviously using the command line for starting nautilus, so i figured you would use the command line for your problem.

as far as:
> after doing this command i can only see the root file system hd and not the other hds
i'm not familiar with nautilus, i use KDE for my ubuntu

---

### Post by forestpixie on 2007-09-04
once you're in nautilus - do you have root and file system - open file system - then if it's another hd look in /media

---

### Post by ac1240 on 2007-09-04
i dont have any clue how to navigate between hd and desktop 
the file called 
DemoRecorder
and its on the desktop

can you pls write to me how to get to a drive 
and how to get to this DemoRecorder on the desktop

---

### Post by forestpixie on 2007-09-04
in terminal or in nautilus? in terminal the desktop is Desktop - it's case sensitive - as is everything in Linux 

so if you opened a terminal 

```
cd Desktop 

```
would get there, cd desktop would give you

```
bash: cd: desktop: No such file or directory
```

---

### Post by ac1240 on 2007-09-04
for ******* sake i just wanna delete a folder why it have to be so hard
and i cant understand your instructions 
cd Desktop
brought me to the desktop but i cant delete
pls write the all command for deleting the DemoRecorder on my desktop
plssssss i am starting to lose it

---

### Post by nowshining on 2007-09-04
do the gksudo nautilus
when it opens up do the following

DO NOT CLICK THE TOP HOME IT WILL GO TO ROOT HOME

click filesystem - home - your username - desktop

right click the file/folder you want to delete and it should be gone, anything on your desktop shouldn't be locked :(

---

### Post by ac1240 on 2007-09-04
> **nowshining said:**
> do the gksudo nautilus
when it opens up do the following

DO NOT CLICK THE TOP HOME IT WILL GO TO ROOT HOME

click filesystem - home - your username - desktop

right click the file/folder you want to delete and it should be gone, anything on your desktop shouldn't be locked :(
tyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy

---

### Post by nowshining on 2007-09-04
your welcome.. :)

---

### Post by mckryptyk on 2007-09-04
> for ******* sake i just wanna delete a folder why it have to be so hard
and i cant understand your instructions
cd Desktop
brought me to the desktop but i cant delete
pls write the all command for deleting the DemoRecorder on my desktop
plssssss i am starting to lose it


Do exactly this in your terminal:

copy and paste
```
sudo rm  ~/Desktop/DemoRec*
``` (use sudo rm -R if it won't delete)

Seriously I hope you take some time to read a little bit about how linux works for your own betterment. (or how to use gnome/your desktop)

This is the equivalent of someone using windows going "Hurrr me angrees, canno find da start button 1!1!! eleventy!!."

Cheers.

---

### Post by ThrobbingBrain66 on 2007-09-04
ac1240:

These sites will help you with any further problems you may encounter.  Bookmark them...they will be your Ubuntu bible for your first few months.
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

---

### Post by mckryptyk on 2007-09-04
> **ThrobbingBrain66 said:**
> ac1240:

These sites will help you with any further problems you may encounter.  Bookmark them...they will be your Ubuntu bible for your first few months.
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

I'm glad you posted that for him and all new users. 
I wish they would read the beginners forum Sticky Posts though.

---

### Post by itechza on 2007-09-11
Thanks Man - this was a great help!!

---

