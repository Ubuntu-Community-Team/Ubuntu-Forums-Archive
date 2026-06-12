---
title: "A(nother) way to hide files"
date: 2005-07-07
forum: Absolute Beginner Talk
---

### Post by 6line on 2005-07-07
My problem is this, I have some 500+ web pages saved on my computer, so when I save them they look like this...

example.html
example_files

I normally just hid the _files folder to lessen the clutter by giving it a hidden attribute, but Ubuntu doesn't recognise that and it shows up all my _files folders.
If I put a '.' infront of the file the html links will no longer point to the correct folder.

Is there any other way to hide folders other than putting a '.' infront of the name? Or am I just going to have to bite the bullet and rename them all?

---

### Post by void_false on 2005-07-07
Go other way. Make folder with symlinks to your original *.html files.

---

### Post by poofyhairguy on 2005-07-07
[QUOTE=void_false]Go other way. Make folder with symlinks to your original *.html files.[/QUOTE]

I don't even understand what that means....

---

### Post by 6line on 2005-07-08
erm... yeah, I got that feeling too

---

### Post by ChrisTheGeek on 2005-07-08
The only way to 'hide' files under linux is for the file name to begin with a '.'  There is no hidden attribute.

There is a feature in linux similar to a shortcut in Windows called a symlink.   I think what void_false was suggesting is that you create a new folder containing just symlinks (shortcuts) to your *.html files.  In this new folder only the shortcuts would be visible hence the '_files' files would be hidden - in a way.

Frankly, this seems like more effort than it's worth (unless you know how to write the short shell script that would automate it).  If you have so many files in one directory that the _files are making life harder, then maybe you should consider changing your directory structure instead.

If you want to try the symlink solution, the command is:

ln -s source_file destination_link

---

