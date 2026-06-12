---
title: "Removed Menus. How to Return"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by poetmayhem43 on 2007-06-12
Hi, 

I have somehow managed to stop the main menu bar from displaying.  

i.e. I no longer have the Applications, System, Shutdown menu at the top of the screen of the show desktop at the bottom.  

I think it is either an issue with Beryl or with Clam as the latter was updated before it disappeared.  

My betting is for Beryl (not sure what to type to stop it as it is automatically started on startup)

What do I need to type into the terminal to get it back as it was?  :D

Thanks,

---

### Post by Najand on 2007-06-12
Push Alt+F2 and type "killall beryl" to kill Beryl.
You lost the panel or just the menu?

---

### Post by Omnios on 2007-06-12
Right click the bar where you want the menu. Choose add to panel, GO to utilities and choose menu bar and add it. This is the standard Ubuntu menu.

---

### Post by revealer on 2007-06-12
alt+f2 to get a run application dialog
type killall-gnome-panel and tick run in terminal
if this doesnt solve it try killall-beryl or killall-beryl-manager

---

### Post by Najand on 2007-06-12
> **revealer said:**
> alt+f2 to get a run application dialog
type killall-gnome-panel and tick run in terminal
if this doesnt solve it try killall-beryl or killall-beryl-manager

Well, I don't think there is no need for a dash between killall and the process name.

---

### Post by poetmayhem43 on 2007-06-12
Thanks, Beryl is now off.

I don't think the panel is there anymore either.    
I also don't have the bar at the bottom with the 'show desktop' icon.

---

### Post by Najand on 2007-06-12
Push Alt+F2 and type "gnome-panel" to start panels again.

---

### Post by poetmayhem43 on 2007-06-12
> **revealer said:**
> alt+f2 to get a run application dialog
type killall-gnome-panel and tick run in terminal
if this doesnt solve it try killall-beryl or killall-beryl-manager

Thanks Revealer, that solved it.  Cheers.

---

### Post by Sailor-Moon on 2007-06-15
i have a similar problem

i have a hp and ubuntu would not install, thanks to a post on the forums using 
The first solution is (with the live-cd) :
- Select 'Other options' with F6
- Remove 'splash', 'quiet' and '--'
- Add 'all_generic_ide'

i managed to get it to install.

now when i run ubuntu, i get the log in screen, then i get a desktop wallpaper, two grey bars flash on and off about 10 times along the top and the bottom of the screen, then they vanish and i am left with just a cursor and a desktop with nothing on it :(

---

