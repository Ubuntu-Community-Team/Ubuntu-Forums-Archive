---
title: "Dont have permission to add or delete music from my iRiver mp3 player"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by suver.17 on 2006-07-11
Hi all,
     how do I gain permission to add and delete music from my iRiver mp3 player?  This problem began when I updated to dapper drake, and I am a linux newbie.  It is basically an external hard drive/drag and drop process.  Thanks for the help.
Jared

---

### Post by catlett on 2006-07-11
If you are just dragging and dropping files and are having issues, launch nautilus as root. (nautilus is the file browser. it's what opens the window when you click on a folder) Normally you are a user when browsing with Nautilus and you have user rights.
If you launch nautilus as root, you can do anything because you have administrative rights.
Enter this command in the terminal ```
gksudo nautilus
```It will ask you for a password. Use the one you login with. Then the browser will open. Browse to your iriver icon or however it appears and you can drag in or out.

If you want a launcher on the panel to launch nautilus as root instead of having to always issue the command, you can create a launcher.
Right click on the top or bottom panel. A menu will come up, select "+ Add to Panel"
Select "custom application launcher"

Actually I am taking a screenshot of what you have to fill in. You can give it an icon by hitting on "no icon". That will open up the folder that keeps the system icons. Double click on the one you want to represent root nautilus.
[IMG]http://i80.photobucket.com/albums/j180/brthomas503/launcher.jpg[/IMG]

---

### Post by suver.17 on 2006-07-12
Awesome, thanks a lot.

Next problem...I know i have nearly 4 gig free on the mp3 player because I just cleaned it up a bit, however nautilus is still saying that I only have 12mb available and saying I don't have enough room to add files, any clue as to why this is?

The Ubuntu Community rules, 
Jared

---

