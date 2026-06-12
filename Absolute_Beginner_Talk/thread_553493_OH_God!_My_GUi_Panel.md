---
title: "OH God! My GUi Panel"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by ATiwolf on 2007-09-17
I was reading a guide on how to play warcraft 3 in the forums.[Link]("http://ubuntuforums.org/showthread.php?t=45407&page=3")

 I had already installed wine prior to reading the thread but i figured it wouldn't be a problem.
after updating and stuff I couldn't get the sudo apt-get install winetools command to work...The terminal couldn't find it.So i went to source forge and downloaded the winetools program from them.

Next I tried running wine tools in the terminal but the files i got from sourcefourge just contain a folder with the wintools program in it. So i ingnored that step

**This is where the problem starts:** I popped in my warcraft cd to see what whould happen if i got wine to try and install or run the install.exe on the disk...but my xubuntu is weird and i have to restart my computer to get any newly inserted cd to show up on the computer...so i did....upon logging in i noticed my panels where missing from the top and bottom of the screen.....:(.....I waited to see if the system was just slow staring up.....Nothing...I tried a snit load of ctrl+ combinations if i could get something to come up....nothing....

  now im in a  panic.. I tried to right click and open file on my desktop using firefox to get here to seek wisdom....but xubuntu said firefox was already running...with no panels I can't access the applications- system-, i can't kill the already running firefox...

I even re-restarted xubuntu **twice** to see if it was a glitch....but it ain't showing up....

Please help..:cry:...please....

[IMG]http://i101.photobucket.com/albums/m53/Atiwolf/OMGAwesome.gif[/IMG]

---

### Post by Skidpad on 2007-09-17
See if you can kill & restart them while in your current session with these terminal commands:

To kill it off and restart it:
Code: killall gnome-panel

To restart gnome-panel:
Code: gnome-panel &

If you've rebooted, FireFox shouldn't be running now either.

---

### Post by ATiwolf on 2007-09-17
**Unfortunately** I can't try that out un till tomorrow. Regardless....[SIZE="3"]Thank You Very Much[/SIZE].

[IMG]http://i101.photobucket.com/albums/m53/Atiwolf/OMGAwesome.gif[/IMG]

---

### Post by Skidpad on 2007-09-17
No problem.  Post back tomorrow when you can.

---

### Post by picpak on 2007-09-17
He's using Xubuntu...shouldn't it be *killall xfce4-panel* and *xfce4-panel &*?

---

### Post by ATiwolf on 2007-09-17
Thanks for pointing that out, PicPack.You People here in the Ubuntu Community pwn.
[IMG]http://i101.photobucket.com/albums/m53/Atiwolf/OMGAwesome.gif[/IMG]

---

### Post by ATiwolf on 2007-09-17
Wait....Just remembered some [SIZE="3"]CRUCIAL[/SIZE] information.I **[B]can't access the normal terminal in xubuntu**[/B],i have to utilize konsole  to do my terminal task.If i try and going into the normal terminal my computer does some kind of quick reboot without going thru the Grub stuff....So how can i access konsole? 

Ctrl +Alt+f2 is like getting locked in a[FONT="Arial Black"] pitch black[/FONT][IMG]http://msn.mess.be/data/thumbnails/21/scaredddd.gif[/IMG] room with no way out so i think i can't use that....

---

### Post by Skidpad on 2007-09-17
> **picpak said:**
> He's using Xubuntu...shouldn't it be *killall xfce4-panel* and *xfce4-panel &*?
Oops!  My bad - Thanks for catching that!

---

### Post by picpak on 2007-09-17
> **ATiwolf said:**
> Wait....Just remembered some [SIZE="3"]CRUCIAL[/SIZE] information.I **[B]can't access the normal terminal in xubuntu**[/B],i have to utilize konsole  to do my terminal task.If i try and going into the normal terminal my computer does some kind of quick reboot without going thru the Grub stuff....So how can i access konsole? 

Ctrl +Alt+f2 is like getting locked in a[FONT="Arial Black"] pitch black[/FONT][IMG]http://msn.mess.be/data/thumbnails/21/scaredddd.gif[/IMG] room with no way out so i think i can't use that....

Oh dear, I thought I was the only one with problems with the Ctrl+Alt+F* terminals. However, mine just logs me out. Think this should be reported as a bug?

---

### Post by ATiwolf on 2007-09-17
Decided to stay up and tinker with the linux box [Don't have classes early in the morn on tues]:)

*When i type in the kill command it says no process killed
When i type in the xfce4 restore command i get this:
[1] 4979
atiwolf@atiwolf-linux:~?
xfce4-panel:4979 ):GTK-WARNING **:
Cannot Open Display


[SIZE="1"]I used the ctrl+alt+f2(.....Found out how to exit[/SIZE]

> **picpak said:**
> Oh dear, I thought I was the only one with problems with the Ctrl+Alt+F* terminals. However, mine just logs me out. Think this should be reported as a bug?

PSSssSST! Use ctrl+alt+f7
:)

---

### Post by picpak on 2007-09-18
> **ATiwolf said:**
> Decided to stay up and tinker with the linux box [Don't have classes early in the morn on tues]:)

*When i type in the kill command it says no process killed
When i type in the xfce4 restore command i get this:
[1] 4979
atiwolf@atiwolf-linux:~?
xfce4-panel:4979 ):GTK-WARNING **:
Cannot Open Display

Try ```
xfce4-panel --display :1
```


> **ATiwolf said:**
> PSSssSST! Use ctrl+alt+f7
:)

Thanks, but it automatically takes me back to the login screen.

Here's what happens:
- I press Ctrl+Alt+F1, and the boot screen that I'd see if usplash was disabled shows up.
- I press Ctrl+Alt+F1 again, the console flashes, and the login screen pops up.

After that, Ctrl+Alt+F1 works perfectly. It's really frustrating.

---

### Post by ATiwolf on 2007-09-18
Thanks,I appreciate it.Can't try that command right now I'm in a computer class  8).

[_This might not help._]("http://linux.about.com/od/ubuntu_doc/a/ubudg24t8.htm")

---

### Post by ATiwolf on 2007-09-18
\\:D/          \\:D/                      \\:D/                   \\:D/                    \\:D/
[FONT="Verdana"][CENTER][SIZE="3"]I Did It![/SIZE][/CENTER][/FONT]

This is how _WE_ fixed it:

    After Using serveral commands in the fullscreen terminal.(Provided by Skidpad And Picpack):)
I finally relized how *[SIZE="2"]futile[/SIZE]* it was to try and initialize a GUI interface in a Non-Gui environment. Therefore i was forced to painstakingly search through directory after directory of files and executables to find the one thing i knew that could solve my problems: Konsole

   Eventually i found it in usr-bin and started it up...I dropped in the xfce4-panel & command and my panels returned...

   I'll never take GUIs for granted again:^o

Thanks Pplz

---

