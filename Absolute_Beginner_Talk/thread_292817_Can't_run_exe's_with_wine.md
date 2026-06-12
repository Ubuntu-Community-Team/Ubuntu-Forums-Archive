---
title: "Can't run exe's with wine"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by superbeef on 2006-11-04
Hey everybody. For whatever reason, any time I try to run anything with a .exe extension with wine, it gives me this message:

"The filename "install.exe" indicates that this file is of type "executable". The contents of the file indicate that the file is of type "DOS/Windows executable". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "DOS/Windows executable", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file."

Now, I can change the extension to just about anything else (usually go with .wine) and then it will run, but that poses a decent problem when trying to run things off a cd. For example, right now I'm trying to run the setup for Warcraft III, but it's setup.exe and gives me that message when I try to run it.

I have also tried running these things in terminal using both of the following:

"/media/cdrom0/install.exe"
"sudo /media/cdrom0/install.exe"

both give me "permission denied" thing after this. I know it doesn't have anything to do with the permissions thing you can change by changing their properties to make them executable, because I've already done that too.

Any help is greatly appreciated.

---

### Post by claydoh on 2006-11-04
you need to run it like this:
```
wine /path/to/your/installer.exe
```Also make sure you have run winecfg to set up your drives so wine can see your cdrom

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine) has more information for you

---

### Post by superbeef on 2006-11-04
All right that did it, thanks a lot!

---

