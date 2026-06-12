---
title: "how to create a shortcut?"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by sallam on 2006-01-24
I've finally managed to view my other partitions! thanks to the wonderful help of this forum.
Now, I need to know how do I create a shortcut to a file located in an old partition?
ubuntu doesnt seem to support the use of the right mouse button to drag and drop, and when I use the left button, it just copies the file where I drop it. Also right-clicking a file brings a menu that doesnt have 'create shorcut' option..
whats 'add link'?

---

### Post by lreyes6 on 2006-01-24
you have to create a launcher... 
right click on desktop and then create a launcher..

---

### Post by frodon on 2006-01-24
There is a command line which allow you to create a symbolic link, it will not copy the file but just create a link to it (it works for directories also) : ```
ln -sf the_file_you_want_to_link The_destination
```If you want a shorcut on the desktop use /home/username/Desktop directory as destination (you might need root access to do that for some files, in this case just add sudo before the command).

---

### Post by sallam on 2006-01-24
Oh God!!
you're saying I need to be a progammer to be able to throw a simple shortcut in my desktop? and I thought ubuntu was for the rest of us poor mouse-happy casual people. No wonder microsoft is still domenating.

---

### Post by jrib on 2006-01-24
You can just use lreyes6 method then, both methods will give you a shortcut on your desktop :)

---

### Post by midwinter on 2006-01-24
Try dragging with the middle button.

---

### Post by frodon on 2006-01-24
[QUOTE=sallam]Oh God!!
you're saying I need to be a progammer to be able to throw a simple shortcut in my desktop? and I thought ubuntu was for the rest of us poor mouse-happy casual people. No wonder microsoft is still domenating.[/QUOTE]lol, typing a line in a terminal does not mean your a programmer, don't see the terminal as a disadvantage because for sure it's one of the most useful thing in linux but you're able to do all without it up to you ;). 
Maybe a simple drag & drop works, a write click on the desktop should also allow you to create a shortcut.

---

### Post by sallam on 2006-01-24
Thanks, I did i!
right-clicked and selected 'create launcher...'
I was disappointed when I found there a line asking for a command! but I realized that selecting 'link' from the drop down menu changed that to browse to my file.
Thanks so much everyone for helping a desperate guy.
ps. "Maybe a simple drag & drop works" it does? how? it only makes a copy of what I drop.

---

### Post by mostwanted on 2006-01-24
[QUOTE=sallam]Oh God!!
you're saying I need to be a progammer to be able to throw a simple shortcut in my desktop? and I thought ubuntu was for the rest of us poor mouse-happy casual people. No wonder microsoft is still domenating.[/QUOTE]

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by Brunellus on 2006-01-24
[QUOTE=frodon]There is a command line which allow you to create a symbolic link, it will not copy the file but just create a link to it (it works for directories also) : ```
ln -sf the_file_you_want_to_link The_destination
```If you want a shorcut on the desktop use /home/username/Desktop directory as destination (you might need root access to do that for some files, in this case just add sudo before the command).[/QUOTE]
A symbolic link is overkill for a user who wants a desktop launcher.  

To the OP:  The little icons that appear on your desktop are "launchers".  "shortcut" is usually Windows-speak for a link of some sort.  Linux has a very powerful set of tools for linking/aliasing, but they are too much for your present needs.

When a more hardened Linux user hears 'shortcut', he is conditioned to think 'symbolic link.'  We blame Microsoft for using the word "shortcut" in a number of different, confusing instances, most notably:

-As a pseudo-symbolic link in their file managers

-As a synonym for "bookmark" or "URL" in Internet Explorer.


To achieve your original objective:  On GNOME (that's regular ubuntu), right click the desktop and choose "new launcher."  

Re: commandline use.  Most of us are accustomed to the command line;  it is a very quick and elegant way of doing things, once you learn it.

---

### Post by galgoz on 2006-01-26
When I create a launcher for a file that is in a directory path that has spaces in the directory name I get a file not found.  How do you format the path when there are spaces in the path?

---

### Post by OtrMan on 2006-01-26
I especially liked Midwinter's suggestion to drag with the middle mouse button.  That was new to me.

Does anyone know why the apt installer doesn't stop to ask configuration questions (like laucher placement)?

---

### Post by purpleturtle on 2006-01-26
I've just been trying to create shortcuts on the Desktop for the first time coincidentally.  I found that if you drag from Nautilus (for e.g.) onto the Desktop  with the left mouse button, and before releasing, pressing ctrl and/or shift gives you the option to move, copy or link (like Windows).

I prefer the middle click approach, but the ability to change the behaviour of a left click drag is useful if you've already started the maneuver without considering that you might want to move or link rather than copy.

---

