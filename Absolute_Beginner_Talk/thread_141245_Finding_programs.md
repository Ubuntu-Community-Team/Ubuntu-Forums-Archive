---
title: "Finding programs"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by ditane on 2006-03-07
When I install programs with synaptic, I sometimes have a problem.  I either can't find the program, or can't figure out how to run it. I'm not sure which. Sometimes I find a file with that programs name, but nothing happens when I double click.
I thought I saw something before on how to run some programs, but I couldn't find it again. Any suggestions?
Thanks

---

### Post by Xian on 2006-03-07
Generally a launcher is installed within one of the menu categories included in the main panel. There are of course many exceptions as often programs are simply meant to be run from the terminal. What application(s) are you having problems finding and running?

---

### Post by ditane on 2006-03-07
Well, when looking through some of the stuff in synaptic, I got a bit click happy and added a bunch of programs, most of which I dont remember even.  I guess part of the problem is that I am new to linux and ubuntu, and wanted to try a bunch of stuff And being used to Windows, I half expected everything to be avaliable with a GUI and it all show up in one place to launch.  Any suggestions on a good guide for beginners, especially dealing with programs and also the terminal?  I keep finding guides, and somehow losing where they are.

Thanks

---

### Post by 3rdalbum on 2006-03-07
I had that problem when I first started using Ubuntu. Here's what I do now whenever something doesn't show up in the Applications menu:

1. Go into the Terminal program
2. Type the exact name of the package and press return.

If it says "command not found", type [FONT="Courier New"]man *packagename*[/FONT]. It should then give you a manual page about that particular package, and what programs are included with it (and therefore, what you need to type to open a particular program).

When you've found what command opens the program, go into Applications Menu Editor and add a new item to one of the menus. In the field which says what command to run, type the command that you've found.

------
Alternatively, there's a couple of things you can download from Synaptic that give you a "Debian" submenu within the Applications menu, and often shows programs that aren't automatically added to the Ubuntu applications menu. Unfortunately, I can't remember what these things were called or how to set them up.

---

### Post by cwaldbieser on 2006-03-08
[QUOTE=ditane]Well, when looking through some of the stuff in synaptic, I got a bit click happy and added a bunch of programs, most of which I dont remember even.  I guess part of the problem is that I am new to linux and ubuntu, and wanted to try a bunch of stuff And being used to Windows, I half expected everything to be avaliable with a GUI and it all show up in one place to launch.  Any suggestions on a good guide for beginners, especially dealing with programs and also the terminal?  I keep finding guides, and somehow losing where they are.

Thanks[/QUOTE]
If you double-tab TAB in the terminal, you will get a big list of all the commands in your command PATH.  If you type a few letters and then TAB, you will get a list of matching commands.

---

