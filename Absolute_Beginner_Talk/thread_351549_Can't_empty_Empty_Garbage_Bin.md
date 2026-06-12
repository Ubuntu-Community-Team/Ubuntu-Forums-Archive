---
title: "Can't empty Empty Garbage Bin"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by psi36 on 2007-02-02
I try to empty my garbage bin, but I get an error (pop-up):

```
Error while deleting.
"/xxx/yyy.zzz" cannot be deleted because you do not have permissions to modify it's parent folder.
```

I tried starting nautilus as root, but there I don't have the option to empty my garbage bin (it's greyed out).

Problem is I can't empty my usb stick, cause there's still files in it's .trash.

---

### Post by Archmage on 2007-02-02
Strange.

Try this (warning, make sure you enter the right name)

```

sudo rm .Trash-USERNAME -r

```

(normaly you can just hit TAB after entering "sudo rm .Trash" and the bash will automatical insert the right name for the folder just add " -r" to it.)

---

### Post by psi36 on 2007-02-02
That doesn't work.
When I sudo rm .Trash and press TAB, I only get the name of a foder in trash and when I just sudo rm .Trash -r in my home dir that doesn't solve the problem either

---

### Post by phossal on 2007-02-02
Using nautilus, drag the files out on to your desktop. Then do:
```
sudo rm -r *filename*
```
Or simply change their permissions. 
```
sudo chown YOUR_USER_NAME *FileName*
```
Then delete them like normal.

---

### Post by psi36 on 2007-02-04
If I try to cut and paste those files out of my trash I get the same error: 
""xxx/yyy.zzz" cannot be moved because you do not have permissions to change it or its parent folder." 

The files are just copied to the desktop. I can delete those copied files, but the ones in my trash aren't gone. 

Same thing if I just drag and drop.

And if I sudo nautilus my trash folder is empty. Not only my root trash folder, but also the folder /home/*myusername*/.Trash

---

### Post by phossal on 2007-02-04
```
**[COLOR="Red"]sudo[/COLOR]** nautilus
```
Then delete them.

[EDIT] When you click to open the trash folder, there are files in it? But when you use sudo nautilus, it's empty? Huh?

---

### Post by psi36 on 2007-02-04
> **phossal said:**
> [EDIT] When you click to open the trash folder, there are files in it? But when you use sudo nautilus, it's empty? Huh?

Exactly that's the porblem. 
If I sudo my trash can is empty.

[[IMG]http://zonk.be/img/garbage_bin_tbn.png[/IMG]]("http://zonk.be/img/garbage_bin.png")

---

### Post by bg1256 on 2007-02-04
I've had the same problem.

Enter into the garbage bin, right click on the file that won't delete, then properties, then permissions, then make sure you have permission to read /write / execute the file.  Once you have all those boxes checked, click ok.  Then right click the file and delete.  All should work.

---

### Post by shareMenaPeace on 2007-02-04
Click "view" and "Show hidden files" in the trash window.

---

### Post by bg1256 on 2007-02-04
> **shareMenaPeace said:**
> Click "view" and "Show hidden files" in the trash window.

keyboard shortcut = ctrl+h :)

---

### Post by psi36 on 2007-02-04
Already tried "show hidden files".

And I can't change the permissions of the files, cause they're owned by root. 

And since I can't see the files as root I can't change the permissions or delete them...

---

### Post by phossal on 2007-02-04
```
sudo rm -r ~/.Trash/*
```
If that really doesn't work. Remove the applet. Issue the command again. Restart. Login as you. Add your trash applet back. By the way, are you running beryl?

---

### Post by phossal on 2007-02-04
Here is another way I might try:
```
sudo slocate -u 
slocate *bleep-109520*
```

Then delete all the files in the path of *bleep-109520*. For example, if *slocate *bleep-109520** returns */home/dimi/.Trash/bleep-109520* then I really *am* going to delete everything this way:
```
sudo rm -r /home/dimi/.Trash/*
```

---

### Post by maestrobwh1 on 2007-02-14
I know with kubuntu, I assume a similar directory structure, my user trash is a different directory than my root trash.  My root trash will be empty, but you need to go to home/youruserid/.local/Share/Trash/files (there is another directory next to /files in Trash there called "info" so I sometimes find I need to go in there and clean it out... although I generally need to reboot, or just toss a random file in trash (not from root!), to get the icon to show full or empty.

I sometimes get crap I can't empty.  It annoyes me, although I can just use a file manager in root mode and go to that folder.

I use Thunar (sudo thunar) in root mode when I have such issues.  It is nice and smiple.  I like Krusader for KDE, but it is just too busy at times.

---

### Post by phossal on 2007-02-14
I tested this a lot. If you delete files from the trash file from the command line, without using the applet, it screws up the icon display of the applet. If right-clicking the trash container and emptying the trash doesn't work, just remove the applet from the panel and add a "new" one.

---

### Post by gregb49 on 2007-02-21
Thank for the > sudo thunarsuggestion. I had been using > sudo konquerorin KUBUNTU, which is a bit flaky, to remove the .trash folder from my MP3 hardware. Greg

---

### Post by doghi on 2007-02-21
Hi there!

I would like to come back to the point, that with sudo nautilus the trash is empty, because I am having the exact problem and didn't find any hint throughout the last few days. Maybe someone here can bring some enlightment to me?!

ciao,guido.

---

### Post by phossal on 2007-02-21
Remove the applet from the panel. Then add it back again.

> **phossal said:**
> I tested this a lot. If you delete files from the trash file from the command line, without using the applet, it screws up the icon display of the applet. If right-clicking the trash container and emptying the trash doesn't work, just remove the applet from the panel and add a "new" one.

---

### Post by doghi on 2007-02-22
OK, I've tried that, but no effect!

Maybe that helps: The files that my trash displays are all physically located in the /boot folder, and are all owned by root (as should be)!

ciao,guido.

---

### Post by crysys on 2007-02-27
> **phossal said:**
> Remove the applet from the panel. Then add it back again.

I'm using Kubuntu Edgy and this worked for me, thank you.

Also, yes I did just install Beryl right before this problem cropped up.

---

### Post by aysiu on 2007-02-27
> **doghi said:**
> OK, I've tried that, but no effect!

Maybe that helps: The files that my trash displays are all physically located in the /boot folder, and are all owned by root (as should be)!

ciao,guido.
Alt-F2 and ```
gksudo nautilus
``` should allow you to delete any file. Just keep in mind that when you launch Nautilus as root, the trash you see in the window is /root/.Trash and not /home/doghi/.Trash

So you'll have to navigate directly to /home/doghi/.Trash to see those files and delete them. You may also have to enable through Edit > Preferences the ability to delete files (instead of just moving them to root's trash).

---

### Post by doghi on 2007-02-27
> **aysiu said:**
> Alt-F2 and ```
gksudo nautilus
``` should allow you to delete any file. Just keep in mind that when you launch Nautilus as root, the trash you see in the window is /root/.Trash and not /home/doghi/.Trash

So you'll have to navigate directly to /home/doghi/.Trash to see those files and delete them. You may also have to enable through Edit > Preferences the ability to delete files (instead of just moving them to root's trash).

OK, maybe I didn't make that quite clear: I've got the Buh!-effect that, if I open the Trash /home/guido/.Trash via gksudo, it's empty!!! Only when opening the Trash as user, I see the content of the /boot directory inside the Trash. The properties say, that the files are located in /boot and are owned by root, which is the reason, why I get the 'no rights' error, when trying to empty the trash.
Oh and by the way, yes I'm running beryl, but what's wrong with that?

---

### Post by doghi on 2007-03-05
Bump!

---

### Post by mab1151 on 2007-03-12
I have the same problem which developed last night after deleting some obsolete .tar files. After playing with various things apparantly without success - suddenly the trash bin showed empty (for no reason it seemed), at which point I closed down! This morning it is showing full again - it shows 31 items in trash, if I delete a fresh file the trash count goes up by 1 - if I then empty the trash the count goes back to 31 - and I get the same error as others in this thread if I try to delete any more. I have worked through all the suggestions in this thread with no effect ........ Help!!!!!!

---

### Post by mab1151 on 2007-03-12
> **mab1151 said:**
> I have the same problem which developed last night after deleting some obsolete .tar files. After playing with various things apparantly without success - suddenly the trash bin showed empty (for no reason it seemed), at which point I closed down! This morning it is showing full again - it shows 31 items in trash, if I delete a fresh file the trash count goes up by 1 - if I then empty the trash the count goes back to 31 - and I get the same error as others in this thread if I try to delete any more. I have worked through all the suggestions in this thread with no effect ........ Help!!!!!!

I have done some more investigation on this - passing on my findings as it may help someone else...

I opened the .trash folder using the aplet - the first files in the folder were actually directories created by the .tar files when they were extracted - these seem to be the cause of the problem, I found that I could manually delete the .tar files themselves from trash, but not the extracted folders, having deleted all the .tar files and a few others that were also in the trash folder I was left with the extracted folders only - and I found that I could manually delete all the files from these folders but NOT the folders or sub-folders themselves, however this now left 7 empty folders in trash! In pure desperation I tried cutting and pasting one of thes folders to the desktop - it worked - gone out of trash - I now tried one of the above suggestions from root terminal:

sudo rm -r filename

and lo behold the directories disappeared. Repeated with all the other rogue directories and all is now well, trash is empty and stayed empty after restart.

Very new to the operating system (although I was involved briefly with some unix machines about 12 years ago) so can't imagine what is going on, but my problem is solved - couldn't have done it without info gleaned here!!

---

### Post by Gorbachev on 2007-03-25
> **phossal said:**
> ```
sudo rm -r ~/.Trash/*
```
If that really doesn't work. Remove the applet. Issue the command again. Restart. Login as you. Add your trash applet back. By the way, are you running beryl?

I'm sorry if this is thread revival, but I just wanted to share with everyone that I had this problem and the above command worked. Also, I am running beryl.

Thanks!! :)

---

### Post by lamalex on 2007-03-25
my prefered way is
```

cd .Trash/
sudo rm *

```
works like a CHARM.

---

### Post by andybleaden on 2007-04-19
manually delete all the files from these folders but NOT the folders or sub-folders themselves, however this now left 7 empty folders in trash! In pure desperation I tried cutting and pasting one of thes folders to the desktop - it worked - gone out of trash - I now tried one of the above suggestions from root terminal:

sudo rm -r filename

and lo behold the directories disappeared. Repeated with all the other rogue directories and all is now well, trash is empty and stayed empty after restart.



This worked for me thanks very much!!

---

### Post by panache on 2007-10-08
Hey
Old thread i know, but i stumbled across it after encountering similar problems. None of the solutions above worked for me until...
i realised that the files showing up in the garbage bin applet had been deleted from a fat32 windows partition. The files were actually located in a .Trash-USERNAME folder in /media/xxxx/.Trash-USERNAME. If you have a similar problem:
cd to this folder (where xxxx is the relevant mounted disk, and USERNAME is your username)
use the ls command to list the files containted in the trash folder
sudo rm -r filename to delete the pesky files (where filename is one of the folders found using ls)
hope this helps someone
sam

---

