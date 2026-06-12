---
title: "Filetype changes when icon is clicked"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by toadliy on 2008-01-21
Hi,
I'm running Gutsy and have been having this issue for a while where the filetype of a given file will change when I click its icon, and then the file can't be opened because it's no longer associated with any programs. Both the file's icon and properties change to fit its new filetype, but the file reverts to its original state once the computer is restarted and works fine again. I had assumed this was an issue with Nautilus, so I switched to Thunar yesterday (I'd been wanting a more lightweight file manager anyway), but the problem persists. The only difference is that with Nautilus the files would change to program files, and now under Thunar they become 'unknown' files.

It seems unlikely that Nautilus and Thunar would both have the same bug, which leads me to believe that the issue might be with Gnome rather than the file manager. Has anyone found a fix for this, or can at least offer some suggestions? Thanks.

---

### Post by Kulgan on 2008-01-21
Could you give a more precise example? Is it only with certain file-types, or with all files? Sometimes if part of a file is missing, as with incomplete torrents, they won't be recognised, but I haven't heard of it happening with other files....

---

### Post by toadliy on 2008-01-21
No, these are complete files. It happens with any and all files--mp3, png, txt, odt, you name it. For instance, I might click on an audio file and inexplicably the icon changes from a music note to what looks like a blank sheet of paper blowing in the wind, and it can't be opened with any programs. If you look at the document's properties, it lists the file type as unknown, even though the file's extension hasn't changed. Once this starts happening, it will do this to every file I click on, regardless of type or the directory of the file. I think it's triggered by extensive file browsing. There's a possibility that it's caused by something wrong with one of gnome's icon libraries (I've experienced problems with them before), but I really don't know.

---

### Post by mikeyphi on 2008-01-21
Right-click on suspect files - check under Properties/Open with.......perhaps some of your file types have somehow got associated with the wrong program.

---

### Post by Kulgan on 2008-01-21
Now that's strange... That usually only happens when the file's extention doesn't match up with the mime type - but you say it doesn't even list a type in the properties... 

I'm sorry to say I have no idea. You should probably post the issue over in the [Desktop Environments]("http://ubuntuforums.org/forumdisplay.php?f=132") section, or on Gnome's forums.

---

### Post by toadliy on 2008-01-21
mikeyphi: That doesn't seem to be the issue... The program associations for each file type are fine. When the bug shows up, the file type itself changes (and with it the program associations) even though all I've done is select the file's icon with the mouse. Plus, everything goes back to normal on a restart.

Kulgan: Thank you anyway, I appreciate your help.

---

