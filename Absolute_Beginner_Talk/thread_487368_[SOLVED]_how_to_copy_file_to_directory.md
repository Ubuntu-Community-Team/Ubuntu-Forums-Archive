---
title: "[SOLVED] how to copy file to directory"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by ewarmour on 2007-06-29
I'm simply trying to copy/paste a php file from my desktop to var/www/apache2-default and I get access denied. This happens with other dirs too. I don't want to have to sudo cp etc... from the terminal everytime. How to I give myself rights to these directories?

Thanks, newbenoob.

---

### Post by swoll1980 on 2007-06-29
hit alt f2 in the run command enter "gksu nautilus" with out the quotes this will give full read write access

---

### Post by tarek on 2007-06-29
Go to the command line and type: gksudo nautilus &
This will start nautilus as root. I added an icon to the menu so I don't have to type.

Edit:
swoll1980, I was just typing the same thing :)

---

### Post by starcraft.man on 2007-06-29
> **swoll1980 said:**
> hit ait f2 in the run command enter gksu nuatilus this will give full read write access

I don't really recommend that, I mean it gives nautilus full power over your files. IMO, thats not secure. Course if convenience is most important that concern won't matter to you.

Alternatively, you could just write a simple bash script I think if its only from desktop to that folder all the time. That would save the hassle of typing.[ Look at Linux Command for learning that.]("http://www.linuxcommand.org/writing_shell_scripts.php") Scripts are powerful, I should use them more, alas I feel almost compelled to input my commands live :p.

Oh and if you just want to give yourself ownership of that folder, [permissions tutorial.]("http://www.linuxcommand.org/lts0070.php")

---

### Post by kakalaky on 2007-06-29
Another way to do this is add a script to nautilus to open another instance with root privilidges in your current location.  To do this paste the following code into a text editor and save it as root-nautilus-here in ~/.gnome2/nautilus-scripts/

```
#!/bin/bash

# Opens a nautilus window as root.

foo=`gksudo -u root -k -m "enter your password for nautilus root access" /bin/echo "got r00t?"`
sudo nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI
```

then ```
chmod +x ~/.gnome2/autilus-scripts/root-nautilus-here
```

This will allow you to right click in nautilus and run the script.

---

### Post by ewarmour on 2007-06-29
thank ya'll very much. Seems to be overly restrictive this OS.

BTW how did you add an icon for gksudo nautilus & to your menu? That would be great for my graphical butt.

Thanks again.

---

### Post by swoll1980 on 2007-06-29
Just secure thats all

---

### Post by tarek on 2007-06-29
> **ewarmour said:**
> thank ya'll very much. Seems to be overly restrictive this OS.

BTW how did you add an icon for gksudo nautilus & to your menu? That would be great for my graphical butt.

Thanks again.

That's why Linux is better than Windows, you can't screw the system easily.

1) Right-click on Application menu
2) Choose Edit Menus
3) Pick a menu, I picked System Tools
4) Click on New Item
5) In the command field enter:
```
gksudo nautilus /var/www
```
replace /var/www with whatever you want.

Give it a name and click close and close the menu editor.

Now go to the menu where you added it and run it.

tk

---

### Post by kakalaky on 2007-06-29
NM, above beat me to it.

---

### Post by swoll1980 on 2007-06-29
The reason things are not restricted on windows is that 99% of windows users are loged on as su all the time and don't even know it. This is how most windows pc's turn into zombie robots

---

### Post by kakalaky on 2007-06-29
In case you don't know, you can write to anywhere in your home folder and it's subfolders without being root (using sudo, su, gksudo, etc.)  Just about anywhere else in the filesystem you will need to be root.

---

### Post by ewarmour on 2007-06-29
> **swoll1980 said:**
> The reason things are not restricted on windows is that 99% of windows users are loged on as su all the time and don't even know it. This is how most windows pc's turn into zombie robots

I'm a MS .net developer (web and windows apps) and expert with nt and xp. I have no real reason to go to vista so thats that. I started out as a LAMP dev and now do .NET exclusively. It makes $$, what can I say? 

My *nix is so rusty...

I'm just out to see if I can transition to linux, ubuntu to be precise, and do everything I need to do *except* .net development. For that I'll stick to my XP 64 box for now. Maybe I'll get to the point where I can run mono and vs.net under wine but right now I just need to learn how to use Ubuntu via this graphical ui and build some php/postgresql or mysql apps again. Eclipse is installed now I need to learn how to use that too... but time I have 

Thanks for the help!

---

### Post by tarek on 2007-06-29
I programmed in .net for 2-3 years - web and desktop apps - on windows but as far as I know mono - the .net environment for linux - is doing pretty good. 
I remember using Novel web tools at work which were developed using mono and we were running a linux server. The last time I checked mono supported .net 1.1 but I'm sure now they have a new version. And regarding the IDE, there must be an IDE for .net on linux somewhere.

I guess I don't have answers but if Novel is using mono then it must be something good :)

---

