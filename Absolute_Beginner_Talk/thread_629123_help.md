---
title: "help"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by Tiberias104 on 2007-12-02
Ok just started messing with linux live disks. friend told me to try ubuntu so i did. is it possible to run windows executables or alteast convert them to something readable by ubuntu and second can i change the partitions if at some pt i want ot get rid of ubuntu without reformatting my comp

---

### Post by PmDematagoda on 2007-12-02
You can run Windows executables using a program called Wine which can be installed using:-

```
sudo apt-get install wine
```

Once it is installed do:-

```
winecfg
```

To configure the Wine to fit your needs.

When you want to run a .exe file, you can open it with Wine in the file manager or do:-
```

wine nameoffile.exe
```

---

### Post by santiagoward2000 on 2007-12-02
> **Tiberias104 said:**
> Ok just started messing with linux live disks. friend told me to try ubuntu so i did. is it possible to run windows executables or alteast convert them to something readable by ubuntu and second can i change the partitions if at some pt i want ot get rid of ubuntu without reformatting my comp

Yes and Yes!
About Windows' executables, you can use WINE to run them. Just install it from the repositories:
```
sudo apt-get install wine
```
That should do it!

And about the partitions, you can use GParted from the liveCD (I think it's under the System menu). With it you can resize, create and delete partitions. You could just use it to delete the Ubuntu partition and resize the Windows' one. However, I think there could be a problem with the start up, you'll have to reconfigure GRUB, but I'm not really sure how that works...

---

