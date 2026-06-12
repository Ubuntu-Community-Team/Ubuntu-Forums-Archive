---
title: "How to create an archive (zip. 7z, etc), containing folders in Nautilus 2.14.2 ?"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by davescafe on 2006-06-02
I am searching for a way to create an archive in Nautilus that contains folders (directories).  For example, in Nautilus, I can easily right-click on a document and from the in-context menu, select "Create Archive...".  From there, I am given the option of naming the archive, and selecting what form of archive I want (tar.gz, zip, 7z, etc.).  The problem is that when I do the same thing for a folder (or directory), the archive is created and it is empty.  This behavior seems defective.  I have searched the Nautilus documentation out at gnome.org, but there is no mention of the Archive feature.

Any suggestions would be welcome.

Thanks,

Dave

---

### Post by Kilz on 2006-06-02
[QUOTE=davescafe]I am searching for a way to create an archive in Nautilus that contains folders (directories).  For example, in Nautilus, I can easily right-click on a document and from the in-context menu, select "Create Archive...".  From there, I am given the option of naming the archive, and selecting what form of archive I want (tar.gz, zip, 7z, etc.).  The problem is that when I do the same thing for a folder (or directory), the archive is created and it is empty.  This behavior seems defective.  I have searched the Nautilus documentation out at gnome.org, but there is no mention of the Archive feature.

Any suggestions would be welcome.

Thanks,

Dave[/QUOTE]

I have just made a few archives. Right click on a folder , then click "Create Archive" in the menu that pops up. You can choose what kind of archive from the extension selector menu on the create archive box. None were empty, I even tested that out by opening them.

---

### Post by davescafe on 2006-06-04
[QUOTE=Kilz]I have just made a few archives. Right click on a folder , then click "Create Archive" in the menu that pops up. You can choose what kind of archive from the extension selector menu on the create archive box. None were empty, I even tested that out by opening them.[/QUOTE]


Thank you for your reply.  I have Ubuntu installed on 2 machines.  I am unable to get the archive to work for folders (as I described above), on the one machine.  After reading your reply, I tried on my other Ubuntu machine and it works.  So I guess I need to figure out what the difference is between the two.

Thanks,

Dave

---

### Post by davescafe on 2006-06-05
I have found the reason I had a problem - 7-zip archives created through Nautilus do not save folders.  All the other formats work.

---

### Post by Ben Sprinkle on 2006-06-05
lol yep thats all u had to do =D>

---

### Post by phetre on 2006-06-05
[QUOTE=davescafe]I have found the reason I had a problem - 7-zip archives created through Nautilus do not save folders.  All the other formats work.[/QUOTE]
You probably already know this, but you can also start File-Roller from the Accessories menu, then add your directories manually.  Does this help with the 7-zip problem?

---

### Post by davescafe on 2006-07-04
[QUOTE=phetre]You probably already know this, but you can also start File-Roller from the Accessories menu, then add your directories manually.  Does this help with the 7-zip problem?[/QUOTE]

It does not solve the problem, but I appreciate your suggestion.

Specifically (for those who may be following this):
1.  I right-clicked on the Applications menu and selected "Edit Menus"
2.  Under "Accessories" I clicked to enable the Archive Manager (I presume that this is "File Roller")
3.  Clicked on the "Close" button
4.  Went to the Applications menu => Accessories => Archive Manager
5.  I created a new archive and named it
6.  I dragged a folder from Nautilus into the Archive Manager
Result:  Error message which reads, "An error occurred while adding files to the archive."

The option "command line output" reveals more info, which culminates in the message: WARNING: cannot find 8 files.

This error only happens when 7-zip as an archive type.  Other archive types such as "automatic" (tar) and jar, do not have problems with folders.

---

### Post by curvedinfinity on 2006-10-31
I also have this problem. File-roller simply will not add directories to 7z archives. Being a 7z fan, this has bothered me for a long time. Good to see it's not just me.

Can anyone help?

---

### Post by Ben Sprinkle on 2006-10-31
If you want to do it in terminal do this:
```

cd dir
tar -cf/home/$USER/file.tar folder-or-files-to-be-added

```
Or in Nautilus right click a folder and goto create archive.

---

### Post by curvedinfinity on 2006-10-31
Thank you for your reply, but I am refering to a specific feature of File-Roller that does not work.

I do know how to create an archives using the terminal, nautilus right-click menu, and through File-Roller directly. 

The specific feature of File-Roller I am refering to, which I believe does not work, is the ability to add directories to a 7z archive.

---

### Post by Ben Sprinkle on 2006-10-31
No clue about 7z then, I always use rar or tar.

---

### Post by davescafe on 2006-10-31
> **synectics said:**
> No clue about 7z then, I always use rar or tar.

rar is console-only, correct? I am aware of how to run these commands at a terminal prompt (7z, rar, etc.), but that sort of defeats the whole point of using Linux on the desktop. So rather than using 7z, I have begun using b-zipped tar files, because these can be created and opened on multiple platforms and have a reasonably high compression rate. Ideally though, it would be nice to have similar functionality in file roller as exists at the terminal prompt.

Dave

---

### Post by curvedinfinity on 2006-10-31
> **davescafe said:**
> rar is console-only, correct? I am aware of how to run these commands at a terminal prompt (7z, rar, etc.), but that sort of defeats the whole point of using Linux on the desktop. So rather than using 7z, I have begun using b-zipped tar files, because these can be created and opened on multiple platforms and have a reasonably high compression rate. Ideally though, it would be nice to have similar functionality in file roller as exists at the terminal prompt.

Dave
File-Roller is able to compress and decompress rar. However, it only allows the extensions .ar,.ear,.war, and .jar for creating a new rar (for what reason, I have no idea). Any old rar program should be able to open your archive if you simply rename one of those extensions .rar.

It technically supports .7z (you can compress and decompress individual files as stated above). I bet that directories dont work because of something simple, like it giving relative paths to p7zip when it needs absolute ones.

---

### Post by Ben Sprinkle on 2006-11-01
Rar does have several GUI's for it.

---

