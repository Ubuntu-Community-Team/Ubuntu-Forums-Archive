---
title: "How to CD dir in terminal"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by ablegreen on 2007-07-03
Ok I'm familiar with windows, where you can go into cmd, and then type

cd c:/whatever

How do I do this in the terminal that comes with Ubuntu? And what's the path to my desktop?

Thanks

---

### Post by Jimmyfj on 2007-07-03
> **ablegreen said:**
> Ok I'm familiar with windows, where you can go into cmd, and then type

cd c:/whatever

How do I do this in the terminal that comes with Ubuntu? And what's the path to my desktop?

Thanks

cd /home/path to the wanted folder

path to your desktop= /home/your_name/desktop

---

### Post by Nekiruhs on 2007-07-03
/home/$USER/Desktop is your desktop. $USER is a variable that contains your username. /home/$USER/ could also be typed as ~

---

### Post by greg_g on 2007-07-03
Well, here are some commands to help you:

"ls" ls lists the contents of the directory
"cd" changes directory, but you have to input the directory name.

So, for an example if you did an "ls" and you got:
Desktop
Folder1
Folder2

you would "cd Folder1" to go to Folder1.  Just typing "cd" will bring you to your "home" directory.  Which is, well, your home on linux.

And "cd .." works the same as it does in Windows.

---

### Post by ablegreen on 2007-07-03
Ok thanks guys!

---

### Post by weblordpepe on 2007-07-03
In Windows everything uses the backslash. But in all other operating systems under the sun....ya use forward slash.

Instead of typing 'dir' to see files. Type 'ls'

Linux/Unix/*nix has a very different directory structure from Windows. The biggest difference is how programs are layed out.
Eg: In Windows, you have a program files folder, then the program folder, then the subfolders.
In Linux, its kinda backwards.

You have the configuration, logs, libraries, binaries, all in main directories.  And program specific stuff is underneath.
Eg:
/etc/X11/xorg.conf

etc means configuration files, the subfolder is X11, then the xorg.conf file.

Your documents & things exist in /home/username
And your desktop is a sub-directory of your documents & stuff eg:
/home/username/Desktop

---

### Post by kwacka on 2007-07-03
As you will have inferred from the other comments, the drive doesn't matter - so c:\home in linux becomes /home.

Little tips: 
cd ..    goes up one tier in the directory, (e.g.  if you're in /home/xyz/documents you'll go to /home/xyx).

if you have a directory with a space (e.g. 'My Programs'):

put a single or double quote at the begininning and end - cd 'My Programs' , or
put in a backslash  cd My\Programs, or
type cd My  then hit the tab key (this only works if there's one file with that name; e.g. cd My <Tab> might take you to 'My Documents' instead')

---

