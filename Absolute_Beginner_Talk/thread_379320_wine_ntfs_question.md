---
title: "wine ntfs question"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by Chopperman on 2007-03-08
Now before I go trying to do something silly, lemme aski if it is silly before I even start. 

Suppose I have an app installed on a windows drive on an ntfs partition. And I want to run that app from the ubuntu environment. Can I mount the ntfs drive and run the app from that drive or do I need to reinstall it on the ubuntu drive?

---

### Post by milton1 on 2007-03-08
you should be able to run it from where it is. however, if the program requires write access to the installed folder, you will need to have ntfs write ability installed, and you will need write permission to the mounted ntfs drive.

Edit: many windows apps also write to other files in other folders. Running the app in wine could end up trying to write to the fake drive C instead of the real windows folders. this could screw up your program/saved files. If the app is poorly written (very possible) it will throw an absolute file reference instead of a relative one, thus messing up file calls.

---

### Post by Chopperman on 2007-03-08
> **milton1 said:**
> you should be able to run it from where it is. however, if the program requires write access to the installed folder, you will need to have ntfs write ability installed, and you will need write permission to the mounted ntfs drive.

Thanks Milton. 
Well yeah that makes sense. How compatible is ubuntu with ntfs when writing? Reading is one thing, writing is another bag of cats. if there is a reasonable chance that the write operations will crater my windows drive, I'll suck up the extra drive space on the ubuntu unit

---

### Post by milton1 on 2007-03-08
write capability requires one additional package (I forget the name). It is mostly stable, but there is still some chance of making your ntfs partition sad. I would recommend against it if you have the choice.

---

### Post by i0Null on 2007-03-08
I have recently done this too. I decided that to save me from having to install the windows application twice, i just installed [ntfs write support ]("http://ubuntuforums.org/showthread.php?t=337970") and link it to wine.

The easiest way to do this is to goto your wine directory (~/.wine by default) and symbolically link the "Programs File" to the one on your windows drive. you can also link you "windows" file also to save you from having to copy missing dll's that have not yet been ported to wine. However, i have found this causes some bugs in my application's, therefore i just copied over the files it was complaining about. 

Also, in wines "windows/profiles" directory i have linked the "My Documents" and "Desktop" folders to point to my home and desktop directory on linux.

Finally, it is probably a good idea to create a shell script for each of applications you would like to run. This will allow you to parse command lines to the app. This will then allow you to associate files for it.
And simple example of one of these scripts is shown below:

```

#!/usr/bin/env bash
export WINEPREFIX="/home/i0null/.wine"
wine "/home/i0null/.wine/drive_c/Program Files/Macromedia/Flash 8/Flash.exe" "$@"

```

---

### Post by Patrick K on 2007-03-08
I've not had any luck running a previously installed windows apps with wine. I think the problem arises in the registry. Wine doesn't use the real windows registry. It uses its own "fake" registry in its own "fake" C:\ drive. When the program launches it will look to the registry for paths and other info. Since under wine it will be looking to the "fake" wine registry, it will not find the data it needs. 

I don't know about ntfs but I'm pretty sure you'll have problems regardless of the file system involved. In my case FAT32 is the file system.

I even tried exporting all the registry keys for the apps from the windows' registry and importing them into wine's registry. This didn't work with the the two apps I tried this with. A lot has to do with the app, though. Some may be more forgiving than others. You can try it but don't be too disappointed if it fails.

---

### Post by Chopperman on 2007-03-08
Thanks Gents!

Sounds to me like installing the app into the ubuntu system is the more foolproof method. And fool proof is what I need :)

---

