---
title: "how to find recently downloaded program in Easy Peasy..."
date: 2013-07-05
forum: Any Other OS
---

### Post by Florio on 2013-07-05
Hi,

I've just installed Easy Peasy and am now trying to personalize my netbook. I've downloaded Gimp via the Ubuntu Software Centre, but cannot find the application. I would like to place it in the 'Graphics' folder. Can someone tell me where Gimp has ended up, and how I can place it (or at least the icon) in the 'Graphics' folder?

Thanks

---

### Post by sudodus on 2013-07-05
.

---

### Post by Florio on 2013-07-05
Thanks for your reply, Sudodus. I don't know if you are familiar with Easy Peasy; i thought the various categories on the desktop were kinds of folders, but I suppose they are actually menus. In any case I expected to find Gimp automatically placed in the Graphics one, but it isn't. Clicking on the Easy Peasy logo in the top left-hand corner does not bring up a search option. I'll keep trying to locate the program via different search filters, but once I find it, how can I get it (or at least the application icon) into the Graphics folder/menu?

---

### Post by Florio on 2013-07-05
Thanks for your reply, Sudodus. I don't know if you are familiar with  Easy Peasy; i thought the various categories on the desktop were kinds  of folders, but I suppose they are actually menus. In any case I  expected to find Gimp automatically placed in the Graphics one, but it  isn't. Clicking on the Easy Peasy logo in the top left-hand corner does  not bring up a search option. I'll keep trying to locate the program via  different search filters, but once I find it, how can I get it (or at  least the application icon) into the Graphics folder/menu?

---

### Post by sudodus on 2013-07-05
I thought Easy Peasy was a nick-name for Ubuntu with Unity because you have [Ubuntu] as prefix in the title. I'm sorry, I don't know how it is organized.

Normally in linux, you can start a program from a terminal window, using its name in lower-case letters. At least in Ubuntu and Lubuntu, you start a terminal window with the hotkey combination

[I][B]ctrl + alt + t
[/B][/I]
and in that window you type

```
gimp
```

and press the Enter key. This works because programs are supposed to be installed into directories in $PATH, so you need not enter the full path, only the filename of the program (or a symbolic link to the program).
 
But I guess you can find gimp via a graphical user interface too, Let us hope someone who knows Easy Peasy will give you real help :-)

---

### Post by Cheesemill on 2013-07-06
*Thread moved to **Other OS/Distro Support**.*

Not a Ubuntu support request.

---

### Post by Plumtreed on 2013-07-06
I was surprised to see EasyPeasy as a current release......I think it is based on 10.04....but looks and runs well on the Asus eeePC701 or similar. 

Have you installed EasyPeasy or are you running live in Unetbootin....in which case you new additions may not be retained on reboot.

---

### Post by Florio on 2013-07-07
Yes, I have in fact installed the OS. Since first writing, I have managed to install GIMP and get it into the Graphics menu on the desktop. I ran the program from the terminal as suggested here, and for some reason it was then automatically placed in the correct menu.

I am now trying to get other already installed software (for example the Evince pdf reader) into a desktop menu, but what worked for GIMP no longer works with other programs. Is anyone here familiar with EasyPeasy and how to personlise the desktop? I cannot do this from Ubuntu Software Centre.


> **Plumtreed said:**
> 
Have you installed EasyPeasy or are you running live in Unetbootin....in which case you new additions may not be retained on reboot.

---

### Post by Plumtreed on 2013-07-07
.....from memory, go to 'applications-File Browser.......then open usr/share/applications              -you should be able to drag and drop apps to the Desktop 

....also refer to the eeePCforum for archive notes on UbuntuEEE and Easy Peasey


in EasyPeasy you open Files&Folders......then open Desktop, in the right panel click on File System, then bore down thru usr/share/applications

---

### Post by Florio on 2013-07-08
> **Plumtreed said:**
>  in EasyPeasy you open Files&Folders......then open Desktop, in the right panel click on File System, then bore down thru usr/share/applications

Thanks Plumtreed. I had already tried this, but the Desktop folder does not seem to be connected to what actually appears on the desktop, i.e. the various menus. In fact it was empty before I placed the Evince pdf reader folder inside it. 

I cannot find the various desktop menus (Games, Graphics, Favourites, Office etc.) in the list of system files. And even if I did manage to discover where they are, I don't know how I could move Evince, say, into Office so that its icon would appear there and not the whole folder.

By the way, whereabouts in Australia are you? I'm a fellow aussie, but now living overseas.

---

