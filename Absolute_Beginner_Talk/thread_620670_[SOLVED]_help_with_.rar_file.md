---
title: "[SOLVED] help with .rar file"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by fiskking on 2007-11-22
downloaded file .rar file and used command in terminal to get a rar manager

sudo apt-get install rar
sudo ln -fs /usr/bin/rar /usr/bin/unrar

when I tried to extract the .avi file it gives this error:

Write error in the file /home/fisk/Desktop/cam-oldmen.avi [R]etry, [A]bort 
Write error in the file /home/fisk/Desktop/cam-oldmen.avi
Inappropriate ioctl for device

---

### Post by moffa on 2007-11-22
Why did you:  sudo ln -fs /usr/bin/rar /usr/bin/unrar

I'd remove it and ```
 sudo apt-get install unrar 
```

then ```
 unrar e filetounrar.rar 
```

make sure you use select the rar file not the file to be extracted.

---

### Post by fiskking on 2007-11-22
thanks moffa,  I found the line from here:  

[http://www.ubuntux.org/how-to-install-rar-archiver-rar](http://www.ubuntux.org/how-to-install-rar-archiver-rar)

How do I remove this line?

---

### Post by taurus on 2007-11-22
```
sudo rm /usr/bin/unrar
sudo apt-get remove rar
sudo apt-get update
sudo apt-get install unrar
```

---

### Post by fiskking on 2007-11-22
thanks guys for the help...

received this in terminal:

fisk@RaneYisrael:~$  unrar e cam-oldmen.rar

UNRAR 3.70 beta 3 freeware      Copyright (c) 1993-2007 Alexander Roshal

Cannot open cam-oldmen.rar
No such file or directory
No files to extract


the .rar files are located in a specific directory/file

---

### Post by taurus on 2007-11-22
Where did you save those files to?  You need to be in the same directory or you need to include the whole path.

```
ls -la ~/Desktop
```

---

### Post by nikoPSK on 2007-11-22
unrar e file.rar

I think you gotta be in the directory of the rar file (say desktop)

---

### Post by fiskking on 2007-11-22
yeah I just realized this.  It sucks being a noob.

Thanks guys for the help

---

