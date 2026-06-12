---
title: "Wine Program Installing Problem"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by ubbu on 2006-10-04
Hi,

I installed a program using Wine, when i try to start the application with "wine awinprogram.exe" it gives the 

```
wine: could not load L"c:\\windows\\system32\\awinprogram.exe": Module not found
```

error.

and just seconds after this it continues like

```
wineserver: could not save registry branch to /home/ubbu/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/ubbu/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/ubbu/.wine/user.reg : Permission denied

```

and freezes there.

SOmething I am missing in installing the program ? I did the same steps in here [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine) . I think I am missing a step or a configuration.

Thanks in advance for any help

---

### Post by CatKiller on 2006-10-04
Have you run **winecfg**?

---

### Post by ubbu on 2006-10-04
I did, checked some options but nothing seems wrong there to me (as I am new at it may be I am missing something possibly)
Is the solution in winecfg ?

---

### Post by pay on 2006-10-04
Try changing directory to where the program is installed. ie ```
cd /home/YOURUSERNAME/.wine/drive_c/Program\ Files/PROGRAMYOUINSTALLED
```and then run the program```
wine PROGRAMYOUINSTALLED.exe
```

---

### Post by ubbu on 2006-10-04
Well seems I didn' properly installed the win based program.

It is not located in the drive_c/Program Files directory.

SO I tried to reinstall and I realized that there these error messages appearing in terminal

```
err:msi:cabinet_notify failed to create L"c:\\Program Files\\PROGRAM NAME\\Normal.spt" (error 3)

```

same error message for every file that the installer tries to install.

ANything to the with the permission properties or smthng ?

---

### Post by ubbu on 2006-10-05
no idea ?

---

### Post by hyper_ch on 2006-10-05
I followed this guide to set wine up:

[http://www.ubuntuforums.org/showthread.php?t=149585](http://www.ubuntuforums.org/showthread.php?t=149585)

Maybe that gives you the one or other clue :)

---

### Post by ubbu on 2006-10-27
Couldn't solve the problem yet.
I uninstalled wine
reinstalled it

Still experiencing problems

When I try to install a program, the setup of the program give an error that it can not write the files to the specified directory.

For example I tried to add an application from winecfg by adding the Add Application button, and i can not see any directories there to browse. its a blank. Meanwhile this message is listed in the terminal

```
err:commdlg:IShellBrowserImpl_BrowseObject could not browse to folder
```

I tried to install another windows exe, and it turns back with same kind of error message saying that cant create directory etc. THen I go and manually created that directory and give the write permissions, than it installed some files in it but gives some other "cannot create" errors.

I guess there is something wrong with the permission, don't have an idea.

Any help would be appreciated.
Thanks in advance

---

### Post by CatKiller on 2006-10-27
You could try ```
chown -R ubbu:ubbu .wine
``` to see if that helps.

---

