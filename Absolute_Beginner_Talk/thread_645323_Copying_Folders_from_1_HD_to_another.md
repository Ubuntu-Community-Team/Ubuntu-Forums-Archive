---
title: "Copying Folders from 1 HD to another"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by killaray on 2007-12-19
i just bought a new HD and wanna copy the folders over to the new 1 from the old one.. but i dont wanna copy the file system like the command ```
sudo cp /dev/hdb1 /dev/sda1
``` does.. i wanna make it so itll just strictly copy the folder

oh yea i wanna it to be command line cause i think my PC will freeze for some reason if i just drag it over

---

### Post by Existentialist on 2007-12-20
With cp you can use the -r flag to copy folders recursively.  Never write anything to /dev/anything as this is the block device and will destroy you partition information.  If it is mounted you would write to /media/sda1

>cp -r /home /media/sda1/home

Should copy everything in your home directory to a folder called home on the sda1 drive/partition

---

### Post by nowshining on 2007-12-20
what are ur computer specs?

---

### Post by thelatinist on 2007-12-20
Note that copying the folders on your hard drive using cp will not preserve ownership, permissions, timestamps, etc.  If you need to preserve such information (as in a backup), you can cd to the parent folder of the one you want to copy and then use:

```
sudo tar cf *folder_name* | ( cd /media/sda1; tar xfp -)
```

Be careful, though: using the -f switch this will not ask before overwriting files of the same name in the destination folder.  If you want to specify more than one folder in the current folder, just list them separated by spaces (ie, *folder_name_1 folder_name_2 etc...*)

---

### Post by hyper_ch on 2007-12-20
I'd do that:

```

sudo cp -Rp /dev/hdb1/* /dev/sda1/*

```

That will copy everything and keep the file permissions

---

### Post by thelatinist on 2007-12-20
> **hyper_ch said:**
> I'd do that:

```

sudo cp -Rp /dev/hdb1/* /dev/sda1/*

```

That will copy everything and keep the file permissions

I've been told there are a couple of problems using cp:

1) Not all versions of cp support the -R flag (only a problem if you use multiple *nixes)
2) -R doesn't always handle symbolic links properly.

I've been using tar for this purpose because I thought it was the only way to ensure everything was preserved, but I would be glad to learn otherwise.

---

