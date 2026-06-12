---
title: "Rename file from Terminal"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-10-03
How is it again I rename a file from Terminal?
Thanks

---

### Post by Ben Sprinkle on 2006-10-03
> **aktiwers said:**
> How is it again I rename a file from Terminal?
Thanks

```

mv '/home/$USER/file.ext1' '/home/$USER/file.ext2'

```
I have heard that the move command is the rename also.

---

### Post by aysiu on 2006-10-03
You don't have to include the path if you're already in the directory, by the way: ```
cd ~/music
mv songname.mp3 newsongname.mp3
```

---

### Post by n0dl on 2006-10-03
Depending on the permission of the file you may need to use sudo or pass the -r option
```
sudo mv -r somefile newfilename
```

---

### Post by aysiu on 2006-10-03
nOdl, can I ask what the *-r* option does? I didn't see it in [the f'in manual](http://www.hmug.org/man/1/mv.php) (and I did read it).

---

### Post by Ben Sprinkle on 2006-10-03
-r=
Rename?
Or Root?

---

### Post by pufuwozu on 2006-10-03
> **aysiu said:**
> nOdl, can I ask what the *-r* option does? I didn't see it in [the f'in manual](http://www.hmug.org/man/1/mv.php) (and I did read it).

It's an invalid option, that's why.

---

### Post by spaced2259 on 2006-10-03
-r according to the manual i have is supposed to be recursive

---

### Post by aysiu on 2006-10-03
A recursive rename of one file...? I'm not sure I know what that means.

---

### Post by Ben Sprinkle on 2006-10-03
What's recruitive mean?

---

### Post by sumguy231 on 2006-10-03
If it was valid, it would only apply to folders.

---

### Post by aysiu on 2006-10-03
> **sumguy231 said:**
> If it was valid, it would only apply to folders.
So you would rename everything within the folder...?

I'm still having trouble conceptually wrapping my head around recursive renaming.

I've moved folders just fine: ```
sudo mv /usr/share/backgrounds /usr/share/backgrounds.old
```

---

### Post by CatKiller on 2006-10-03
> **aysiu said:**
> So you would rename everything within the folder...?

I'm still having trouble conceptually wrapping my head around recursive renaming.

You could potentially rename everything based on some pattern, such as ```
mv B*.bmp L*.bmp
``` and you might want to do that recursively through directories. I have no idea if that particular pattern would work as expected, nor if -r is a valid option, since I've not been at this long, but that is the kind of thing I used to do when I was playing The Sims.

---

### Post by Medieval_Creations on 2006-10-03
I don't think I've ever used -R (recursive) when renaming something.  I mainly use it when copying or to delete an entire directory.

The way I always tried to remember it when I was starting out with Linux is that you use -R (recursive) to change a directory and every file & sub directory within it.

I hope that helps to better explain what recursive is.

Examples: 
Copying an entire folder -
   sudo cp -R /<folder_name>  /<destination>

Deleting a directory -
   sudo rm -R /<folder_name>

Changing the group and owner of a folder & all files contained within -
   sudo chown -R <user_name> /<folder_name>
   sudo chgrp -R <user_name> /<folder_name>

---

