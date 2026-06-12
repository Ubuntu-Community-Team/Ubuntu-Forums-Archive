---
title: "please help! how do i create the file kde-start-compiz???"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Murdo on 2007-09-08
Hi

OK im a complete newb and im using Suse SLED 10 and dont understand the following:



    * Create the file /home/<username>/bin/kde-start-compiz
    * Enter two lines into it: 

compiz --replace glib gconf <plugins to load> &
gtk-window-decorator &


how do i create the file???

Thanks

---

### Post by cookies on 2007-09-08
Use a text editor like Kate or KWrite. Put those lines in the file, save it to where you need to. The right click it and make it executable. 

Got it? I know it sounds kinda funky....

---

### Post by wormser on 2007-09-08
Open a terminal.  Applications> Accessories> Terminal.  Search for a bin directory with the ls command.

```
ls
```

If you see a folder called bin then skip this next step.  To create a folder called bin.

```
mkdir bin
```

Now we to change directory into the bin directory.

```
cd bin
```

Now we can create the file kde-start-compiz.

```
touch kde-start-compiz
```

The folder and file is now made.  You can double check it by using the ls command again.  Now you can add those 2 lines.

```
gedit kde-start-compiz
```

Paste the lines in and close the file.

---

