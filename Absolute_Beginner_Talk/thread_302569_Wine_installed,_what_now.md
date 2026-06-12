---
title: "Wine installed, what now"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by kiyometane on 2006-11-18
I sucessfully installed wine. Now how to use it. I'm trying to install a windows 32 bit program. what command should i use to install the application?
thanks

---

### Post by cactaur on 2006-11-18
Well, now with wine, you can install a program by just running the setup.exe or whatever file. You can run it by:

```
wine "C:/Program Files/yourfolder/yourprogram.exe
```

I think that's how you do it.

---

### Post by unbuntu kid on 2006-11-18
how do you run the app if your windows partition is NFTS and Linux ext3, and no FAT32 partition to share?  Neither is compatable with the other.

---

### Post by kiyometane on 2006-11-18
I'm trying to run the application from my cd room
and i get the error " error intalling Ikernell.exe " at begening of setup

---

### Post by unbuntu kid on 2006-11-18
when you want to easily run an app im wine, righ click the .exe--> open with other application...-->(at the bottom)Use custom Command-->Type in "wine" (w/o the quotes)
It should run fine!

---

### Post by kiyometane on 2006-11-18
thanks

---

### Post by Buck2348 on 2006-11-18
I just installed wine and gave it a try.  It ran a simple Windows program called Notepad with no problems.  When I tried to run a bigger program--Corel Print House--I got the following:
```

buck@Dmitri:~$ wine "/media/hda2/Program Files/Corel/Print House 6/Printhse.exe"
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\media\\hda2\\Program Files\\Corel\\Print House 6\\CRLCTL83.dll") not found
err:module:import_dll Library CRLCTL83.dll (which is needed by L"Z:\\media\\hda2\\Program Files\\Corel\\Print House 6\\CRLUI83.dll") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\media\\hda2\\Program Files\\Corel\\Print House 6\\CRLUI83.dll") not found
err:module:import_dll Library CRLUI83.dll (which is needed by L"Z:\\media\\hda2\\Program Files\\Corel\\Print House 6\\Printhse.exe") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\media\\hda2\\Program Files\\Corel\\Print House 6\\CRLCTL83.dll") not found
err:module:import_dll Library CRLCTL83.dll (which is needed by L"Z:\\media\\hda2\\Program Files\\Corel\\Print House 6\\Printhse.exe") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\media\\hda2\\Program Files\\Corel\\Print House 6\\CrlWeb83.dll") not found
err:module:import_dll Library CrlWeb83.dll (which is needed by L"Z:\\media\\hda2\\Program Files\\Corel\\Print House 6\\Printhse.exe") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\media\\hda2\\Program Files\\Corel\\Print House 6\\Printhse.exe") not found
err:module:import_dll Library MSVCP60.dll (which is needed by L"Z:\\media\\hda2\\Program Files\\Corel\\Print House 6\\Printhse.exe") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"Z:\\media\\hda2\\Program Files\\Corel\\Print House 6\\Printhse.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\hda2\\Program Files\\Corel\\Print House 6\\Printhse.exe" failed, status c0000135
```

For the entries that I checked, the .dll files are there, either in the same folder with the executable or in the Windows folder.  Can anyone help, please?  My Ubuntu will be complete if I am able to run a few old Windows programs.

Thanks,
Buck

---

### Post by jordanmthomas on 2006-11-18
wine looks in its own windows folder for those dlls.  The easiest way is to copy them from your actual windows installation to your wine windows installation.

You'll need to find those dlls and put them in ~/.wine/somewhere  
I'm not sure why it doesn't find the ones in the same directory, though.
Perhaps you would need to run the installer in wine and have two copies on your hard drive.

---

### Post by kiyometane on 2006-11-19
I have 2 hhds, one with ubuntu and the other windows. They dont see each other. Do u know how to make ubuntu see the windows hardrive so that i can use it files with wine

---

### Post by bodhi.zazen on 2006-11-19
> **kiyometane said:**
> I have 2 hhds, one with ubuntu and the other windows. They dont see each other. Do u know how to make ubuntu see the windows hardrive so that i can use it files with wine

Assuming you windows is hda1...

```
sudo mkdir /mnt/windows
sudo mount /dev/hda1 /mnt/windows -o uid=1000,gid=1000
```

To make this long lasting you need to edit [fstab](http://ubuntuforums.org/showthread.php?p=1653968#post1653968).

[Mounting Windows Partitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

This may also help [How to wine](http://doc.gwos.org/index.php/HowToWine)

But to enable your application you should search and follow instructions at [wineHQ, application database](http://appdb.winehq.org/). Search for instructions in the gray box on the Left....

---

### Post by Denn1s on 2006-11-19
[http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html]("http://http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html")

I think the address is pretty self explanatory

:P

---

### Post by bodhi.zazen on 2006-11-19
> **Denn1s said:**
> [http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html]("http://http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html")

I think the address is pretty self explanatory

:P

Looks good, but the link is re-directed. Updated:
[http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html](http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html)
[URL=http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html]

you have one too many http:// in your "[URL="http://http://] hard code :p

---

