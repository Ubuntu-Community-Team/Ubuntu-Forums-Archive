---
title: "Setting prefered applications..."
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by azmansell on 2006-05-18
Hi there,
does anyone know how to set prefered applications (browser, email client etc) in Kubuntu.

cheers!

---

### Post by louis_nichols on 2006-05-18
You'll find them here: Open Control panel>KDE Components>Component chooser

Good luck!

---

### Post by azmansell on 2006-05-18
[QUOTE=louis_nichols]You'll find them here: Open Control panel>KDE Components>Component chooser

Good luck![/QUOTE]

I can find KDE Components (in system settings though) but it dosent give me options for component chooser. am i missing a vital bit of software?

p.s. im on 5.10 breezy if that helps at all?!?!

cheers!

---

### Post by louis_nichols on 2006-05-18
Strange. The version of Kubuntu doesn't matter, because KDE is independent of that. kde's control center (or system settings, or whatever they call it) has always had this option, ever since I first used it almost 2 years ago.

Try this then: launch the application **kcontrol** from terminal and you should find it there. It should look something like this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=9658&stc=1&d=1147961426[/IMG]
. Now, dependending on your settings, you might have icons instead of the tree/list system I have, but should find the same structure.

Now, if it's not there either, then it may mean you're missing some package, although I can't imagine how, because I didn't install it separatelly, it just came with all the default things when I wanted to install k3b and krusader.

---

### Post by azmansell on 2006-05-18
[QUOTE=louis_nichols]Strange. The version of Kubuntu doesn't matter, because KDE is independent of that. kde's control center (or system settings, or whatever they call it) has always had this option, ever since I first used it almost 2 years ago.

Try this then: launch the application **kcontrol** from terminal and you should find it there. It should look something like this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=9658&stc=1&d=1147961426[/IMG]
. Now, dependending on your settings, you might have icons instead of the tree/list system I have, but should find the same structure.

Now, if it's not there either, then it may mean you're missing some package, although I can't imagine how, because I didn't install it separatelly, it just came with all the default things when I wanted to install k3b and krusader.[/QUOTE]


That works a treat!
your a star!!!

a couple of extras though just to be cheeky...
what is the easiest way to add this to my panel?

and one that may challenge you a bit...

when i try to send something to the wastebasket i get the following error...

"could not make folder /home/azmansell/.local/share/Trash."

any ideas? it worked fine in ubuntu (which i have just upgraded to)

nice one

---

### Post by louis_nichols on 2006-05-18
[QUOTE=azmansell]

what is the easiest way to add this to my panel?[/QUOTE]

I guess you'd just have to add a launcher for an application with command **kcontrol**. I don't remember whether it is already in the panel shortcuts menu and I can't check because I haven't installed kde on this last setup I have.


[QUOTE=azmansell]and one that may challenge you a bit...

when i try to send something to the wastebasket i get the following error...

"could not make folder /home/azmansell/.local/share/Trash."

any ideas? it worked fine in ubuntu (which i have just upgraded to)

nice one[/QUOTE]

It is indeed a strange situation. I never use trash or wastepasket so I can't have encountered it. See if creating the folder yourself helps:

```
mkdir /home/azmansell/.local/share/Trash
```

although, to my knowledge, the path for trash would have to be
```

/home/azmansell/.Trash
```

so I don't know why kde would look for it there. You might wanna try just a symlink:

```
ln -s /home/azmansell/.Trash /home/azmansell/.local/share/Trash
```

---

### Post by azmansell on 2006-05-19
Just tried these but still no good.

how do you normally delete files then? sounds more effecient if its your prefered way of doing things!

---

### Post by dmizer on 2006-05-19
[QUOTE=azmansell]how do you normally delete files then? sounds more effecient if its your prefered way of doing things![/QUOTE]
just click on the file so it's highlighted and hit the 'del' key on the keyboard.

heh ... it's not that simple huh?  same problem.

try this:
open konqueror and go to settings -> configure konqueror
there you can set the prompt when deleting files. you can also activate the "show 'Delete' context menu..." to bypass the trashcan

this way, when you delete a file, it just doesn't go to trash.  it just deletes.  kind of eliminates that safety net, but at least you can delete files.  just make sure you REALLY want to delete them when you do ... lol

---

### Post by azmansell on 2006-05-19
[QUOTE=dmizer]just click on the file so it's highlighted and hit the 'del' key on the keyboard.[/QUOTE]

hitting 'del' gives me the same error as before.

ive managed to delete the files i wanted using the rm command so all is ok for now, although i would like to get the wastebasket working (purely because im lazy!)

cheers!

---

### Post by dmizer on 2006-05-19
yeah ... sorry, i realized that after i posted.  still not sure how to get your wastebasket to work, but if you see my edited post, you can disable the wastebasket so files are just deleted instead of going to the wastebasket first.

---

### Post by azmansell on 2006-05-19
[QUOTE=dmizer]yeah ... sorry, i realized that after i posted.  still not sure how to get your wastebasket to work, but if you see my edited post, you can disable the wastebasket so files are just deleted instead of going to the wastebasket first.[/QUOTE]

That works a treat.. nice one!

by the way, louis, cheers ive got kcontrol onto my panel by right clicking> add to panel> applets> quick launcher.

This put 3 little icons on my panel (konsole, control centre ,help)

so thats sorted.. cheers both!

---

