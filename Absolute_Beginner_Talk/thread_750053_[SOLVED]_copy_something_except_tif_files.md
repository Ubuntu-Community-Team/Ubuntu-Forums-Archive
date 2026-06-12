---
title: "[SOLVED] copy something except tif files"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by antonio_ing on 2008-04-09
I guys i would like to copy all the directories in another directory without copying the tif files that are included. What is the right command from the terminal??

---

### Post by ghostdog74 on 2008-04-09
```

find /fullpath -type f ! -name "*.sh"

```
the example will find files in /fullpath (including subdirectories ) that does not end with ".sh".
if you want to copy everything into ONE directory
```

find /fullpath -type f ! -name "*.sh" -exec cp "{}" /destionation {} \;

```
otherwise, if you need the same directories structure at the destination , some more coding need to be done.

---

### Post by Gen2ly on 2008-04-09
hmmm...

**Edit:** Ghostdog beat me too it, his way is probably better

The best I think of would be to create the directories:

```
mkdir -p /directory/subdirectory/subsubdirectory
```

Then the files could be copied like such:

```
cp *.[p,j,g][n,p,i][g,f] /directory/subdirectory/sub...
```

The above only includes png, jpg, and gif, others will have to be added.

I do suppose find could help too:

```
find . -name "*.png" -name "*.jpg" -name "*.gif" | xargs cp /directory/subdir...  {} \;
```

I'm not sure that find can grab multiple -name instances though.

Hope this helps.

---

### Post by sdennie on 2008-04-09
If you just wanted to recreate a directory/file structure in a different location without including the .tif files, you could do the following from the directory you want to duplicate:

```

cp `find . ! -name "*.tif"` destination

```

That should recreate the directory structure in whatever directory you specify as "destination" but, without the tif files.

---

### Post by antonio_ing on 2008-04-09
it doesn't work because it says that each file is not a directory. There are some directories and some files in them that need to be copied.

---

### Post by antonio_ing on 2008-04-09
Vor,

the tif files are nested in the subdirectories
when i copy with your suggestion it copies also the tif files inside the directories

---

### Post by ghostdog74 on 2008-04-09
> **antonio_ing said:**
> it doesn't work because it says that each file is not a directory. There are some directories and some files in them that need to be copied.
show the script you used. you did not put -type f if you are using the find method.

---

### Post by antonio_ing on 2008-04-09
find /media/disk/Antonio/FlowViz_jet/20080319/ -type f ! -name "*.tif" -exec cp "{}" /home/antonio/Desktop/Flow_viz/20080319/ {} \;

---

### Post by ghostdog74 on 2008-04-09
> **Dirk.R.Gently said:**
> hmmm...

**Edit:** Ghostdog beat me too it, his way is probably better

The best I think of would be to create the directories:

```
mkdir -p /directory/subdirectory/subsubdirectory
```

Then the files could be copied like such:

```
cp *.[p,j,g][n,p,i][g,f] /directory/subdirectory/sub...
```

The above only includes png, jpg, and gif, others will have to be added.

no, the above will include files with extension pig,ppf,jng etc etc

> 
I do suppose find could help too:

```
find . -name "*.png" -name "*.jpg" -name "*.gif" | xargs cp /directory/subdir...  {} \;
```

I'm not sure that find can grab multiple -name instances though.

Hope this helps.

```

find . \( -name "*.png" -o -name "*.jpg" -o -name "*.gif" \) | ........

```

---

### Post by sdennie on 2008-04-09
Ok.  I should have tested before writing it.  A simpler way may be to use a variation with tar instead:

```

tar cf no-tif.tar `find . -type f ! -name "*.tif"`

```

That will create a file called no-tif.tar in the directory which you can then copy, move, etc to a destination directory or even machine and then untar it (tar xvf no-tif.tar) and it should rebuild stuff the way you want.

---

### Post by antonio_ing on 2008-04-09
i'll be more precise because i'm new of the terminal
I have to copy from /media/disk/Antonio/FlowViz_jet/20080319/ to /home/antonio/Desktop/Flow_viz/20080319/ all the directories and the files named media, rms , data.mat except the tif files.

I have wrote  this in the terminal:

antonio@antonio-laptop:/media/disk/Antonio/FlowViz_jet/20080319$ find . -name "media" -name "rms" -name "data.mat" | xargs cp /home/antonio/Desktop/Flow_viz/20080319/ {} \;

but the answer was:

cp: target `;' is not a directory

---

### Post by ghostdog74 on 2008-04-09
> **antonio_ing said:**
> find /media/disk/Antonio/FlowViz_jet/20080319/ -type f ! -name "*.tif" -exec cp "{}" /home/antonio/Desktop/Flow_viz/20080319/ {} \;

remove the last {}

---

### Post by antonio_ing on 2008-04-09
vor 

it worked greatly thanks very much

---

