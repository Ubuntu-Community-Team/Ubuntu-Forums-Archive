---
title: "[SOLVED] How to Print a List of Folders"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by wayfarer51 on 2007-11-30
Hi, I'd like to know how to do two things:

[LIST=1]
[*]print a list of folders & subfolders and 

[*]to be able to also print a list of the contents of these folders
[/LIST]

Yes, I did look it up on Google and had no luck, and unless it's buried somewhere in the search results for the Forums here, there's no mention of it.

Anyway, I'd appreciate your help.

Thanks,
Neill

---

### Post by quandary on 2007-11-30
here i have you three ways, choose whichever gets closest to what you desire:

i used the folder /root/Desktop as an example

on the terminal, type:
find /root/Desktop/* -type d -print > directorylist.txt
or
find /root/Desktop/* -type f -print > filelist.txt
or
ls -R1 /root/Desktop > output.txt

then type:
gedit directorylist.txt
or
gedit filelist.txt
or 
gedit output.txt

to open the textfiles with gedit.

You can then print the textfile ;-)

type rm directorylist.txt
rm filelist.txt
rm output.txt

to delete the textfiles afterwards.

---

### Post by nick_h on 2007-11-30
You could also use the tree command if you want a more graphical output.  Install it with:
```
sudo apt-get install tree
```
To get a directory listing type:
```
tree -d /dir/path
```
If you want files as well omit the -d option.

You can redirect the ouput as suggested in the previous post.

---

