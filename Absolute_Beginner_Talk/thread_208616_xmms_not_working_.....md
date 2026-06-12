---
title: "xmms not working ...."
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by mourad on 2006-07-03
I have install automatix, and everyting was working good, i used to open the streamtuner and chose my station and then it is played in xmms, till suddenly i was doing my regualer job, but xmms does not want to open, and i noticed that my cpu monitor reaches 100% busy, and when i look in the processes I find Xmms "sleeping", i try to end processes but it doesn't respond, I unistalled the xmms using aptitude, and then reinstalled using aptitude, and the restarted my computer, but the same problem exists, I tried the synaptic to reinstall , but the same problem exists .....

Any help of what is going on here, and how to help solve it ???? :confused: :confused: :confused: :confused: 

I am dying here not able to listen to my favorite stattion :cry: :cry: :cry: :cry:

---

### Post by woedend on 2006-07-03
if you cannot get xmms to open, you should probably rename your .xmms directory(in your home folder).  
/home/yourusername/.xmms
you must choose to show hidden folders to see it naturally.  I would name it .xmms_backup.  Then when you launch xmms see if it works(hopefully it will).  It will automatically create a new .xmms.  The reason I say to rename instead of deleting the folder because that folder contains your settings for xmms, and if this doesnt fix the problem, you can easily restore the folder by renaming it back to .xmms.

---

### Post by mourad on 2006-07-03
[QUOTE=woedend]if you cannot get xmms to open, you should probably rename your .xmms directory(in your home folder).  
/home/yourusername/.xmms
you must choose to show hidden folders to see it naturally.  I would name it .xmms_backup.  Then when you launch xmms see if it works(hopefully it will).  It will automatically create a new .xmms.  The reason I say to rename instead of deleting the folder because that folder contains your settings for xmms, and if this doesnt fix the problem, you can easily restore the folder by renaming it back to .xmms.[/QUOTE]

Thanks so much Woedend ... I worked in a way ... let me rephrase this, it opened alone, and with streamtuner, but in the same interface size .... When I tried to view it with the double size option as I am used to, it freezed, yet the music still going on, but it did not max to the double size .....

The point is, i really want to know how renaming the .xmms fixed the problem, actually what was the problem ??? and if there is no solution for the freezing issue when maximizing , I can live with the same size, at least it is working and I am able to listen to the music back again ....\\:D/ \\:D/ \\:D/

---

### Post by woedend on 2006-07-03
.xmms(or .anything for that matter in your home directory) stores settings.  So say you really made a bad choice about a setting, or a setting became corrupt, when xmms starts and tries to use whichever setting it was, it simply doesnt work.  by removing/renaming .xmms, xmms thinks its the first time you are running it and starts anew.
not sure which setting was actually broken for you.  But keep this in mind for future apps, its helpful :)

---

