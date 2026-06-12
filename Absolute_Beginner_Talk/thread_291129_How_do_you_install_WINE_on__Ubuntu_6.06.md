---
title: "How do you install WINE on  Ubuntu 6.06"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by bobsta63 on 2006-11-02
Hi all,

Would anyone be able to help? I would like to install WINE so that I can run a few Windows Applications, can this be done using the Add/Remove Software tool (On Applications Menu) or do you have to compile it manually? (If so does anyone know an good tutorials for compiling it?

Also once I get WINE up and running how do I make launchers to place on the desktop to auto run a windows app? would it be something like...

```
wine /home/USERNAME/example.exe
```

Also is there a particular place you need to put the window's EXE's so that WINE will execute them: For example the EXE will not execute from anywhere else but say ```
/usr/bin/wine/applications
```

Thanks in advance :)

---

### Post by jrings on 2006-11-02
I suggest that you have a look at Automatix2, it can install a number of useful things for you, you not only Wine but maybe there is other stuff yu'd like.

[http://getautomatix.com/wiki/index.php?title=Installation](http://getautomatix.com/wiki/index.php?title=Installation)

Has a pretty good tutorial how to use it, you can copy&paste the commands into a console.

---

### Post by Klaidas on 2006-11-02
> sudo apt-get install wine
I gotta warn you though, wine ussually doesn't work as it should... (at leat for me).
You might better want to try Crossover oor just keep you windows partition if you need very specific apps.

---

### Post by timetunnel on 2006-11-02
You don't have to compile it yourself. Just install it with the Package Manager and you're done.

To add a menu item, open the menu editor and create a new menu item in the desired place. The important thing is how the command for the menu item has to look like. You have to provide the full path to the executable (remember the case-sensitivity in Linux). Example:
```
wine /home/username/mywinapps/bla/bla.exe
```
That's it usually. :-)

There's no particular place where you have to place the applications. If you use an installer (setup.exe usually) to install a Windows application, it will usually goes to a subdirectory in /home/username/.wine/

ubuntu has a slightly out-of-date version of wine. If you want the very latest version, you can find information about that - and more general information about wine - here: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Be aware that not all applications run fine with wine - or at all. [http://winehq.com](http://winehq.com) has an application database with information about what runs and what not.

---

### Post by bobsta63 on 2006-11-02
Thank you guys, I will try tonight when I get home,

Thanks a bunch!! :)

---

