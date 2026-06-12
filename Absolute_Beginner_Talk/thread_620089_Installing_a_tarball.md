---
title: "Installing a tarball"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by RobHK on 2007-11-22
Never successfully installed a tarball yet, but have attempted to read up on it

I downloaded grubed.tar.gz. (Grub Editor). It's on the desktop.

I gave it permission to execute as a program.

I double-clicked and it opened in Archive Manager.

I double-clicked on the README file.

It said "From the terminal, cd to the directory this help file is in, and type:
sudo ./install
Installation from then on is automatic."

Problem is I've no idea how to "cd to the directory this help file is in". I don't know which directory the terminal opens in. Like I said the tarball is on the desktop.

---

### Post by mali2297 on 2007-11-22
Open the terminal and type..
```

tar -xvzf ~/Desktop/grubed.tar.gz
cd grubed
sudo ./install

```

To explain,
..the first command extracts the archive (can also be done with the GUI archive manager),
..the second command change directory to the extracted folder,
..the last command runs the script to install GrubED.

---

### Post by smartbei on 2007-11-22
First you need to untar the archive:
```

tar -xvzf grubed.tar.gz

```
Then follow the README's instructions.

EDIT: mali2297 beat me to it :)

---

### Post by PmDematagoda on 2007-11-22
First type
```
cd ~/Desktop
```

to move to the Desktop folder, then
```

cd the name of the folder on the Desktop
```

then go on with the usual instructions.

---

### Post by zvacet on 2007-11-22
```
cd Desktop
```

```
tar yxvf packagenametar.gz
```

This command will create folder with packagename.You need to go inside.

```
cd /your new folder
```

Now you can run given command.

---

### Post by PmDematagoda on 2007-11-22
Whoa 4 replies in 3 minutes, we may just have set a record here:D. By the way zvacet, you made a typo in 

```
cd /your new folder
```

this will refer to the file being in the / directory not in the Desktop folder, so the command should look like this:-

```
cd your new folder
```

---

### Post by lynnevan on 2007-11-22
[http://sol4.net/compress.shtml](http://sol4.net/compress.shtml)  This guy is great!

This is my bible for the stuff you were talking about.

I picked up on your topic because I was hoping somebody was going to explain how/where to install it so that it doesn't just install itself into it's own little directory - lib files go in /lib executables go in /usr/bin or sbin, docs go in /usr/shared, etc.  Even if you install it in /usr/local, it doesn't look to me like it distributes the files where it should, and it still makes  it's own directory.

Are you sure you want that folder sitting on yr Desktop?:rolleyes:

Hopefully I've made enough of an idiot of myself that someone will straighten me out:confused:

luck

lynnevan

---

### Post by RobHK on 2007-11-22
> **mali2297 said:**
> Open the terminal and type..
```

tar -xvzf ~/Desktop/grubed.tar.gz
cd grubed
sudo ./install

```

To explain,
..the first command extracts the archive (can also be done with the GUI archive manager),
..the second command change directory to the extracted folder,
..the last command runs the script to install GrubED.

Thanks. That worked. So the terminal opens on the desktop? Seems reasonable but different from a Windows command line window. It's these little things that those in the know take for granted that are frustrating when attempting to switch from the Evil Empire.

---

### Post by zvacet on 2007-11-22
@PmDematagoda

You are right.Mea culpa!

---

### Post by mali2297 on 2007-11-22
> **RobHK said:**
> Thanks. That worked. So the terminal opens on the desktop? 

No, it opens in your home directory **/home/yourusername** or **~** for short. The first command however extracted the archive to ~ and you continued from there.

You can check which directory you are in with the command **pwd**. 

The path to your desktop is **~/Desktop**.

---

