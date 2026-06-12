---
title: "[SOLVED] removing windows from grub"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by leetrefz on 2006-11-17
Windows became a casualty of my kubuntu install. I went to load it, but got a blue screen, I assume those unmovable files I saw in the win defrag didn't like the partition being sized down. 

So I deleted the windows partition in qtparted, but windows is still in grub. 

I don't understand the grub edit menu. don't want to see winny there no more.

---

### Post by Bachstelze on 2006-11-17
```
sudo nano /boot/grub/menu.lst
```

Look for the lines regarding your windows, it should be like this

title       Windows XP    # or whatever you set it to
root        (hdWhatever)
# maybe some other stuff here like makeactive or savedefault
chainloader +1


delete all of them :)

---

### Post by PigCorpse on 2006-11-17
In the terminal, type:

sudo nano /boot/grub/menu.lst

Go down and you'll see the Windows entry, just delete that. Then, press Ctrl-X and save it.

---

### Post by bodhi.zazen on 2006-11-17
Nice !

```
sudo gedit /boot/grub/menu.lst
```

that is a small "L" in menu.lst

Just add a # in the front of the Windows stanzas (all the lines associated with windows)

Like this:

# Windows XP
# root (hd0,0)
# makeactive
# chainloader +1
# boot

(# = comment out, saves for later if you need it)

Save and exit.

8)

---

### Post by bonjun on 2006-11-17
can't it done by:

> sudo update-grub

---

### Post by leetrefz on 2006-11-17
Thanks for all the help! I just went into the file with konqueror opened it as root and deleted the stuff. don't think I'll be putting windows back. 3 days on linux, already feeling like I'm learning lots. Just don't understand the all pervading love for the terminal. cheers

---

### Post by jhenager on 2006-11-17
> **bodhi.zazen said:**
> Nice !

(# = comment out, saves for later if you need it)

Save and exit.

8)

Good advice. If you don't comment out lines, save a backup first.
After getting burned once, I never risk working without a net.

---

### Post by bodhi.zazen on 2006-11-17
> **leetrefz said:**
> Thanks for all the help! I just went into the file with konqueror opened it as root and deleted the stuff. don't think I'll be putting windows back. 3 days on linux, already feeling like I'm learning lots. Just don't understand the all pervading love for the terminal. cheers

The CLI is very helpful. As you become more familiar with LInux you will use it more and more.

Initial advice:
[list=number][*]Add a "mini command line" to your desktop toolbar.
[*]I run a transparent terminal ALL THE TIME. Try tilda, you can hide and openwith the F1 key. Try out [tilda](http://tilda.sourceforge.net/tildashots.php)
[screenshot](http://img183.imageshack.us/img183/4745/200611022253251600x1200vq7.png)
[*][Basic CLI](http://doc.gwos.org/index.php/CommandLineBeginners)[/list]

---

### Post by housam on 2006-11-17
Originally Posted by bodhi.zazen

> The CLI is very helpful. As you become more familiar with LInux you will use it more and more.

Initial advice:

   1. Add a "mini command line" to your desktop toolbar.
   2. I run a transparent terminal ALL THE TIME. Try tilda, you can hide and openwith the F1 key. Try out tilda
      screenshot
   3. Basic CLI


I've downloaded Tilda to my desktop, can you tell how to install it.

thanks

---

### Post by bodhi.zazen on 2006-11-17
> **housam said:**
> Originally Posted by bodhi.zazen




I've downloaded Tilda to my desktop, can you tell how to install it.

thanks

Try installing from the repositories first (search in synaptic)

[tilda](http://packages.ubuntu.com/dapper/x11/tilda)

---

### Post by leetrefz on 2006-11-19
I got tilda in synaptic but see no trace of it anywhere. Is it just for gnome?

---

### Post by housam on 2006-11-20
Originally Posted by leetrefz

> I got tilda in synaptic but see no trace of it anywhere. Is it just for gnome?

try this :

$ sudo apt-get install tilda
then after installation type ;
$ tilda

---

### Post by leetrefz on 2006-11-20
thanks, since then I've found yakuake. seems good.

---

### Post by bodhi.zazen on 2006-11-20
type```
tilda -C
``` To get the configuration menu.

---

