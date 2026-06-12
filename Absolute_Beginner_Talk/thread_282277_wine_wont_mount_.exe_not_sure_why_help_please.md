---
title: "wine wont mount .exe not sure why help please"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by DraeLee on 2006-10-22
ok got a problem.  I installed wine yesterday and things seemed to be working ok but WoW wouldnt finish installing.  So i uninstalled wine and reinstalled it today, but now i get an error saying

Couldn't display "/media/cdrom0/Installer.exe".

I dont know what its not working properly, but I uninstalled and reinstalled it several times.  Once thru synap and once straight from the tar.  I am still very new to this and I might need a hand holding, but I will listen

thanx in advance

---

### Post by CatKiller on 2006-10-22
Does "Installer.exe" really start with a capital I?

---

### Post by DraeLee on 2006-10-22
yes it does well i tried a different method ok check this out.  I copied all of the wow files to a folder but my problem is that i cant access it thru the cli so that i can do the wine command for the Installer.exe   Do you know i would write a command.

i tried cd /hda and all that but i dont know the command to write.  any help would be appreciated im at a loss


oh also i dont know how to check what partions are there on my pc thru the cli

---

### Post by CatKiller on 2006-10-22
> **DraeLee said:**
> my problem is that i cant access it thru the cli

cd is the command to **c**hange **d**irectory. There are links to basic command howtos in people's signatures, but I've never been to any, so I don't know where they are.

Also, you can use tab-completion for files and paths (and commands). So you type the start of the filename and then press Tab. If the rest of it can be uniquely filled in, that will happen. If it can't, the computer will beep and pressing Tab again will give you a list of files that match what you've typed so far. 

>  so that i can do the wine command for the Installer.exe   Do you know i would write a command.

You can use Windows-style paths in quotes for things through Wine. So ```
wine "C:\Program Files\I Can't Believe It's Not\warcraft.exe
``` or whatever. I don't know if you get to use tab-completion that way though.

Also, if you find your file in Nautilus you should, once Wine is configured through winecfg, be able to right-click on the file and select "Open with Wine Windows Emulator".

I have no idea where you copied your files, or what they were called, to be able to give you more instruction than that.

> i tried cd /hda and all that but i dont know the command to write.  any help would be appreciated im at a loss


oh also i dont know how to check what partions are there on my pc thru the cli

As far as you are concerned from the command line, there are no partitions on the computer. Linux has a [unified filesystem]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") where everything is a file that fits somewhere into the tree of files that starts at /. If a partition is **mounted** at a **mount point** it will appear at that point in the filesystem. If it isn't mounted, it won't appear at all.

I hope this is helpful to you.

I haven't tried to run WoW through Wine, so I can't address your specific problem of it crashing. There are many posts of people trying to do so in the Gaming and Leisure forum - perhaps that might have some information you could use?

Good luck.

---

### Post by DraeLee on 2006-10-22
ok thanks ill try there

---

