---
title: "Can you help me?."
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by vaharim on 2006-01-25
Hi, I am absolutely new to linux and I have a bit of a problem.
The description will be a bit long but I want to explain as much detail as posible.
I have been a windows user all my life but one month ago my windows installation just wouldn't start, so I decided to use one of my disks to install linux and I decided to give a try to ubuntu, I have installed ubuntu in half of a disk and in the other half I have a vFAT partition.
Yesterday I downloaded some pictures to the vFAT partition through ubuntu with the intention of making a back up DVD, today I opened a window for the DVD burner and copied all the pictures there, the pictures were in a folder which contained another 3 folders, when I was going to try and burn them to the DVD I realized the file was to big so I dragged the folder back to the vFAT partition and a dialogue appeared saying that those files were already in the disk and if I wanted them to be replaced I cliked "no" and next thing I know, both the pictures in the vFAT partion and the ones in the window for the DVD burner are gone but the main folder and the other three folders inside it are still on there, only the contents are gone, the wastebasquet has nothing on it and I tryed making a search for the type of file with no luck.
Now my question is: is it there any chance of recovering this pictures either with third party software or through ubuntu?, and if when you delete items in linux are they gone forever or they go as in windows to another place until you are sure you dont want them anymore?.
I am new to linux and I will hate to be scared away in this silly way because if this had happened in windows I will put a month salary in the fact you can still recover those pictures.
Thanks to anyone willing to give me an idea and if anyone want to tell me of about back ups can you please keep it for yourself.
Cheers.

---

### Post by steve.horsley on 2006-01-25
Bad news. I have no idea if you can get them back. Try exiting the file manager and opening it again. I **suspect** that the problem may have been caused by upper/lower case name confusion in the vfat driver. I have seen things get confused before when trying to copy a file or create a directory when there is one that already exists with the same name but different upper/lower case. I wonder if dragging files out and back somehow got tangled up like that. If so, the answer is to avoid vfat when working in Linux. Stick with Linux file systems - ext2/3 or resierFS.

I may be being unfair to vfat - I use it regularly to share files between Linux and Windows (dual boot) and don't get problems too often, but I can't think what else would have done it. Your best chance of recovering them might be a windows deleted file recovery utility.

---

### Post by cotcot on 2006-01-25
Hopefully you have set your history in your netbrowser long enough to find back the web sites from where you downloaded the pictures.
Have you checked the vFat file content after your burning story ? If you move files to another directory you sometimes have to "reload" or "refresh" the window in order to see the result of the move.

---

### Post by vaharim on 2006-01-26
Hi guys, thanks for your quick reply, I was pretty much sure the pictures were gone I just  wanted to make sure I got some more ideas before expending money in an expensive file recovery utility that I think it may recover those pictures, the thing is that I'm an amateur photographer and betwen those pictures  I have  the ones I took in a wedding and a lot more, and although I had already modified and save the best pictures I still wanted to keep the ones I haven't use yet.
Anyway thanks for your help and just one another thing, I live in UK, do any of you know of a good book for absolut beginners on linux maybe in waterstones or something?.
Thanks again for your help.

---

