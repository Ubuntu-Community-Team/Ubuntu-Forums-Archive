---
title: "Eager newbie with silly questions"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by Bsranger on 2006-06-07
Hey guys! I've just made the conversion to linux from windows and i have alot of learning to do. The first question i have is how to have programs appear in the dropdown list under applications. I would like to run bitorrent to look at it, but it is not under the internet listing. The add programs menu says its installed. Is there a way to make it easy to get to from the gui? Also Ive read alot of the help sections and you guys are great at posting what us new guys need to put into console. I am running into the problem that i get the results i want but i dont understand what i just put it. Is there a resource out there that would allow linux illiterate users to learn the language so to speak? BTW im using dapper.

---

### Post by Nequeo on 2006-06-07
[QUOTE=Bsranger]Hey guys! I've just made the conversion to linux from windows and i have alot of learning to do. The first question i have is how to have programs appear in the dropdown list under applications. I would like to run bitorrent to look at it, but it is not under the internet listing. The add programs menu says its installed. Is there a way to make it easy to get to from the gui? Also Ive read alot of the help sections and you guys are great at posting what us new guys need to put into console. I am running into the problem that i get the results i want but i dont understand what i just put it. Is there a resource out there that would allow linux illiterate users to learn the language so to speak? BTW im using dapper.[/QUOTE]

Just right click on top of the menu (the Ubuntu symbol/Applications menu - don't open up the menu first) and select 'Edit Menu'. 

Bittorrent probably already has a meny entry that is just hidden. You can probably enable it by finding it in the 'Internet' section and ticking the box.

You can also use the menu editor to add your own entries - but any programs you install using the 'Add/Remove Programs' program will put their own entries in the menu automatically.

Cheers,

---

### Post by nalmeth on 2006-06-07
In a terminal, type 
killall gnome-panel

it will restart the panel, possibly with the new applications listed.

Read my *learn the terminal* link for some guides, ranging on technical level.

Welcome to Ubuntu!

---

### Post by Bsranger on 2006-06-07
thank you very much guys!!!

---

### Post by Nequeo on 2006-06-07
[QUOTE=nalmeth]In a terminal, type 
killall gnome-panel

it will restart the panel, possibly with the new applications listed.

Read my *learn the terminal* link for some guides, ranging on technical level.

Welcome to Ubuntu![/QUOTE]

With Ubuntu 6.06 you don't need to do this anymore. In version 5.04 and earlier you did... Maybe 5.10, I can't remember. But in Ubuntu 6.06 the menu will show new entries without needing to be killed and restarted.

Btw, if you're interested in poking around the scenes, all menu entries are just text files ending in '.desktop' that sit the folder /usr/share/applications. If you browse to that folder and open a few of those files in a text editor, you'll quickly see what's going on. 

[EDIT]
One more thing. As far as 'learning the language' is concerned, I definately reccomend reading through the Ubuntu User Guide, which you can find in the 'System--->Help--->System Documentation' menu. Read it cover to cover, and you'll be way ahead of the game! 

I work in Tech Support - and I would hazard a guess that the majority of support calls we get are the result of people not reading anything that appears on the screen in front of them. 

Never click on a box without reading the message first, and don't be afraid to enter some text from any error message you get into Google, and you'll be laughing. 
[/EDIT]

Cheers,

---

