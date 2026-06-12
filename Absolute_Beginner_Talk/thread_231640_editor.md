---
title: "editor"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by dirkdekker on 2006-08-07
New in Ubuntu and like tochange the # lines in sources.list but ca'n find any commandline statement for EDIT !!
Please help. Where do I find an editor programm?
Dirk

---

### Post by wjp.reg on 2006-08-07
> **dirkdekker said:**
> New in Ubuntu and like tochange the # lines in sources.list but ca'n find any commandline statement for EDIT !!
Please help. Where do I find an editor programm?
Dirk

sudo gedit /etc/apt/sources.list

---

### Post by cantormath on 2006-08-07
> **dirkdekker said:**
> New in Ubuntu and like tochange the # lines in sources.list but ca'n find any commandline statement for EDIT !!
Please help. Where do I find an editor programm?
Dirk

are you using vi?
if you are you need to type i, the move around, change it, then hit esc, then <shift>+<;>, then wq to save/exit.

You might want to try nano if you are gonna edit via command line.

I usually use gedit to edit sources.list:

```
sudo gedit /etc/apt/sources.list[/CODE
That is like notpad in windows, you might find that alot easier.

also, you can edit sources via menu:
System>Administration>Software Properties.
thats as easy, and as gui as it gets.  

dont forget, if you are gonna change the source, either update in synaptic or in terminal
[CODE]sudo apt-get update
```
before looking for stuff to install.
Be careful when you do updates too, the universe and backports arent as tested as the stuff in the repositories you started with.  

Good luck

---

### Post by dirkdekker on 2006-08-07
thanks, put in the line after the command prompt :
sudo gedit /etc/apt/sources.list
result:
sudo: gedit: command not found.

(btw: iis is a server installation 5.10 breezy)

---

### Post by cantormath on 2006-08-07
> **dirkdekker said:**
> thanks, put in the line after the command prompt :
sudo gedit /etc/apt/sources.list
result:
sudo: gedit: command not found.

(btw: iis is a server installation 5.10 breezy)

are you using kubuntu?.......with kde?

try
```
sudo kate /etc/apt/sources.list
```

if you are on ubuntu, with gnome, install gedit....
```
sudo apt-get install gedit
```

However, I thought gedit came on the install of dapper.

---

### Post by aysiu on 2006-08-07
*sudo kate* won't work.

If you want to use Kate, do ```
kdesu kate /etc/apt/sources.list
```

---

### Post by cantormath on 2006-08-07
> **aysiu said:**
> *sudo kate* won't work.

If you want to use Kate, do ```
kdesu kate /etc/apt/sources.list
```

ahhh! your right! duh.......
I dont use kubuntu.....damnit to kde ::grin::

```
kdesu kate /etc/apt/sources.list
```

---

### Post by wjp.reg on 2006-08-07
There's also nano ..

sudo nano /etc/apt/sources.list

---

### Post by dirkdekker on 2006-08-07
No it is a simple server installation without any extra's.
I did this: sudo apt-get install gedit
and got a lot of installations over the screen.!!!
ending with: setting up gedit (2.12.1-0ubuntu1)
And that all for a simple commandline editor???
Who knows?
dirk

---

### Post by davebgimp on 2006-08-07
> **dirkdekker said:**
> No it is a simple server installation without any extra's.
I did this: sudo apt-get install gedit
and got a lot of installations over the screen.!!!
ending with: setting up gedit (2.12.1-0ubuntu1)
And that all for a simple commandline editor???
Who knows?
dirk

Wish you'd mentioned the server install earlier. 

try **sudo vim /etc/apt/sources.list**

---

### Post by dirkdekker on 2006-08-07
I did this: sudo vim /etc/apt/sources.list
and opened the file for editing.
Question : how do I leave this editor and save the changes?

---

### Post by dirkdekker on 2006-08-07
Hi you wrote:

dont forget, if you are gonna change the source, either update in synaptic or in terminal
```
sudo apt-get update
```
before looking for stuff to install.
Be careful when you do updates too, the universe and backports arent as tested as the stuff in the repositories you started with.  

I installed a simple server breeze 5.10 .
Is that no a stable version?

---

### Post by davebgimp on 2006-08-07
> **dirkdekker said:**
> I did this: sudo vim /etc/apt/sources.list
and opened the file for editing.
Question : how do I leave this editor and save the changes?

After making your edits, type

**:wq**

---

### Post by dirkdekker on 2006-08-07
> **davebgimp said:**
> After making your edits, type

**:wq**

thanks ! 
Are there more statements in this tiny editor?

---

### Post by cantormath on 2006-08-07
gedit is for gui, not server install without gui, uninstall it

```
apt-get remove gedit 
```

also, synaptic is gui, so you cant use that, you have t apt-get stuff.

---

### Post by wjp.reg on 2006-08-07
> **dirkdekker said:**
> I did this: sudo vim /etc/apt/sources.list
and opened the file for editing.
Question : how do I leave this editor and save the changes?

Googling "Vi Help" yields over 82 million links.. Help yourself or go here:

[http://unixhelp.ed.ac.uk/vi/index.html]("http://unixhelp.ed.ac.uk/vi/index.html")

---

