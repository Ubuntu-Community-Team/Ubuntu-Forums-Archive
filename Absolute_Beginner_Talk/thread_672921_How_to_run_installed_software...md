---
title: "How to run installed software.."
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by SectorNitad on 2008-01-20
Dear Ubuntu gurus,

I have recently made the switch from Mr Gates' operating system to Ubuntu and am very impressed. However I have two problems/mental road blocks - which are both probably conceptual problems - 

1. After installing new software from the Synaptic Package Manager I can't see how I run it.

For instance, I have installed vim-gtk (the GUI based VIm editor) and it installed correctly but   there is no icon to it in the Applications manager. Where Windows has .exe files which one can just click on I don't see the same sort of thing in ubuntu.

2. I am having conceptual difficulties with the way the file-system is "laid out". Where windows has a definite "Starting point" such as "C:\" I don't see such in ubuntu.

I am certain that these questions have been asked many times and that there is probably a  document somewhere but i can't find it so any help would be greatly appreciated,

thanks
H

---

### Post by Joeb454 on 2008-01-20
I'm not sure about the first part, as I've never used or installed vim-gtk sorry.

As for the second one, the "Starting point" is / (root)

your personal files will be stored in /home

program files and such will most likely be somewhere in /usr

Hope this helps a bit :)

---

### Post by kaboodle_fish on 2008-01-20
If you click Alt + F2 then you can just type the name of the application you want to run

---

### Post by frup on 2008-01-20
I think part of the packaging guidlines is that all GUI programs should have a launcher. :( You are using Ubuntu not Kubuntu right?

---

### Post by kellemes on 2008-01-20
Maybe a good startingpoint..
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

As far as I know vim should be in the menu's.
Anyway you can run the graphical version of VIM from the terminal by running "gvim" or use ALT-F2 and type "gvim".
If it's indeed not in the menu's you can always add it using the menu-editor.

---

