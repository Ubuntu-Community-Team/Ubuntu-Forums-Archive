---
title: "Need help deleting directory from filesystem"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by MeanStreak on 2007-12-17
I know there are several posts regarding this but I'm having no luck so posting a new thread here. 

I have created a folder called My Book (also by mistake one called My Bo) and need to delete them. However sudo rm -r My Book is not working. Please advise. 

> charles@charles-desktop:/media$ ls
cdrom  cdrom0  floppy  floppy0  My Bo  My Book  sda1
charles@charles-desktop:/media$ sudo rm -r My Book
[sudo] password for charles:
rm: cannot remove `My': No such file or directory
rm: cannot remove `Book': No such file or directory

---

### Post by Rocket2DMn on 2007-12-17
The problem is that there is a space, so you need to use what's called an escape character when in the command line.  Otherwise it thinks you are telling it to delete 2 directories by the name of My and Book.  The character you use is \
```
sudo rmdir My\ Book
```
Do be careful with the rm and rmdir commands, they are dangerous,  Please make sure there is nothing of any importance in those directories.

---

### Post by MeanStreak on 2007-12-17
Excellent - thanks for that. I had a feeling the space was causing troubles. I have some very long file name types in that directory - is there a quick way to list them in the terminal? (they are aborted backups I want to clear out)

> charles@charles-desktop:/media/My Book$ ls
2007-12-16_10.24.43.089150.charles-desktop.ful
2007-12-16_15.45.30.806529.charles-desktop.ful
2007-12-16_16.04.12.895727.charles-desktop.ful
2007-12-16_16.14.11.280328.charles-desktop.ful

Better yet - a command to delete both directory + contents?

---

### Post by nowshining on 2007-12-17
if u have a space in the name u need to put half quotes on each end example would be:

My Book

if ur in the directory with the my book folder u input

rmdir -f 'My Book'

---

### Post by Rocket2DMn on 2007-12-17
If you use the recursive rm on the directory it will empty it and delete the directory, you were on the right track before
```
sudo rm -r My\ Book/
```
If you were looking to do specific files, you can also double hit TAB to autofill (once you start typing) or hit TAB twice to see all contents.

---

### Post by nowshining on 2007-12-17
u don't have to do sudo if ur in ur own home folder do u?

---

### Post by MeanStreak on 2007-12-17
Thanks to you both - directories and files are deleted! :)

---

### Post by Rocket2DMn on 2007-12-17
> **nowshining said:**
> u don't have to do sudo if ur in ur own home folder do u?

You only need sudo if you don't own even just one of the files or directories.  He's in /media so everything there should be owned by root:root (otherwise there would be more serious problems),  hence the need for using sudo.  So, in your home directory, you shouldn't need to use sudo.

---

### Post by nowshining on 2007-12-17
if u want to be autoprompted for each deletion 

sudo gedit /etc/bash.bashrc

add the following

#prompt for removal of files/folders in console mode
alias rm='rm -i'
alias cp='cp -i'
alias mv='mv -i'


save and then exit, logout and back in for it to tak effect, so the next time u use those rm commands u get asked if u'd really like to remove them and if so type the letter y and hit the enter key or if not type n and then hit enter to abort for that  file. The samve for copying files via the command line/terminal (cp) and moving files which also is the command to rename them (mv)

---

### Post by nowshining on 2007-12-17
and ur weleome :)

---

