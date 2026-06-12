---
title: "not entirely sure what this is called..."
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by ushaba on 2007-01-30
i have three basic questions, i guess. i've got a few programs i've installed from source via tar packages, and a few problems with loki installers and things like them. what i want to know is how i can manually do the following from the command line:
1) create a command that i can launch (bash script) which links to ...../ut-bin for instance. i just need it to go to the file and launch the program when i tell it to, and i'm sure there's pretty basic syntax, because i've seen it before, but i'm not having much luck searching for "launcher thingy
2) how can i then make a link on a desktop or whatever with an icon that uses that thingy? 
3) if i want to create a menu entry, do i link to the imaginary bash command i am creating, or give it the parameters for the original binary executable, such as ./...../ut-bin?

PS. what is that launcher thingy called in english? 
thanks/cheers

---

### Post by mal on 2007-01-30
If you right click on the gnome panel at the top of the screen and then select "Add to Panel...", you will see a button labeled "Custom Application Launcher".  This will let you create an icon on the panel to execute any command you wish.

Maybe this will meet your needs.

Mal

---

### Post by ushaba on 2007-01-30
sadly, i am not using gnome, and i prefer to learn the command line way as much as possible. but i think that;'s similar to what i'm looking for. if anyone knows how gnome goes about creating launchers, that's what i want to know, at least for the icons. the other question of how to make a command line bash script must have a general form...
cheers
ushaba

---

### Post by kerry_s on 2007-01-30
> **ushaba said:**
> i have three basic questions, i guess. i've got a few programs i've installed from source via tar packages, and a few problems with loki installers and things like them. what i want to know is how i can manually do the following from the command line:
1) create a command that i can launch (bash script) which links to ...../ut-bin for instance. i just need it to go to the file and launch the program when i tell it to, and i'm sure there's pretty basic syntax, because i've seen it before, but i'm not having much luck searching for "launcher thingy
2) how can i then make a link on a desktop or whatever with an icon that uses that thingy? 
3) if i want to create a menu entry, do i link to the imaginary bash command i am creating, or give it the parameters for the original binary executable, such as ./...../ut-bin?

PS. what is that launcher thingy called in english? 
thanks/cheers

1) Create a script in your account> gedit .myapp
put>
#!/bin/sh
path to executable:example: /usr/bin/app

make the script executable> chmod +x .myapp

2)Drag the executable to the desktop

3)Straight to the app

I'm not really sure about #1, for a luncher you can just point straight to the executable, so you wouldn't need a script, unless you need to launch it in a terminal. In that case it would be>
#!/bin/sh
xterm -T "app name" -e application

man xterm for more info.

---

### Post by RomeReactor on 2007-01-30
Hi. I haven't used KDE in a while, so i'm not sure if this is built in to it, but try right-clicking on the desktop and see if one of the options is "Create Launcher"; then post here how you invoke the programs you want on the command line and their location so we can help you with the scripts.

EDIT: oops, didn't see you there kerry_s :mrgreen:

---

### Post by kerry_s on 2007-01-30
> **RomeReactor said:**
> Hi. I haven't used KDE in a while, so i'm not sure if this is built in to it, but try right-clicking on the desktop and see if one of the options is "Create Launcher"; then post here how you invoke the programs you want on the command line and their location so we can help you with the scripts.

EDIT: oops, didn't see you there kerry_s :mrgreen:

Hey, don't let me scare you. Every one always takes off when i show up. Do i smell bad? :confused:  :D

---

### Post by ushaba on 2007-01-30
i'm actually using fluxbox, as i was more or less content with xfce but found a lot of unusual problems where programs would just die but stay on the screen and killall wouldn't seem to change the fact... another story. but i'm mainly interested in the text way of doing things. i think i've got it now though. thanks all!
cheers

---

