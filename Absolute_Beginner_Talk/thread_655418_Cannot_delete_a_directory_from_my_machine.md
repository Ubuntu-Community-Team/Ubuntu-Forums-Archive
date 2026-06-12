---
title: "Cannot delete a directory from my machine"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by kvorion on 2008-01-01
I happened to extract some code samples from google android on my machine. I did this on my ntfs drive while I was using windows XP. It so happened that when the archive was extracted, the folder hierarchy that was created was very deep and sort of recursive. I have one folder called NotepadCodeLab which has another folder called NotepadCodeLab and this goes on for several levels. 
When I tried to delete this directory from windows explorer it said that the directory naming hierarchy is too long and it simply refused to delete the folders. So I booted into Ubuntu and tried. I mounted the NTFS partition into /mnt/e and navigated into the directory. 

```

su
mount -t ntfs /dev/sda5 /mnt/e
cd /mnt/e

```



When I do

```

sudo rm -r NotepadCodeLab/

```

I get several errors:
```

rm: cannot remove directory `NotepadCodeLab//New Folder/Notepadv1/Notepadv1/1/1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/.metadata/.plugins/org.eclipse.jdt.ui': Read-only file system
rm: cannot remove directory `NotepadCodeLab//New Folder/Notepadv1/Notepadv1/1/1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/.metadata/.plugins/org.eclipse.ui.ide': Read-only file system
rm: cannot remove `NotepadCodeLab//New Folder/Notepadv1/Notepadv1/1/1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/.metadata/.plugins/org.eclipse.ui.workbench/workingsets.xml': Read-only file system
rm: cannot remove `NotepadCodeLab//New Folder/Notepadv1/Notepadv1/1/1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/.metadata/version.ini': Read-only file system
rm: cannot remove `NotepadCodeLab//New Folder/Notepadv1/Notepadv1/1/1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/.project': Read-only file system
rm: cannot remove `NotepadCodeLab//New Folder/Notepadv1/Notepadv1/1/1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/Notepadv1/AndroidManifest.xml': Read-only file system


```

and so on....

How do I delete these folders? Please help

---

### Post by taurus on 2008-01-01
How did you mount that ntfs partition?  Did you use ntfs-3g driver or did you just use ntfs?  If you want to write or delete stuff in ntfs partition, you need to use ntfs-3g driver instead.

Maybe that's why you get the read-only filesystem when you mounted it with ntfs driver.

---

### Post by kvorion on 2008-01-01
I mounted again using ntfs-3g and tried to delete. This time there was no message, but the rm command just did not return for a very long time. I terminated the rm command and deleted the folder using nautilus.
One question: When I say move to trash, to which trash does that content go? Does it go to the recycle bin my windows OS? Cos I had nothing in my trash folder.

---

### Post by taurus on 2008-01-01
Look in /root/.Trash.  Also, check your ~/.Trash as well.

```
ls -la ~/.Trash
sudo ls -la /root/.Trash
```

---

### Post by kvorion on 2008-01-01
Couldnt find it in either place, but what I wanted to delete is gone.

---

