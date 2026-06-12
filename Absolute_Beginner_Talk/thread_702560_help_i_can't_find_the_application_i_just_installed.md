---
title: "help i can't find the application i just installed!"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by cnote1239 on 2008-02-20
i just installed 7 zip with the add or remove programs menu but i can't find it anywhere! i know this is a bit silly but i've only had ubuntu for a day and i'm a bit lost.:) please help.

---

### Post by Therion on 2008-02-20
That's because it's a command line aplication.  With it installed the Archive Manager will work with .7z format automatically.  If you have a .7z file you want to extract, you can simply right-click on the file and use the "Extract Here" option in the context menu.

---

### Post by spiderbatdad on 2008-02-20
It is a command line tool. I believe you also need p7zip ```
sudo apt-get install p7zip
```

Of course ubuntu has gzip
```
man gzip
```

---

### Post by familyjules74123 on 2008-02-20
Therion and spiderbatdad are right.  If you ever have trouble finding an application that has an interface though try using the Alt+F2 command.  It is a finder and usually when you start typing in the program highlighted names with come up, just keep typing until you see the program you are looking for.

---

### Post by cnote1239 on 2008-02-20
well wheres the archive manager? i can't find that either.:confused:

---

### Post by FuturePilot on 2008-02-20
It's hidden by default. Right click on the Applications menu and select Edit Menus. Go to the Accessories and check the Archive Manager box. Then it will show up under Accessories. You can also just double click on a .7z file and it will open

---

### Post by spiderbatdad on 2008-02-20
Archiving is also a command line process, but it has some graphical applications as Future Pilot pointed out. Lets say you have a file you want to archive. Right click the file. You'll see an option to create an archive. Let's say you have a tar or zip file you want to extract. Right click the package and you'll see an option to extract it.

---

### Post by cnote1239 on 2008-02-20
thanks i found archive manager and got that working. yay!!!\\:D/

---

### Post by stchman on 2008-02-20
> **cnote1239 said:**
> i just installed 7 zip with the add or remove programs menu but i can't find it anywhere! i know this is a bit silly but i've only had ubuntu for a day and i'm a bit lost.:) please help.

The 7zip packages are just what you can call plugins for File Roller(Archive manager).

I suggest that you install the rar stuff as well.

```

sudo apt-get -y install rar unrar p7zip p7zip-full
```

Now that those are installed either click on a .7z or .rar file and you can decompress that archive.  You also have the ability to create .7z or .rar archives as well.

---

### Post by fatality_uk on 2008-02-20
Additionally, you can find where a program has been installed from the terminal and use that to navigate to the directory, for instance, if you wanted to know where Quake4 had just been installed, type the following in a terminal
> 
whereis quake4

Result will look like this
> quake4: /usr/local/bin/quake4 /usr/local/games/quake4

---

