---
title: "How to maintain ubuntu?"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by tac603 on 2007-08-24
Hi, I was wondering if it's possible to maintain a clean system. For example if i were to install a bunch of applications and later uninstall them, would there be any leftovers or remnant / orphan files laying around? Is there a way to keep track of them ? In XP I use InCtrl by PC magazine, was wondering if there's a similar program for ubuntu. thanx

---

### Post by swoll1980 on 2007-08-24
gconf cleaner cleans gconf keys (like a win reg cleaner) sudo apt-get autoremove cleans un neaded dependencies

---

### Post by tac603 on 2007-08-24
I'll check it out. thanx

---

### Post by Golyadkin on 2007-08-24
Also, apt keeps copies of every .deb you install in a directory somewhere in /var/cache/apt 
After a month or two this can easily be 500 to 1000MB in size, so you might want to clear that out too. They are only there to make reinstallation easier.

---

### Post by tac603 on 2007-08-24
thanx. Have created a link to that directory on my desktop. :)

---

### Post by aitorcalero on 2007-08-24
There is also an utilitiy called ***deborphan*** that make searches of orphan debfiles. You can then remove the through dpkg -r

---

### Post by tac603 on 2007-08-24
Thanx a lot.. that's really cool. Here's the link for others who are interested. 

[http://packages.ubuntu.com/feisty/admin/deborphan](http://packages.ubuntu.com/feisty/admin/deborphan)

---

### Post by Golyadkin on 2007-08-24
It is preferred to install software from the repositories if it is available there, and deporphan is. You can simply install it by typing
>  sudo apt-get install deporphan 
in the terminal (or search for deporphan in Synaptic Package Manager)

---

### Post by TeaSwigger on 2007-08-24
> **tac603 said:**
> Thanx a lot.. that's really cool. Here's the link for others who are interested. 

[http://packages.ubuntu.com/feisty/admin/deborphan](http://packages.ubuntu.com/feisty/admin/deborphan)

There's also Kleansweep for KDE / Kubuntu in the repositories, a cleanup utility with GUI that lets you screen what's being cleaned first and make safety backups if desired. Handles caches, orphaned files and so forth. :)

---

### Post by aberadam on 2007-08-24
I was told Linux didn't need all this stuff...

---

### Post by swoll1980 on 2007-08-24
who told you that it doesn't need to be defraged nor do you have to run realtime antivirus software in the back round this saves on ram and processor use

---

### Post by cwmoser on 2007-08-24
This thread reminds me of the following saying:

"To mess up Linux, you have to work at it.  To mess up Windows, you have to work with it"

Seriously, since I converted from Windows to Ubuntu, I no longer have to deal with utilities like SYPBOT, ADAWARE, CCLEANER, HIIJACKTHIS, MSCONFIG, modifying the registry, etc.  Then deciding which virus scanner to use - AVG, NORTON, MCAFEE, etc.  Updating these scanner definitions.  Paying annual fees for them.

The grass is indeed greener on the Ubuntu side of the fence :-)

Carl

---

### Post by K.Mandla on 2007-08-24
> **bloor75 said:**
> who told you that it doesn't need to be defraged nor do you have to run realtime antivirus software in the back round this saves on ram and processor use
It doesn't need defragging, but you can if you want. And you don't need a virus scanner unless it's something practical for the system, like if you're handling e-mail attachments that are passed on to Windows machines. Otherwise, all those little chores and tasks that were needed to keep a clean system ... are gone. ;)

---

### Post by asmoore82 on 2007-08-24
> **bloor75 said:**
> g**conf cleaner cleans gconf keys** (like a win reg cleaner) sudo apt-get autoremove cleans un neaded dependencies

NO... this a terrible Idea and a HORRIBLE program ...
all it does is delete gconf keys for programs that aren't actively running ...
you may want to use those programs but just because you weren't
at the time it will screw them up for you.

[COLOR="Red"]**[SIZE="2"]NEVER "clean" your system with applications that did not come through apt/Synaptic!!!![/SIZE]**[/COLOR]

---

### Post by oilchangeguy on 2007-08-24
read this:
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by asmoore82 on 2007-08-24
> **Golyadkin said:**
> Also, apt keeps copies of every .deb you install in a directory somewhere in /var/cache/apt 
After a month or two this can easily be 500 to 1000MB in size, so you might want to clear that out too. They are only there to make reinstallation easier.

good info but there is no need to manually delete files from here, just run ...
```
~ $ sudo apt-get autoclean
```
"autoclean" doesn't nuke the whole thing, just deletes the obsolete files
if you insist on getting rid of everything there, you _still_ don't have to do it manually....
```
~ $ sudo apt-get clean
```
if you insist.

---

### Post by Dabblo on 2008-05-28
> **K.Mandla said:**
> It doesn't need defragging, but you can if you want. And you don't need a virus scanner unless it's something practical for the system, like if you're handling e-mail attachments that are passed on to Windows machines. Otherwise, all those little chores and tasks that were needed to keep a clean system ... are gone. ;)

Wow, I was looking and this sure is cool. I tried some Anti Virus and it said like..:guitar:

---

### Post by Dabblo on 2008-05-28
> **Dabblo said:**
> Wow, I was looking and this sure is cool. I tried some Anti Virus and it said like..:guitar:

To double quote this I run old fashioned WinMX on my machine no problem under wine latest with the help of 3 .dll files as natives and it sure rocks..

---

