---
title: "Accessing Windows files"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by OlyPerson on 2007-12-01
Ok, so I'm trying to switch over to using Ubuntu for almost everything on my Win XP dual booted computer.  I want to be able to access music, picture, and document files while in Ubuntu that are stored in the XP partition.  I have a method in mind to do this, but I don't know if it can be done, or if there is simply some easier way.  
What I had in mind was to make another partition for those files and just access them from there.
So could people help me with this?  Or with a better way to do it.
Thanksss

---

### Post by dondad on 2007-12-01
> **OlyPerson said:**
> Ok, so I'm trying to switch over to using Ubuntu for almost everything on my Win XP dual booted computer.  I want to be able to access music, picture, and document files while in Ubuntu that are stored in the XP partition.  I have a method in mind to do this, but I don't know if it can be done, or if there is simply some easier way.  
What I had in mind was to make another partition for those files and just access them from there.
So could people help me with this?  Or with a better way to do it.
Thanksss

You could make another partition formatted as FAT32, which would be accessible from either Windows or Ubuntu. YOu can also access the Windows files from Ubuntu. If you are using Gutsy, you should be able to see them already. If not, then there is a setup that allows reading/writing NTFS files.

---

### Post by celticbhoy on 2007-12-01
If you goto Places -> Computer, and select FileSystem from the lest hand pane, then double click media, and you should see an icon for each of your partitions and drives. Just doulble click on the windows partition to gain access.

---

### Post by gigaferz on 2007-12-01
when you click on places you should be able to see your hardrive, or go to /media to see whats there.

or do you want to share files over a network?

---

### Post by OlyPerson on 2007-12-01
> **celticbhoy said:**
> If you goto Places -> Computer, and select FileSystem from the lest hand pane, then double click media, and you should see an icon for each of your partitions and drives. Just doulble click on the windows partition to gain access.

I do that but none of what I want I can see on there, only stuff that seemingly goes with the XP OS.
How hard is it to make a FAT32 partition?  And can't Ubuntu read and write NTFS files now, so why not make it a NTFS partition?

---

### Post by celticbhoy on 2007-12-01
Can you post a screen shot of what is displayed when you view the windows partition ??

---

### Post by OlyPerson on 2007-12-01
Aha!  I found it :oops:
But I can't open my music (MP3) format in RhythmeBox.  How can I open my music in Ubuntu?

---

### Post by celticbhoy on 2007-12-01
In Rythembox goto Music -> Import Folder, and select the location of your MP3 files, they should now load into the App.

---

### Post by dondad on 2007-12-01
> **OlyPerson said:**
> Aha!  I found it :oops:
But I can't open my music (MP3) format in RhythmeBox.  How can I open my music in Ubuntu?

YOu may need to install the mp3 codecs.

---

### Post by OlyPerson on 2007-12-01
> **celticbhoy said:**
> In Rythembox goto Music -> Import Folder, and select the location of your MP3 files, they should now load into the App.

When I do that it says "The GStreamer plugins to decode "MP3" files cannot be found".  I looked for the plugin to encode them but to no avail.

---

### Post by OlyPerson on 2007-12-01
> **dondad said:**
> YOu may need to install the mp3 codecs.

How do I do that?

---

### Post by celticbhoy on 2007-12-01
Try this link :-

[http://ubuntuforums.org/showthread.php?t=626949&highlight=mp3+codec](http://ubuntuforums.org/showthread.php?t=626949&highlight=mp3+codec)

---

### Post by heatpumpcontrol on 2007-12-01
Ahhh, I get it. You only have one partition as most people do I bet.

Well if that's the case then do the following.
 Click on 'Places'

click on 'Computer' - down the drop down list
in the new file Nautilus browser's left pane 
 click on 'File System'

in the right pane 
 click the 'media' folder

now you'll see the 'windows' partition under 'Local Disk'
 click on 'Local Disk'
 click on 'Document Settings'
 click on your user name folder
 click on 'My Documents'

here is where Windows stores all of your personal files. Now what you can do is left click the 'My Documents' folder and drag it to the left pane under your lowest folder in the left pane and this will create a shortcut to you 'Documents" located in your Windows partition. 

Now if you have Gutsy installed, it will 'mount' your Windows partition automatically. If not you can install NTFS using the Add/Remove under the 'Applications' menu. 

Now, (breath....) if you want to create a partition, it can be NTFS or ext3. If you make it ext3 format, you can install '[ext2ifs]("http://www.techenclave.com/forums/full-read-write-access-ext3-ifs-60383.html")' program which will allow your Windows O/S to view files in the ext3 partition. If you have enough space in your Windows partition, I suggest you resize that partition instead of messing the linux partitions. Just use 'Gnome Partition Editor' to resize the NTFS partition.

good luck

---

### Post by OlyPerson on 2007-12-01
Thanks, but I still can't figure out how to play the MP3 files :confused:
It seems like it should be working but then it doesn't.

EDIT: Got it :)

---

### Post by OlyPerson on 2007-12-02
Ok, so I don't really have it.

I can access all of my files, but I've run across something really annoying.  Every time I start up RythmeBox to play music, it has to do what seems like load all the music, so it takes about 20 minutes to play and music because it has to transfer from the XP partition.

How do I fix this?

---

### Post by celticbhoy on 2007-12-05
Dont use rythmebox box myself i prefer amarock have you tried it

---

