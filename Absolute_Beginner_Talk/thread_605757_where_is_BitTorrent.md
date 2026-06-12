---
title: "where is BitTorrent??"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by nikolas68 on 2007-11-07
sorry...it might sound silly...but i can't find my BitTorrent that should be installed!! Where is the link?

---

### Post by carlosjuero on 2007-11-07
I think the BitTorrent link in the Apps menu is hidden by default. To check you can right click the applications menu (in Ubuntu w/ GNOME) and select Edit Menus; in the list click on the Internet sub menu and look for BitTorrent. Check the box beside it to show it.

---

### Post by Inxsible on 2007-11-07
you could also try out a bunch of torrent software which offer a lot of improvements/features over the default BitTorrent install.
some torrent software are
kTorrent
deluge

you can install deluge by```
sudo aptitude install deluge-torrent
```
and ktorrent by ```
sudo aptitude install ktorrent
```

---

### Post by nikolas68 on 2007-11-07
> **Inxsible said:**
> you could also try out a bunch of torrent software which offer a lot of improvements/features over the default BitTorrent install.
some torrent software are
kTorrent
deluge

you can install deluge by```
sudo aptitude install deluge-torrent
```
and ktorrent by ```
sudo aptitude install ktorrent
```

ktorrent looks good.....BUT HOW do you make it the default torrent so that it takes over the downloads automatically??? i can't get it :confused:

---

### Post by Happy_Man on 2007-11-07
Just right-click a torrent file, say "Open With", and choose the app you want.

---

### Post by nikolas68 on 2007-11-08
i would rather have it as default application....and not to "open with" everyetime...SO i do i make Ktorrent my default???

---

### Post by atomkarinca on 2007-11-08
when you select the "open with" option and change it to ktorrent, that makes it default application for torrent files.

---

### Post by nikolas68 on 2007-11-08
> **atomkarinca said:**
> when you select the "open with" option and change it to ktorrent, that makes it default application for torrent files.

sorry guys...feel like an idiot here: where is ktorrent located? I click "Open With" then "Other" then the "Choose helper application" windows appear. Is it in "File System"? Where??

thanks for helping

---

### Post by mcduck on 2007-11-08
Pretty much all executable files for your programs are in /usr/bin. And to make the file always open with your program of choice simple right-click and 'Open With' doesn't work. You need to Right-click, select 'Properties' and in the dialog that opens set the program in the 'Open with'-tab.

---

### Post by DawnDisciple on 2007-11-08
Can someone tell me what 'sudo aptitude' means when translated to English?

---

### Post by meindian523 on 2007-11-08
Super User DO aptitude(Aptitude is the front end for the APT Package Management utility...... )

---

### Post by DawnDisciple on 2007-11-08
Cool, super user being the same a full administrator rights on windows.  And aptitude just being the shop name of Package Management utility.  I bet there are a lot of people never knew this.:)

---

### Post by meindian523 on 2007-11-08
True

---

### Post by DawnDisciple on 2007-11-08
> **meindian523 said:**
> was that sarcasm?

Noooo, thats the second time someone on here has had a go at me just because I'm a little wanting in the brain department.:)
I like to know exactly what I am doing when I do it and that command meant diddle squat to me until now, so now it makes sense, now I know what the command is doing and why.

---

### Post by meindian523 on 2007-11-08
Am sorry.....the tone of the post suggested sarcasm.......just a slight misunderstanding.....

What you can do if you want to know about a particular command is type in terminal
```

man <command_name>
```

That gives you access to the specs of the entire command including options,references to other related commands,etc.....best way to learn about Linux.......search the man pages....:)

edit:BTW,you can find out more about man by simply typing ```
man man
```.....man are the manual pages written by either the developers themselves or someone who really knows the ins and outs of them.....

---

### Post by DawnDisciple on 2007-11-08
> **meindian523 said:**
> Am sorry.....the tone of the post suggested sarcasm.......just a slight misunderstanding.....

***No problem my friend, I am of that age where I can laugh at myself***.:lolflag:

What you can do if you want to know about a particular command is type in terminal
```

man <command_name>
```

That gives you access to the specs of the entire command including options,references to other related commands,etc.....best way to learn about Linux.......search the man pages....:)

***Now that's totally new to me and maybe very helpful, will  be giving that a go, thanks***.

edit:BTW,you can find out more about man by simply typing ```
man man
```.....man are the manual pages written by either the developers themselves or someone who really knows the ins and outs of them.....

.........

---

### Post by meindian523 on 2007-11-08
yeah,I decided that instead of feeding you for a day,I would teach you how to fish......:):lolflag:

---

