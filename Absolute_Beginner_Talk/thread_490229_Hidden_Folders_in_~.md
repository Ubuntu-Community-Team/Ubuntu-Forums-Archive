---
title: "Hidden Folders in ~/"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by waveslider on 2007-07-02
Is there any way I could move all of the hidden folders within my home directory to a new hidden folder, say ~/.hidden, for example, without breaking my system?

I want hidden folders to be visible in Nautilus, but sometimes when you are looking for a particular file or directory, it's annoying to have to scroll through several dozen hidden folders before finding it.

Thanks!

---

### Post by whizbaby on 2007-07-02
NAH dont do it. Instead, veryfy if nautilus accepts keystrokes in folderlists
(e.g. you want to find the folder 'foofolder', open nautilus, hit 'f' . Does it jump to 'f'?)

---

### Post by mcduck on 2007-07-02
Sorry, no.

All the programs are looking for their configuration files from  ~/ and if you move them you will just loose your settings (and the program would most likely just create new files).

---

### Post by nitro_n2o on 2007-07-02
CTRL+H and you'll not see hidden files CTRL+H you can see them back 
Don't miss up with the hidden files in your home folder, you'll just do some big damage :)

---

### Post by waveslider on 2007-07-02
It does, but when I can't remember the name of the file/directory I'm looking for...

Isn't there some way to create a symlink or something that would accomplish what I want?

---

### Post by waveslider on 2007-07-02
Thanks everyone, for the quick replies! Wow

Actually, using Nautilus is not that bad. It's most annoying when opening a file from another program, like firefox, that doesn't seem to respect the hidden folders preference setting in Nautilus. Pressing CTRL+H in Firefox doesn't work, either.

---

### Post by nitro_n2o on 2007-07-02
you can always use the find command in the terminal.. 
so wht do u remember about the file? do u remember its last modification date? it's type?....

---

### Post by whizbaby on 2007-07-02
This is meant for real:
use the terminal for maximum comfort with file operations. Everybody who really has to manage files does it (e.g. I dont use anything else). All it takes is a little time end energy, but dude it rocks to TALK to your machine instead of just mouse-weaving.
):P@nitro

---

### Post by waveslider on 2007-07-02
That's good advice, man. 

Thanks!
waveslider

---

### Post by vanadium on 2007-07-02
Do not move these hidden directories if you want to save yourself a lot of trouble. Instead, if you want easy access to the contents of a hidden directory (.wine/drive_c comes to mind, then create a symbolic link to it from wherever you want to access it (e.g. in your home directory).

---

