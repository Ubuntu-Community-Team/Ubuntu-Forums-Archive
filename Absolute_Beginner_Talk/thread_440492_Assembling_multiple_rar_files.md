---
title: "Assembling multiple rar files"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by roger123 on 2007-05-11
Does anyone know how to assemble multiple files that are in rar format?  I downloaded an episode of a TV show as a bit torrent, and unexpectedly, it contains like 40 rar files.  I'm told that I can use WinRAR to assemble them into one file, but is there a way to do that in Ubuntu?

---

### Post by bashologist on 2007-05-11
# Install unrar:
sudo apt-get install unrar

# Then unrar the file with:
unrar x *.rar

# The *.rar should expand to just one file. So, if you have files *.r00, *.r01, *.r02, *.rar ...

---

### Post by nab on 2007-05-11
If you prefer a gui you can install ark:
```
sudo apt-get install ark
```

If I remember right you have to right click on the first part of the file to extract.

---

### Post by bashologist on 2007-05-11
It's a kde program so if installing this it would probably come with many dependencies and stuff. If it works then it might be a good idea for kde users.

---

### Post by taurus on 2007-05-11
All you have to do is to unpack the first one and it will automatically unpack the rest.

```
unrar x filename.part01.rar
```

---

### Post by mcduck on 2007-05-11
In Gnome, install unrar, then right-click on the first file of the archive and select 'Extract Here'. All files will be extracted automatically.

---

### Post by roger123 on 2007-05-11
> All you have to do is to unpack the first one and it will automatically unpack the rest.

That did it.  I knew it would be something simple like that.  Thanks

---

### Post by go_beep_yourself on 2007-11-04
How can a rar archive made of multiple files be created in Linux?

---

### Post by mali2297 on 2007-11-04
> **go_beep_yourself said:**
> How can a rar archive made of multiple files be created in Linux?

See here:
[http://ubuntuforums.org/showthread.php?t=546135](http://ubuntuforums.org/showthread.php?t=546135)
[http://ubuntuforums.org/showthread.php?t=556756](http://ubuntuforums.org/showthread.php?t=556756)

EDIT:
The above is for making a split archive. If you want to make **one** archive of several files, just type;
```

rar a name_of_archive name_of_file_1 name_of_file_2 name_of_file_3

``` 
etc. It is probably easy with a GUI archiver as well.

---

