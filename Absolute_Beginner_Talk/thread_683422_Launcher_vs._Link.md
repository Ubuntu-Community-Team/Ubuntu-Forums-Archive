---
title: "Launcher vs. Link"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Niniel on 2008-01-31
Here's a nice n00bish question for you - why do we have links _and_ launchers? Seems to me those are pretty much the same. Or not?

---

### Post by wolfen69 on 2008-01-31
by links i assume you mean desktop "shortcuts". some people may prefer an uncluttered desktop, therefore we have launchers. but yes, they are essentially the same.

---

### Post by TheOrangePeanut on 2008-01-31
I'm curious myself.  I didn't even know we had links :)

---

### Post by dcstar on 2008-01-31
> **wolfen69 said:**
> by links i assume you mean desktop "shortcuts". some people may prefer an uncluttered desktop, therefore we have launchers. but yes, they are essentially the same.

No, a "link" is a pointer to a file or a directory, a "launcher" is something that contains a command or URL.

Something may launch when you use a link, but that is only because your computer has a setting to do something when a particular link type is opened.

---

### Post by vanadium on 2008-01-31
A launcher is "gnome specific" and can be compared to the MS Windows shortcuts (for those who have still some familiarity with that OS). It offers quick access to a document, a folder or an application somewhere on your system. It only exists on the desktop.

A link is a reference to a file or a directory that very much in itself acts like the file or directory. It exists at the file system level, and therefore is functional everywhere. In fact, links allow you to rearrange your system in another way without having to physically move or copy files.

Suppose you have your music directory on a separate partition in /media/music. If you create a launcher on your desktop to /media/music, then clicking the launcher will open a nautilus window pointing to "/media/music". If instead you create a link on your desktop, then you obtain the same effect as if you would have moved the /media/music folder to the Desktop folder (/home/$USER/Desktop). Clicking the link will now open a nautilus window pointing to /home/$USER/Desktop/music. With the link, it is as if your data would exist in two different locations, /media/music and /home/$USER/Desktop/music.

---

### Post by mcduck on 2008-01-31
Actually we have launchers and then 2 different types of links, hard links and symbolic links. ;)

Just like dcstar said, launcher is used to run commands or open URL addresses, while link just points to a single file.

Launcher is actually a text file that contains information about what command or URL you want it to start, the name and tooltip information about the launcher, what icon it should use and so on. Launchers are used in panels, menus and for desktop icons, but they do not work from command line, they are just for GUI purposes.

Here's what a launcher looks like when opened in text editor:
```

[Desktop Entry]
Encoding=UTF-8
Name=Text Editor
Comment=Edit text files
Exec=gedit %U
Terminal=false
Type=Application
StartupNotify=true
MimeType=text/plain;
Icon=accessories-text-editor
Categories=GNOME;GTK;Utility;TextEditor;
X-GNOME-DocPath=gedit/gedit.xml
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gedit
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.20.3
X-GNOME-Bugzilla-ExtraInfoScript=/usr/lib/gedit-2/gedit-bugreport.sh
X-Ubuntu-Gettext-Domain=gedit
```

Hard link gives you a link to a single file, so opening the link will open the file it's pointing at. If the original file is moved, the link will also change to point to the new location. If the original file is removed, the link will still work and you can use it to open the file. So hard link is just adds a new filename for the same actual file on your disk. Hard links cannot link to directories or to different file systems, like other disks.

Symbolic link points to a single file or single directory. They are also able to point across file system boundaries. If you move the original file symbolic link will just break and stop functioning as they are not updated like hard links are.

Both types of links are features of Unix/Linux operating systems, and they work from command line and do not depend on any additional software like desktop environments.

Here's a quick introduction to how these links work from a terminal:

First, we'll create a simple text file to play with:
```

mcduck@Hyperion:~/Desktop/links$ echo "text 1" > file1.txt
mcduck@Hyperion:~/Desktop/links$ ls
file1.txt
mcduck@Hyperion:~/Desktop/links$ cat file1.txt 
text 1
```
The file is called "file1.txt" and contains text "text 1".

Next let's create a hard link for it:
```

mcduck@Hyperion:~/Desktop/links$ ln file1.txt file2.txt
mcduck@Hyperion:~/Desktop/links$ ls
file1.txt  file2.txt
mcduck@Hyperion:~/Desktop/links$ cat file2.txt 
text 1
```Hard link is made with the 'ln'-command, and reading the link outputs contents of the original file.

Then we'll make a symbolic link as well:
```

mcduck@Hyperion:~/Desktop/links$ ln -s file1.txt file3.txt
mcduck@Hyperion:~/Desktop/links$ cat file3.txt 
text 1
mcduck@Hyperion:~/Desktop/links$ ls
file1.txt  file2.txt  file3.txt
```Symbolic lninks can be made with "ln -s" and as you can see it works just like the hard link did.

Here's what happens when we rename the original file:
```

mcduck@Hyperion:~/Desktop/links$ mv file1.txt newfile.txt
mcduck@Hyperion:~/Desktop/links$ ls
file2.txt  file3.txt  newfile.txt
mcduck@Hyperion:~/Desktop/links$ cat newfile.txt 
text 1
mcduck@Hyperion:~/Desktop/links$ cat file2.txt 
text 1
mcduck@Hyperion:~/Desktop/links$ cat file3.txt 
cat: file3.txt: No such file or directory

```Hard link still works just like before, but the symbolic link is now broken as it can't find the file it was made to point at.

Now let us remove the original file completely and see what happens to our links:
```
mcduck@Hyperion:~/Desktop/links$ rm newfile.txt 
mcduck@Hyperion:~/Desktop/links$ ls
file2.txt  file3.txt
mcduck@Hyperion:~/Desktop/links$ cat file2.txt 
text 1

```Opening the hard link gives the contents we put in the original file, even though the file was removed.

You can also create symbolic links in the file manager by dragging a file or directory to a new place with middle mouse button, and then selecting "Link Here" from the popup menu.

---

