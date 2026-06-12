---
title: "Mouse chaser eyecandy"
date: 2006-12-25
forum: Art &amp; Design
---

### Post by m_kylli on 2006-12-25
There is a lot of eye candy available for Linux what with panel applets and desklets. But I was wondering if there's anything like this available.

[http://www.geocities.com/SiliconValley/Haven/4173/neko.html](http://www.geocities.com/SiliconValley/Haven/4173/neko.html)

---

### Post by hikaricore on 2006-12-26
[B]Update: Woops, I guess you can download Oneko from the universe repositories.

```
sudo apt-get install oneko
```

If the above line fails, add:

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

To your */etc/apt/sources.list* file.

```
sudo gedit /etc/apt/sources.list
```
[/B]
----

About the closest thing I can find is this:

[http://members.tripod.com/~so_o2/xmus.html](http://members.tripod.com/~so_o2/xmus.html)

But it no longer seems to work, it makes trails based on the image you set for it to use, didn't check to see if any were animated but I don't think they are.  This program was designed for older versions of X in mind which gave you less options when it came to cursor selection.

Oddly enough, Neko does run under WINE, and even loads a dock icon for itself.

But it does not erase the already drawn cats as you can see in my ["Oh Noes" image here]("http://img.photobucket.com/albums/v414/hikari_corgan/Screenshot.jpg").

---

### Post by m_kylli on 2006-12-26
Great. this is just what I was looking for. Thanks.

---

### Post by saxofoner on 2006-12-27
Hey, um.. It installed, but nothing changed, and running 'oneko' did nothing.  How to fix it?  

I like pc kitties...

---

### Post by hikaricore on 2006-12-27
Hmm I have no with the program running on Ubuntu Edgy.  I'm not sure how the other ubuntu variations work with this application as xubuntu and kubuntu may handle X mouse cursors differently.  Have you tried running:

```
oneko
```

From a terminal and see if it gives an error output.

---

### Post by rykel on 2006-12-28
Simply installing Oneko the Cat from the Ubuntu repositories works for me... (see screenshot)

However, is there a GUI somewhere which can start/pause/stop Oneko somewhere, instead of starting "oneko" from a terminal and leaving the terminal open?

Thanks for telling us about Oneko, it's one lovely cat!!

---

### Post by hikaricore on 2006-12-28
Your best bet would be to just make a desktop or menu entry for it.  You don't need a path in the command box, just type:

```
oneko
```

And give the launcher or menu item a name like "Oneko" for example and you should be good to go :)

As for stopping it, you could make another menu item named "Oneko (stop)" with the command:

```
 killall oneko 
```

The only thing I've noticed with stopping oneko it may drop your mouse cursor back to the default "x" shaped cursor for X.  This can be resolved by opening the options panel for your mouse cursors, but otherwise it's just something silly that bugs me hehe.

p.s. for anyone who didn't notice oneko has options for a cat, dog, and two anime kids, you can see all these options by running:

```
oneko --help
```

From the command line.  There's even options for the color, speed and other attributes of your little mouse pets.  :)

---

### Post by tehweezil on 2009-10-17
This is pretty awesome, Oneko is a fun way to brighten up the desktop :D but is it possible to have it only running on the desktop while the windows are above it?

---

