---
title: "XP vs Ubuntu at boot up"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by rubbermyroof on 2007-08-02
Hi, being one of those awful new beginners (just like David Bowie, but he's been at it twenty years) i can't see how to stop the default OS boot from being ubuntu. I get a few seconds to scroll doen to Windows Pro, but I'd rather have that as default for now, or at least that the computer waits for me to pick one or the other myself instead of going to Ubuntu by default - how do I do this? Cheers, J

---

### Post by taurus on 2007-08-02
You can change the default or increase the time out or have GRUB wait for your input by modifying /boot/grub/menu.lst.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by thefoolisme on 2007-08-02
I hate it when people respond in the Absolute Beginners Forum with statements like "oh, just edit this file", and don't say how to get to that file, or what to edit.  <Rant over>

Ok, to change the default OS in Grub, I believe you will find this link useful:  [http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

It explains how and what line to change in the /boot/grub/menu.lst file.  Incidently, you would edit that file in terminal using:  sudo gedit /boot/grub/menu.lst

---

### Post by devanity on 2007-08-02
> **thefoolisme said:**
> I hate it when people respond in the Absolute Beginners Forum with statements like "oh, just edit this file", and don't say how to get to that file, or what to edit.  <Rant over>

Ok, to change the default OS in Grub, I believe you will find this link useful:  [http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

It explains how and what line to change in the /boot/grub/menu.lst file.  Incidently, you would edit that file in terminal using:  sudo gedit /boot/grub/menu.lst

And if you get:
bash: gedit: command not found
Use: sudo apt-get install gedit
And then: sudo gedit /boot/grub/menu.lst

---

### Post by remix79 on 2007-08-04
Thanks to thefoolisme and taurus.  Both the link and the commands were very helpful.

---

### Post by taurus on 2007-08-04
> **thefoolisme said:**
> I hate it when people respond in the Absolute Beginners Forum with statements like "oh, just edit this file", and don't say how to get to that file, or what to edit.  <Rant over>

Ok, to change the default OS in Grub, I believe you will find this link useful:  [http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

It explains how and what line to change in the /boot/grub/menu.lst file.  Incidently, you would edit that file in terminal using:  **[COLOR="Red"]sudo gedit[/COLOR]** /boot/grub/menu.lst

I also hate it when people give a command that could cause trouble with permissions later on.

```
**[COLOR="Blue"]gksudo gedit[/COLOR]** /boot/grub/menu.lst
```

---

### Post by Brunellus on 2007-08-04
> **devanity said:**
> And if you get:
bash: gedit: command not found
Use: sudo apt-get install gedit
And then: sudo gedit /boot/grub/menu.lst
which would be unnecessary.

'gedit' is a text editor, and not the only one out there, either.  since you've got a terminal open anyway, might as well use one of the three (!) text editors that ship with the ubuntu core.

For most people, the most natural will be nano.  

so in that case it's 

nano foo

where 'foo' is the file you want to edit.  if that file needs to be edited by root, then it's 

sudo nano foo

---

