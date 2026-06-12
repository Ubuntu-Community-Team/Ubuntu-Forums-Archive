---
title: "NTFS hard drive renaming.."
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by adamkelt on 2006-01-13
Hiya - another newbie question.  I've got my NTFS drives mounted and readable, but I'd like to "rename" them (even just a quick fix that displays a new name on the icon on the Desktop) to relate them to the Windows world.  Essentially, I'd rather my old C: drive be called something that references that as opposed to hda1.  Is this possible?

On a related note, is there a way to create a directory under / that I can make some sort of "shortcut" like thing (also, similar to Windows) to make accing things like pics or what-have-you a little easier for others than myself.  Just a quick, "click here to get to these files" kind of thing...

---

### Post by Mr_Grieves on 2006-01-13
You need the 'ln' command.
[http://theory.uwinnipeg.ca/UNIXhelp/tasks/links2.2.1.html](http://theory.uwinnipeg.ca/UNIXhelp/tasks/links2.2.1.html)

```

sudo ln -s /path/to/mounted/hda1/neat_files /my_windows_drive/neat_files

```
Will do the trick.

---

### Post by adamkelt on 2006-01-13
[QUOTE=Mr_Grieves]You need the 'ln' command.
[http://theory.uwinnipeg.ca/UNIXhelp/tasks/links2.2.1.html](http://theory.uwinnipeg.ca/UNIXhelp/tasks/links2.2.1.html)

```

sudo ln -s /path/to/mounted/hda1/neat_files /my_windows_drive/neat_files

```
Will do the trick.[/QUOTE]
Didn't seem to do it.  Here's what I tried:

```
sudo ln -s /media/hda1 /Windows
```
Nothing happened.  The icon remained hda1 and the Terminal gave no indication that anything happened..  No discernible effect...

---

### Post by Omnios on 2006-01-13
You can mount it with a different name. In /etc/fstab.

 For example I have mine mounted as Documents

 ```
/dev/hda2       /media/Documents    vfat    rw,users,gid=users,umask=000,       0       0
```

 Fist you have to make a file in media to mount it to 

 ```
sudo mkdir /media/New_File_Name
```

 then in the /media/Documents part above put your file name. I use a differnt fstab entry that gives me my name group privalages.

 Also you can make a link to a file within your mount for example I share My Docuemnts Drive between windows and Ubuntu and have a link named doucments in my home directory that links to My Documents within my shared drive bypassing the hard drive overhead such as trash etc. It is also possible to bookmark this file so it showes up in nautilus to save files etc.

 Hope this helps ,Cheers.

---

