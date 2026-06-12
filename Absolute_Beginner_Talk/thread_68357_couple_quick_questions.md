---
title: "couple quick questions"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by taseal on 2005-09-22
Well my laptop finally gave up on me with windows..

i just recently installed linux and i love it so far (cept the things i dunno piss me off but in time i guess i'll figure'm out lol)

so i'm gunna put linux on the laptop but I was wondering on couple things....
I have all my music on there, which i was gunna trasfer over to a cd but it just keeps freezing once it boots up... all the songs are also on my ipod but they are all named weird (like song's name is DTJNS) I was wondering if there is an itunes like program out there I can use to download the songs off to the computer with the right tags?

2nd question :D

how do i force a program to quit? xine froze up on me earlier and i couldnt quit it... also the DVDs are REAL choppy (the program itself is just choppy actually lol) the help files said use xine-check which I cant find.... where is this? i tried apt-get xine-check but no luck =/

also what was the command to go back in x when ure in command line?

sudo killall gdi
sudo gdi 
i thought but its not...

thx!

loving linux so far btw :D

just alot of stuff to learn...

---

### Post by aysiu on 2005-09-22
[QUOTE=taseal]
so i'm gunna put linux on the laptop but I was wondering on couple things....
I have all my music on there, which i was gunna trasfer over to a cd but it just keeps freezing once it boots up... all the songs are also on my ipod but they are all named weird (like song's name is DTJNS) I was wondering if there is an itunes like program out there I can use to download the songs off to the computer with the right tags?[/quote] The tags aren't the program--they're actually part of the song file. Just copy the .mp3 files (or whatever format they are), and as long as you have a program that can read tags, the tags will be there.

> 
how do i force a program to quit? xine froze up on me earlier and i couldnt quit it...  Are you using KDE or Gnome? In KDE, press Control-Alt-Esc. In Gnome, you may have to add the kill application launcher to the panel or you can create a keyboard shortcut for the command *xkill* (do this by going to configuration editor > apps > metacity > global keybindings and keybinding commands.

> 
also the DVDs are REAL choppy (the program itself is just choppy actually lol) the help files said use xine-check which I cant find.... where is this? i tried apt-get xine-check but no luck =/ You may have to enable DMA. I don't have the link right now. Hold on a sec.

Edit: Okay, [here's the link](http://ubuntuforums.org/showthread.php?t=30949)

---

### Post by 23meg on 2005-09-22
1 - i don't know of a linux program that does this but you may want to check out Ephpod for windows. at worst, you could copy all the songs to a single directory, install Audio Tag Tool (sudo apt-get install tagtool) and then use it to rename the files according to the id3 tags. 

2 - xkill or "force quit" which you can add to the gnome panel

3 - startx

---

### Post by taseal on 2005-09-22
[QUOTE=23meg]1 - i don't know of a linux program that does this but you may want to check out Ephpod for windows. at worst, you could copy all the songs to a single directory, install Audio Tag Tool (sudo apt-get install tagtool) and then use it to rename the files according to the id3 tags. 

2 - xkill or "force quit" which you can add to the gnome panel

3 - startx[/QUOTE]
 startx doesnt work if there is a server running already or something... 

i just saw ure from istanbul

so am i :p

but i'm in FL now :D

so yeah i'm turkish :D

---

### Post by taseal on 2005-09-22
[QUOTE=aysiu]The tags aren't the program--they're actually part of the song file. Just copy the .mp3 files (or whatever format they are), and as long as you have a program that can read tags, the tags will be there.

 Are you using KDE or Gnome? In KDE, press Control-Alt-Esc. In Gnome, you may have to add the kill application launcher to the panel or you can create a keyboard shortcut for the command *xkill* (do this by going to configuration editor > apps > metacity > global keybindings and keybinding commands.

 You may have to enable DMA. I don't have the link right now. Hold on a sec.

Edit: Okay, [here's the link](http://ubuntuforums.org/showthread.php?t=30949)[/QUOTE]

my dma is on :(

---

