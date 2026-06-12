---
title: "Help with switching partitions."
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by Phoenix27 on 2007-10-12
Hello, I have windows XP on one partition and ubuntu on the other. How do I switch it to run linux instead of it booting up windows everytime? thanks

I installed windows AFTER Ubuntu.

Internet does not work for me over the LiveCD either.

---

### Post by louieb on 2007-10-12
See the reinstall GRuB link in my signature.

---

### Post by Duck2006 on 2007-10-12
You will have to install the linux boot loader (grub) to the mbr of the hard drive.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

This may help.

---

### Post by Phoenix27 on 2007-10-12
How do I switch back to Windows now?

Linux is working again though, thank you :D

---

### Post by Duck2006 on 2007-10-12
Did you reinstall grub?

---

### Post by Phoenix27 on 2007-10-12
> **Duck2006 said:**
> Did you reinstall grub?



Yeah.

---

### Post by Duck2006 on 2007-10-12
When you start the system does a grub menu show up?

---

### Post by Phoenix27 on 2007-10-12
> **Duck2006 said:**
> When you start the system does a grub menu show up?

All it says is I can hit ESC and when I do it just shows ubuntu and ubuntu safe mode, no menu though.

---

### Post by louieb on 2007-10-12
You need to add an windows entry to file  /boot/grub/menu.list that looks something like this: (place it at the bottom of the file)
```
title Win XP Home
      rootnoverify (hd0,0)
      makeactive
      chainloader +1
      boot

```This assumes windows is on the first partition of the first hard drive.
To open file for editing press **Alt+F2  **and enter:
```
gksudo gedit /boot/grub/menu.lst
```good luck
BTW I use the site duck2006 pointed to. Its the most complete site on GRUB and Dual Booting in general I have found. (its in my signature too).

---

### Post by Duck2006 on 2007-10-12
Wile your editing the menu.lst change the line that has the hiddenmenu from

#hiddenmenu

to

hiddenmenu

this that way your see the menu, and the color cyan/blue white/blue line from

#color cyan/blue white/blue

to

color cyan/blue white/blue

that way your see and color menu.

---

### Post by Phoenix27 on 2007-10-12
> **Duck2006 said:**
> Wile your editing the menu.lst change the line that has the hiddenmenu from

#hiddenmenu

to

hiddenmenu

this that way your see the menu, and the color cyan/blue white/blue line from

#color cyan/blue white/blue

to

color cyan/blue white/blue

that way your see and color menu.




--------------------------------------------------------------------------------

Well.

I didn't see your post till now (i'm on my other comp.)

Now grub is starting, but the screen is black and it looks like DOS mode.

It's telling me to hit tab for commands and ubuntu won't start up.

---

### Post by Duck2006 on 2007-10-12
Does any OS boot up?

---

### Post by Phoenix27 on 2007-10-12
> **Duck2006 said:**
> Does any OS boot up?

Nope. 

All it says is "Minimal BASH line editing is supported. Hit TAB for available commands"
and then it says grub>

---

### Post by Duck2006 on 2007-10-12
What did you changed in your menu.lst, then grub was working befor it wasn't?

---

### Post by Phoenix27 on 2007-10-12
> **Duck2006 said:**
> What did you changed in your menu.lst, then grub was working befor it wasn't?

I put in the lines that other guy told me to put in at the end.

And yes, it was working before.

---

### Post by Duck2006 on 2007-10-12
You can try booting from super grub disk and see if you can boot back in to ubuntu.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by logos34 on 2007-10-12
>  Originally Posted by Duck2006  View Post
Wile your editing the menu.lst change the line that has the hiddenmenu from

#hiddenmenu

to

hiddenmenu

this that way your see the menu,

Actually it's the reverse.  You want to see the menu, so:

**#hidddenmenu**  (= show menu)

Super Grub should boot ubuntu, but you might also take a look at this:
[URL="http://users.bigpond.net.au/hermanzone/p15.htm#cli"]
'How To Boot Linux from GRUB's CLI (Ubuntu)'
[/URL]

---

### Post by louieb on 2007-10-12
Wonder what you did. Super GRUB can fix it. You just have to go through the doc. Wish I had asked you to save a copy on a USB stick or something. Oh well hind sight is 20/20. Those lines came out of menu.lst on my laptop. What your are seeing looks like this **grub>  **right? that usually only happens when it can't  find /boot/grub/menu.lst.  The Dual boot site has some stuff. Might stick in you live CD again and look for that file on your hard drive.

---

