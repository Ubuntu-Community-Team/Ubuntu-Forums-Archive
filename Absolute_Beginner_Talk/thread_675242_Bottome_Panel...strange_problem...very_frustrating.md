---
title: "Bottome Panel...strange problem...very frustrating!"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2008-01-22
I have two panels, one on top with app. places...and some launchers for firefox, terminal...
on the bottom i have the windows list and run and the system tray and a few other things.

my problem is that my bottom panel is on auto hide, when i put my mouse over it, it does some funny shrink of a few pixels and some icons in the panel disappear then it just locks! none of the buttons on the panel work, i can't right click to delete the panel either!  and whenever i mouse over the bottom panel the top one freezes too!

so i   ctrl+alt+del to restart X and the panels show up as white rectangles,
so i   ctrl+alt+del to restart X again! and the panels show up as white rectangles inside black panels,
so i   ctrl+alt+del to restart X and my original panels are back with all the buttons i had before!    BUT it stilllllll freezes!

i've tried deleting gnome-panel adn reinstalling it, does nothing, the only thing that puzzles me is when i remove gnome-panel restart then install it again my old panels show up!  if i reinstalled it how does it know what i had in my old panels!

THIS IS VERY FRUSTRATING! I JUST WANT TO DELETE THE BOTTOM PANEL!!!!!! OR GET RID OF MY PANELS AND MAKE NEW ONES!!!!

any help would be greatly appreciated!  thanks, Alain!

---

### Post by philinux on 2008-01-22
goto your home directory press ctrl h to sho hidden files.

delete the following then reboot or ctrl alt backspace.

the files are..

.gnome .gnome2 .gconf .gconfd .metacity

they will be recreated.

---

