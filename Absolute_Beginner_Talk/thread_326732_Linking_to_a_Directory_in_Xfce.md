---
title: "Linking to a Directory in Xfce"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by asearle on 2006-12-28
I have just started using Xubuntu and am really pleased with it:  It`s very fast and very simple!

I would like to create links on the desktop and find that I can easily do this with right-click / create launcher.  However, how do I create a link to a directory (rather than to an application)?  I imagine that the `launcher` needs to call file-manager with the name of the directory to be opened.

I just need to know the syntax for the command line.  I`m sure it`s very simple.

And maybe someone can point me towards and good book or tutorial about Xfce (I think I`m converted).

Many thanks,
Alan Searle

---

### Post by pay on 2006-12-28
Open the terminal and type```
man ln
```and that should get  you started.

---

### Post by asearle on 2006-12-28
I tried the 'ln' command but don't think this is what I want:

I just need to create an icon which will call up File Manager at the directory I require.

Maybe all I need is the command for File Manager?  I looked in /usr/bin but couldn't find this executable.

I'm sure that this must be a simple thing.

Many thanks,
Alan Searle

---

### Post by Obor on 2006-12-28
don't know if this is the answer you looking for but did you try the whereis command
i.e for nautilus:
```
~$ whereis nautilus
nautilus: /usr/bin/nautilus /usr/lib/nautilus /usr/X11R6/bin/nautilus /usr/bin/X11/nautilus /usr/share/nautilus /usr/share/man/man1/nautilus.1.gz

```

---

### Post by neowolf on 2006-12-28
So you want to create a link on the desktop that goes to a particular folder?
I'm not entirely sure about XFCE, but in GNOME there is a 'Desktop' directory in the Home folder that contains all icons, you could create a symbolic link here like this.

```

$ cd Desktop
$ ln -s [**WHERE TO LINK TO**] [**LINK NAME**]

```

Or you could create a launcher on the desktop that runs the command `xffm /place/to/link/to`.

---

### Post by pseudonym on 2006-12-28
Do this -

```
cd Desktop
ln -s <name_of _folder> .
```
This creates a symbolic link to the folder specified. An icon will appear on your desktop, and if you right-click and choose 'Open', Thunar file manager will pop up at that location.

As mentioned above, ```
man ln
```
would also be worth a read :)

EDIT - what neowolf said above :)

---

### Post by asearle on 2006-12-28
Yes, this is what I need and the key problem is that I don't know the name of the file manager used by Xfce.  It is titled just 'File Manager' (is there a way to find the name of the underlying executable?).

I went looking for nautilus but could find it and imagine that Xfce uses a different file manager.

Maybe I need an answer specific to XUbuntu?  I might try posting this message in the XUbuntu forum.

Many thanks for your tips.

Regards,
Alan Searle

---

### Post by pseudonym on 2006-12-28
I use Xubuntu. The name of the file manager is 'Thunar' (/usr/bin/thunar). Nautilus is the gnome file manager and xffm is the old xfce file manager.

---

### Post by asearle on 2006-12-28
Yes, that's it.  It is very Xfce- specific.

I used ...

/usr/bin/Thunar /home

To open the thunar (file manager) at the directory /home

Thanks for the tip.

Regards,
Alan Searle

---

