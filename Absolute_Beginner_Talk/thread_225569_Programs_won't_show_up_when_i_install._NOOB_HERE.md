---
title: "Programs won't show up when i install. NOOB HERE"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by David123 on 2006-07-29
When i install a program from the Synaptic Package Manager, it doesnt show up  
in the applications list. Please help. I barely switched to Ubuntu a week ago.:(

---

### Post by chickengirl on 2006-07-29
Which program is it? Try typing its name in a terminal. Also try logging out and back in, that sometimes makes MIA menu items show up.

---

### Post by Clay85 on 2006-07-29
> **David123 said:**
> When i install a program from the Synaptic Package Manager, it doesnt show up  
in the applications list. Please help. I barely switched to Ubuntu a week ago.:(

I keep having the same problems and everyone tells me, 'Oh, just install alacarte/gmenusomethingorother/debian'. But, guess what? I CAN'T FIND THOSE EITHER!

When you find out how to install things, come teach me. :(

I've found that sometimes if I mess around in Applications --> Add/Remove... or if I mess around with Applications --> System Tools --> Menu Editor I can find some programs that weren't there before. If you know the name of the program type ALT+F2 and type in the name. That's how I get around 'not being able to find' programs most of the time.

---

### Post by Sweet Spot on 2006-07-29
So far, whenever I've updated from the repository list, a pop up has told me to re-boot in order for things to take effect. That could be one way of determining what is there or not. (I've only been using Ubuntu for a few days myself. Hell, Linux in general.) Also, a lot of things are usually stored in the "home" folder, which you should have a separate partition for. 

I'm not quite up to snuff with how to manage this directory structure, or how to ever find things either, and am trying to maintain my patience, which is sometimes hard. I'm actually compiling a list of things that I need answers to, that I can't find (I always search). So far though, Ubuntu is pretty cool, with just a few minor annoyances and misbehavioral patterns.

---

### Post by David123 on 2006-07-29
I typed some names of programs i tried to install, but all it showed me was info about the program. I cheked the applications menu again........nothing.

---

### Post by Rumor on 2006-07-29
Alacarte menu editor should be installed by default under Applications > Accessories.

Select it and then highlight the categfory you want your new program to appear. Let's say you've installed pysol, a solitaire card game and it didn't show up. 

You'd highlight games, then click File > Add Entry

You'd name your new program, type in the command for it, 'pysol' in this case and then find an icon for it that you like. 

Click ok, and your program is now in the menu.

---

### Post by catlett on 2006-07-29
The executable binaries for applications are stored in /usr/bin. This is not the normal way to access an app but you can start an app by going to /usr/bin and double clicking on the binary. Places<Computer<Filesystem<usr<bin
You can always create a launcher that points to the binary as well. Right click on the desktop and select "add launcher". Write in the name of the application etc then at command browse to the binary in /usr/bin.
The "whatchamacallit" referred to in a previous post is "Alacarte Menu Editor". Go to Applications<Accessories<Alacarte menu editor. On the left is a list of categories that are in yout top panel menu. When you select one a list appears on the right side. The programs already in the menu are checked off. Programs that aren't on the menu are unchecked. Just check off an entry you want in the menu.
The second "whatchamacallit" mentioned anove was the Debian menu. This is a menu that gets added to the top panel menu under Applications. It lists many more applications than the regular gnome menu. You install it with these commands.
```
sudo apt-get install menu-xdg 
```
```
sudo apt-get install menu
```After a restart, it will appear under applications as Debian.

---

### Post by Clay85 on 2006-07-29
I'm really shocked. Debian is actually working. Before it was greyed out and I couldn't click it. Thanks! 

Also, no one called anything a whatchamacallit, so who are you quoting?

---

### Post by David123 on 2006-07-29
[SIZE="4"]Thanks Guys, the programs show up now....thank god for ubuntu geeks....[/SIZE]

---

### Post by Frank Golden on 2006-07-30
> **catlett said:**
> 
The second "whatchamacallit" mentioned anove was the Debian menu. This is a menu that gets added to the top panel menu under Applications. It lists many more applications than the regular gnome menu. You install it with these commands.
```
sudo apt-get install menu-xdg 
```
```
sudo apt-get install menu
```After a restart, it will appear under applications as Debian.
Thanks Catlett,
I had the debian menu on an earlier install but forgot how I got it.
I guess I should keep a journal.

---

### Post by srikat on 2006-07-30
"I guess I should keep a journal."

A very good idea. I'm very new to Ubuntu and to Linux in general. I've started a free wiki at tiddlyspot.com and jotting down whatever am learning. 

[http://tiddlyspot.com/ubuntu/index.html](http://tiddlyspot.com/ubuntu/index.html)

I suggest you to sign up at tiddlyspot.com. It's fast and free to have a diary where you can save useful stuff.

---

### Post by Frank Golden on 2006-07-30
> **srikat said:**
> "I guess I should keep a journal."

A very good idea. I'm very new to Ubuntu and to Linux in general. I've started a free wiki at tiddlyspot.com and jotting down whatever am learning. 

[http://tiddlyspot.com/ubuntu/index.html](http://tiddlyspot.com/ubuntu/index.html)

I suggest you to sign up at tiddlyspot.com. It's fast and free to have a diary where you can save useful stuff.
Hi srikat,
   Looks like you have had very few problems with Ubuntu. Same here.
Great distro, eh.

---

### Post by srikat on 2006-07-30
You are right. No probs w/ Ubuntu itself...but since am on 64bit I see discrimination from my favorite browser, Opera.

(See [http://www.ubuntuforums.org/showthread.php?p=1316394](http://www.ubuntuforums.org/showthread.php?p=1316394))

I am thinking about installing a 32 bit Ubuntu on this AMD Athlon 64 thus wiping my current install :(

---

### Post by catlett on 2006-07-30
> **Clay85 said:**
> I'm really shocked. Debian is actually working. Before it was greyed out and I couldn't click it. Thanks! 

Also, no one called anything a whatchamacallit, so who are you quoting?

'Oh, just install alacarte/gmenusomethingorother/debian"
Close enough.

---

