---
title: "[SOLVED] direct x uninstall"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by vlaklak on 2008-01-02
[SIZE=3]Hi,

Everyone makes mistakes sometimes and I made one installing Directx9 using Wine!

Now I can not see a 3D things or I can not play 3D games on Ubuntu!  Everything has only 2 sides for me now :)

I can format and rebuilt ubuntu 7.10 without a problem!  But is there an another solution?!?
[/SIZE]

---

### Post by Ub1476 on 2008-01-02
I think all apps for WINE is stored in /home/user/.wine/.

I believe you just need to remove the folder from there, or there should be an uninstall option from the WINE menu.

---

### Post by LowSky on 2008-01-02
i dindt even thin DX would install? You learn something new everyday... anyway I cant see DX or wine auto starting at each boot unless you wrote a script to do so. Are you sure you haven't  turned off your video drivers.

---

### Post by oedipuss on 2008-01-02
If you can't figure out a way to uninstall it, there is another way.
Rename your user wine directory (it is '/home/yourusername/.wine') and run wineprefixcreate : 

cd ~ 
  this cd's to your home dir.
mv .wine .wine_old  
  this moves .wine to .wine_old, essentially renaming it, to ensure it's not lost or overwritten.
wineprefixcreate
  to create the default wine directory, which is a new default .wine, without directx9c or anything else installed.

Unfortunately you 'll have to reinstall your wine programs. Copying an application's directory from 'Program Files' or such might work for simple apps, but not nessesarily. 

EDIT: You can always delete the new .wine (after making sure it's the new default one you're deleting :P ) and rename the .wine_old to .wine again, to revert to your old configuration, if the problem turns out to be something else. If there's important stuff in that dir, and you have some free space, I'd recommend copying it to a backup directory, just to be sure :  cp -r .wine_old .wine_backup.

A useful thing to keep in mind, though a bit more complex, is that you can have multiple wine directories, with different settings, installed applications etc, just like having many windows installs.
Just create a different wine dir, with :
 WINEPREFIX="/home/user/DIRNAME" wineprefixcreate
replacing 'user' with your username and DIRNAME with a name of your choice, and run wine with 
 WINEPREFIX="/home/user/DIRNAME" wine myapplication.exe

---

### Post by vlaklak on 2008-01-03
[SIZE=3]I remove Ubuntu 7.10 and then install again.  And now I know what the problem is.  

The problem is not from DirectX, it is from COMPiZ!!  

I download compiz fusion using : [/SIZE][http://ubuntuforums.org/showthread.php?t=580748&highlight=compiz+fusion](http://ubuntuforums.org/showthread.php?t=580748&highlight=compiz+fusion)

[SIZE=3]this directory and now I can't play any 3D games!  What should I do?!?  
And we can say that this problem is no more, but antoher problem emerges! [/SIZE]

---

### Post by oedipuss on 2008-01-11
You shouldn't be running compiz when using another 3d application. 
Try using one of the switcher utilities such as  : [http://forlong.blogage.de/article/pages/Compiz-Switch](http://forlong.blogage.de/article/pages/Compiz-Switch) 
that can make turning compiz on and off easier.
Otherwise, the quickest way to disable it for a while is running 'metacity --replace' (minus the quotes) in a terminal.

---

