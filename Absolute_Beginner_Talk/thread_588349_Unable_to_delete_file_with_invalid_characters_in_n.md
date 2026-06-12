---
title: "Unable to delete file with invalid characters in name"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by svdb on 2007-10-23
I have a bunch of directories and files created with Windows on a NAS with Ext2 partitions using Samba.
The files have Japanese, Vietnamese, Portuguese and French characters in their names.

Nautilus says it can't delete these directories and files.
sudo rm -r -f with root privileges says it can't remove these directories and files.

For instance, ls gives the following file name:
```
Sabine Larga?m.mp3
```
Notice the question mark in the file name. It should be an accented character.
using rm produces an error message:
```
sudo rm 02\ -\ Sabine\ Larga\?m.mp3
rm: cannot remove `02 - Sabine Larga?m.mp3': No such file or directory
```

When adding the -f parameter, no error is thrown, but the file is not deleted... :confused:

How can I remove such directories and files?

Thanks.

---

### Post by LaRoza on 2007-10-23
Did you try changing the name? When an icon is selected, press F2.

---

### Post by svdb on 2007-10-23
I can't use Nautilus or any visual tool because when I click the file's icon, it instantly disapears. However when Nautilus refreshes it the icon is back.

---

### Post by Klargodut on 2007-10-23
Try to rename the file using the mv command:

```

mv oldfilename newfilename

```

---

### Post by dimbulb1024 on 2007-10-23
> **svdb said:**
> I can't use Nautilus or any visual tool because when I click the file's icon, it instantly disapears. However when Nautilus refreshes it the icon is back.

Try checking elsewhere in the folder. I have had the problem before of a file that was corrupted or such, when I clicked on it to delete it would reposition itself in the folder (who knows why), but once I found it again I could deal with it.

---

### Post by svdb on 2007-10-23
I just tried mv:
```
sudo mv 02\ -\ Sabine\ Larga\?m.mp3 02.mp3
mv: cannot stat `02 - Sabine Larga?m.mp3': No such file or directory
```

---

### Post by Klargodut on 2007-10-23
Can you try to display it in terminal or does that give the same error?
```

cat filename

```

---

### Post by svdb on 2007-10-23
The problem is: the question mark charater is not the real character but only a substitute character used by Ubuntu to display invalid characters (Potuguese accented character in this example)

---

### Post by svdb on 2007-10-23
```
ls
02 - Sabine Larga?m.mp3
sudo cat 02\ -\ Sabine\ Larga\?m.mp3
cat: 02 - Sabine Larga?m.mp3: No such file or directory
```

---

### Post by svdb on 2007-10-23
I guess I'll just have to use Windows to remove the file... :(

---

### Post by mrog on 2007-10-23
If this is the only file in the directory that starts with "02 - Sabine Larga" then try
rm 02\ -\ Sabine\ Larga*

---

### Post by bodhi.zazen on 2007-10-23
Use quotes : " "

> 
bodhi@VirtualUbuntu:~/test3$ touch file?.mp3
zsh: no matches found: file?.mp3
bodhi@VirtualUbuntu:~/test3$ touch "file?.mp3"
bodhi@VirtualUbuntu:~/test3$ ls
file?.mp3
bodhi@VirtualUbuntu:~/test3$ rm "file?.mp3"
rm: remove regular empty file `file?.mp3'? y
bodhi@VirtualUbuntu:~/test3$ ls
bodhi@VirtualUbuntu:~/test3$

---

### Post by Maestro23 on 2007-10-23
Use quotes. " "

Edit: Bodhi beat me to it.

---

### Post by svdb on 2007-10-23
Thank you all for your help.

I tried all the syntaxes you suggested but still got the "no such file" error.

The real file name was
```
  02 - Sabine Larga'm.mp3
```
but Ubuntu saw it as
```
  02 - Sabine Larga?m.mp3
```
hence typing a question mark in the name while trying to remove/rename it could only spawn an error.

I used Windows on VMware to remove the file without a problem.

Is there a way to have Ubuntu support multiple character page codes? For instance Asian languages in addition to western, without having to change regional settings/keyboard/other ?

Edit: I noticed the different file name only too late.

---

