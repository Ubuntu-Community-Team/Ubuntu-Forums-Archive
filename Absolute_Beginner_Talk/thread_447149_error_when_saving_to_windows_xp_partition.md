---
title: "error when saving to windows xp partition?"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by Jdratcliffe on 2007-05-17
when triying to copy a file (picture) across on to my windows partitions i get this error:

"Error while copying to "/ media/disk....backgrounds".
you do not have permissons to write to folder.

?

any ideas?

---

### Post by Quintin Riis on 2007-05-17
What kind of partition?  FAT or NTFS?  Write support for NTFS in the kernel is incredibly limited at this point.  You'll need to use a specialized solution if you want that.

---

### Post by AndyCooll on 2007-05-17
Unless you've created a FAT32 partition, I surmise you are trying to save to an NTFS partition. And you'll need NTFS-2G (I think that's what it's called) installed to be able to do that.

:cool:

---

### Post by Happy_Man on 2007-05-17
Open up a terminal (System --> Accessories --> Terminal) and type;
```
gskudo nautilus
```

navigate over to your /media folder, right-click on "disk" (or whatever partition it is you're trying to access), choose "properties", and under the permissions tab, change the owner and group to you. Should work then.

And if it is NTFS, the correct name is NTFS-3G. To install that, just type this into a terminal;
```
sudo apt-get install ntfs-3g ntfs-config
```

---

### Post by Jdratcliffe on 2007-05-17
> **Happy_Man said:**
> Open up a terminal (System --> Accessories --> Terminal) and type;
```
gskudo nautilus
```
^^^^^^^^^^^^^^^
saids command not found??


navigate over to your /media folder, right-click on "disk" (or whatever partition it is you're trying to access), choose "properties", and under the permissions tab, change the owner and group to you. Should work then.

And if it is NTFS, the correct name is NTFS-3G. To install that, just type this into a terminal;
```
sudo apt-get install ntfs-3g ntfs-config
```
^^^^^^^^^^^^^^^^^^^^^^^^^
installed find but did not make a differences same error?

---

### Post by Quintin Riis on 2007-05-17
It's 'gksu', not 'gksudo'.

Read the NTFS-3G documentation.

---

### Post by Jdratcliffe on 2007-05-27
what documentation?

---

### Post by 13thMonkey on 2007-05-27
Once you've installed ntfs-3g (as above), type 
```
info ntfs-3g
```
into a terminal for the documentation.

There are plenty of HOWTOs on the web too, but ntfs-3g does a good job of setting everything up for you on its own so you probably won't need to change the defaults.

---

