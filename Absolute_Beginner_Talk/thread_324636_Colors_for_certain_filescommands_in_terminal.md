---
title: "Colors for certain files/commands in terminal?"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by pjones0404 on 2006-12-24
a friend of mine had shown me away that you can enable a color sheme to the listings in terminal after running ls. 

it would show directories as a certain color and then show other commands or things as yet another color. this would allow me to quickly know what I could do in a certain directory. I am still learning and sometimes i try to navigate via termainal and get messages that i can not "cd" to something since it is not a directory. 

does anyone know how to enable this. i looked around and all i could find is to change the transperancy and also how to change the color of everything, but not a way to color things differently depending on what it is/does.

---

### Post by tommcd on 2006-12-24
Those ccolors should be enabled by default. cd into different directories via the terminal and you should see files as black, folders as blue, etc. If you don't have that I don't know how to enable it, but you should already have it.

---

### Post by pjones0404 on 2006-12-24
they are color coded. :oops: 

is there a breakdown of what each color is? are they editable? :-k 

 i appreciate the quick response.

---

### Post by po0f on 2006-12-24
pjones0404,

White (or black, depending on color scheme) = regular file
Blue = directory
Green = executable
Pink/purple = media (music, pictures, movies) or socket files
Red = archive files (tarballs, ZIPs)
Cyan = symlinks
Yellow = device files

Green background = 777 permissions
Red background = broken symlink

---

### Post by pandu.rs on 2006-12-24
if it already enabled it is good. otherwise u can enable it by creating an alias in ur ~/.bash_profile as follows

alias ls='ls --color=auto'

---

