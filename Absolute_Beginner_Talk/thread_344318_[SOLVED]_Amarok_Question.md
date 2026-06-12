---
title: "[SOLVED] Amarok Question"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by SilverDragon on 2007-01-22
Well here's my situation. In the program Amarok there are certain places where Amarok scans for your music collection. I'm trying to transfer music from my windows hard drive to my Linux one, because I dual boot off two hard drives. I was going to do this through my iPod, because I just finished burning all the DRM music onto a cd than importing it back on iTunes.

My questions are, how do I create a folder in a place where Amarok actually scans,(like my media folder) because for the most part for what I've been trying the only place where I can create a folder is on the desktop. The reason I want to do this is I can transfer the music off my iPod into that folder and than have Amarok scan it into its collection. 

My second question is, does my collection actually have a folder? or is it even stored somewhere? or does it just scan the folders you check off in the Configure Amarok > Collection option and put it on the Amarok interface where you can listen to music.

That's probably not worded that well so I'll try to explain if you have any questions :-)

---

### Post by Buck2348 on 2007-01-22
> **SilverDragon said:**
> 
My questions are, how do I create a folder in a place where Amarok actually scans,(like my media folder) because for the most part for what I've been trying the only place where I can create a folder is on the desktop. The reason I want to do this is I can transfer the music off my iPod into that folder and than have Amarok scan it into its collection. 

My second question is, does my collection actually have a folder? or is it even stored somewhere? or does it just scan the folders you check off in the Configure Amarok > Collection option and put it on the Amarok interface where you can listen to music.

That's probably not worded that well so I'll try to explain if you have any questions :-)

I would suggest creating folders for any personal files somewhere in /home/SilverDragon.  Desktop is at /home/SilverDragon/Desktop.  I've never had Amarok create a music library, but I think it's safe to say, if I understand your question, that Amarok just indexes your music files and does not copy them to another directory.

Buck

---

### Post by sumguy231 on 2007-01-22
> **SilverDragon said:**
>  or does it just scan the folders you check off in the Configure Amarok > Collection option and put it on the Amarok interface where you can listen to music.


Yes, it monitors those folders and then adds anything in them to your collection. By default it works recursively so if you checked a folder entitled 'music' for example, everything inside folders inside 'music' is also added. Just put that music somewhere in your existing collection folders, or make a new one and add the folder to your collection. To create a new folder, just right-click in Konqueror and go to Create New -> Folder. (Assuming you're using KDE, of course.)

---

### Post by SilverDragon on 2007-01-23
Well I can make a folder in /home, but Amarok doesn't scan there for my music collection. I tried making a folder and than moving to to /media, but the error message saying :

"You do not have permissions to write to that folder." 

appears. I was thinking I think I have to be in as a root somehow and then I'll have access to do this. If that's a solution, how would I do this? The main reason for this as I said, was to transfer music off the ipod into that folder and than have it scanned into my collection for convenience reasons :-)

---

### Post by Pathfinder_ on 2007-01-23
you used to use amarok when i used kde but now i use gnome. anyway i think that in amarok options u can specify in which folders it looks for music. i don't know exactly where it is since i don't use it but i know its there. so just create a folder in ur home directory, put msic there and in amarok options make sure that it check that folder for music.

---

### Post by SilverDragon on 2007-01-23
Well I tried dragging and dropping the files from my iPod into the folder but it would either not work at all or only get to song 121 before just stopping. As a result, I just went straight to the iPod itself and copied it.

Now I'm using Easytag to change the names back to how they look normally.

Oh and ya you were right, I just didn't look hard enough under the Configure Amarok option to find it. So I just put a Music folder under Home like you said :-)

---

