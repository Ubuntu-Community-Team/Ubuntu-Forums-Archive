---
title: "New programs not showing up"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Metalgod89 on 2007-12-10
Hi I have download programs like dgen a sega genesis emulator and I can not seem to be able to find it on my hard drive at all . I used synaptic to download it :/ Any ideas

---

### Post by NovaAesa on 2007-12-10
Try right clicking on Applications then click on Edit Menus. A window should come up, in which you should be able to look for the application (It's probably under games, but have a look around in there). Just tick the box next to the application in question, and then close, and you should be right to go.

---

### Post by Metalgod89 on 2007-12-10
though that is a good thing to keep in mind, no luck  :(

---

### Post by Partyboi2 on 2007-12-10
you can do a search for there location under "Places>Search for Files"
But if you are trying to run them, then type there name into a terminal
eg to run Gimp type gimp
or you can use "locate" Finds any file or diresctory with the name you entered.
eg
```
locate gedit
```

---

### Post by ncappel1 on 2007-12-11
here's another thing to try, open your terminal and enter
```
apropos sega
``` or
```
apropos genesis
```
this will bring up all commands that have something to do with "sega" if you find the appropriate command, you can add it manually to your menus through the "edit menus" dialogue noted above.

---

### Post by Metalgod89 on 2007-12-11
ok I got it to run in the terminal but I have no idea how the program runs if anyone can help that would be very appreciated

---

### Post by spiderbatdad on 2007-12-11
probably runs as a .bin, so you would ./program in a terminal

---

### Post by jaybombalous on 2007-12-11
> **spiderbatdad said:**
> probably runs as a .bin, so you would ./program in a terminal


I think its easier to understand if u stated that its probably a script that needs to be run as a executable (.bin) file instead and this is how you do it.

cd to the directory location of the script and then type in ./ followed by the name of the script. IE...

```
cd directorylocationofscript
./scriptname
```

---

