---
title: "Please Tell Me What This Means"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by tarchy on 2007-05-15
Reference; [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam)

> Simply change to the directory where you downloaded SteamInstall.exe and type

wine SteamInstall.exe

If you downloaded the MSI version of Steam installer, type wine msiexec /i SteamInstall.msi 

I don't know what "CHANGE THE DIRECTORY WHERE YOU DOWNLOADED STEAMINSTALL.EXE" MEANS....

I typed wine msiexec /i SteamInstall.msi but  this error occurs: tarchy@tarchy-desktop:~$ wine msiexec /i SteamInstall.msi
err:msi:copy_package_to_temp failed to copy package L"SteamInstall.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002!

---

### Post by EndPerform on 2007-05-15
You might be better off finding the .EXE version of the Steam installer.  I believe there are issues with the .MSI version.  The link is referencing the .EXE installer, not the .MSI installer which is what you have.

---

### Post by Acglaphotis on 2007-05-15
That means you gotta do this:

```
cd /path/to/steaminstall/
```

And change the "/path/to/steaminstall" for the actual path like /home/john/downloads/. dont put the actual path to the file just to folder where the file is.

-Acgla

---

### Post by tarchy on 2007-05-15
Thanks Acgla, but how do I do that?

---

### Post by tarchy on 2007-05-15
I found out, but this error occurs; 

bash: /home/tarchy/Desktop/Steam/SteamInstall.msi: Permission denied

---

### Post by tarchy on 2007-05-15
Oh, so just do the folder...ok now this error: bash: cd: /home/tarchy/desktop/Steam: No such file or directory

---

### Post by mikewhatever on 2007-05-15
It looks like what you want is:
> cd /home/tarchy/Desktop/Steam
> wine msiexec /i SteamInstall.msi 
The first command moves you to the right directory, the second probably launches the installer in wine.

---

### Post by tarchy on 2007-05-15
So I tried it again and...tarchy@tarchy-desktop:~$ cd /home/tarchy/Desktop/Steam
tarchy@tarchy-desktop:~/Desktop/Steam$

---

### Post by aidanr on 2007-05-15
cd means change directory and the path is case sensitive  so it would be:
cd /home/tarchy/Desktop/Steam/

---

### Post by tarchy on 2007-05-15
Thanks -- 

wine: could not load L"Z:\\home\\tarchy\\Desktop\\Steam\\SteamInstall.msi": Bad EXE format for 
tarchy@tarchy-desktop:~/Desktop/Steam$

---

### Post by tarchy on 2007-05-15
Oh Lord It Worked!! Thank You!!

---

### Post by mikewhatever on 2007-05-15
> **tarchy said:**
> Oh, so just do the folder...ok now this error: bash: cd: /home/tarchy/desktop/Steam: No such file or directory

Please note that it is **Desktop** and not desktop. Remember that the terminal is case sensitive.

---

### Post by aidanr on 2007-05-15
that's for the exe, for the msi it's:
wine msiexec /i SteamInstall.msi

edit:// nevermind you got it

---

