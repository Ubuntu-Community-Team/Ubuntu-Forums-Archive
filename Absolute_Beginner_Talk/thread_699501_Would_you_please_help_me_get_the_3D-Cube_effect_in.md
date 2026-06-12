---
title: "Would you please help me get the 3D-Cube effect in Ubuntu 7.04?"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by ahuman on 2008-02-17
[COLOR="SeaGreen"]If any of you would: please help me solve this problem: Please tell me how you can make four (4) separate desktops appear on your screen so you can perform the 3D-cube effect.

I have a NVidia graphics/video card correctly installed on my computer, but I must not have the correct animation-settings on my computer. I have not been able to get 4 separate windows or desktops to appear when I select the "super key"+e-key at the same time. 

When I press on the scroll-wheel of my cpu-mouse I can get the flat 2-sided desktop-plate effect, but not the 4-sided cube-effect.

Thanks for taking the time to consider helping me. I would appreciate your help & others', who may have some advice related to this topic.[/COLOR]

---

### Post by jan quark on 2008-02-17
right click on the two existing desktop panels in the right corner of the screen

then preferences

then add two more columns so you have four

---

### Post by drs305 on 2008-02-17
In addition, do you have the cube effects selected? Go to System, Preferences, Advanced Desktop Effects Settings and select Desktop Cube. Then you can double click on that to tweak the settings. At least that's the way in Gutsy.

---

### Post by ahuman on 2008-02-17
> **jan quark said:**
> right click on the two existing desktop panels in the right corner of the screen
then preferences
then add two more columns so you have four
[color="Green"]**I appreciate your help. I don't see the option that says "preferences" when I right click on the panels. Would you tell me if I have to select either: "Add to Panel", "Properties", or "New Panel" when I click on the right-corner of my screen?**[/color]

---

### Post by ace007 on 2008-02-17
In Feisty, you must have the package "gnome-compiz-preferences" installed.
```
sudo apt-get install gnome-compiz-preferences
```

then in a terminal run

```
gnome-compiz-preferences
```

Go to the workspaces tab, and set the number of viewports to 4 for a cube.  Make sure the effect cube and rotation is selected.  And under cube settings make sure animate is selected and a rotation settings are set to on for drag n' drop or pointer or whatever.  As far as more advanced settings, I'm not entirely sure yet.

---

### Post by wolfen69 on 2008-02-17
here are some keyboard shortcuts [http://www.keyxl.com/aaa02c8/388/Compiz-Fusion-keyboard-shortcuts.htm](http://www.keyxl.com/aaa02c8/388/Compiz-Fusion-keyboard-shortcuts.htm)

---

### Post by ahuman on 2008-02-17
**[COLOR="Green"]Do any of you know how to _add columns_ via the right side of the panel or screen, like Jan Quark suggested me to do?:[/COLOR]**

> **jan quark said:**
> right click on the two existing desktop panels in the right corner of the screen
then preferences
then add two more columns so you have four

---

### Post by ace007 on 2008-02-17
He is talking about the workspace switcher that come default in the bottom right hand corner of gnome.  You right click on it (its right next to the recycle bin by default) and select preferences.  You can also add it by selecting add to panel by right clicking on the panel.  Anyways, he suggested you set the number of workspaces in this menu to four so that you actually have 4 workspaces to switch to.  However, Gutsy works differently than Feisty.  I know in Gutsy you can set the workspace number and then go to compiz-fusion to control cube behavior.  The way to do this is feisty is different.  In my limited experience with feisty "adding columns" aka adding more workspaces, which can be displayed in a 2x2 array (where the term column come from) in the workspace switcher doesn't do anything for cube behaviour.

---

### Post by drs305 on 2008-02-17
I think you are running two simultaneous threads for the same issue (or I posted an answer in the wrong thread). Did you try running what I suggested in the other post? [http://ubuntuforums.org/showthread.php?t=699596](http://ubuntuforums.org/showthread.php?t=699596)

```
gconftool-2 --type bool --set /apps/panel/applets/workspace_switcher_screen0/prefs/display_all_workspaces true
```

---

### Post by ahuman on 2008-02-17
> **ace007 said:**
> He is talking about the workspace switcher that come default in the bottom right hand corner of gnome.  You right click on it (its right next to the recycle bin by default) and select preferences.  You can also add it by selecting add to panel by right clicking on the panel.  Anyways, he suggested you set the number of workspaces in this menu to four so that you actually have 4 workspaces to switch to.  However, Gutsy works differently than Feisty.  I know in Gutsy you can set the workspace number and then go to compiz-fusion to control cube behavior.  The way to do this is feisty is different.  In my limited experience with feisty "adding columns" aka adding more workspaces, which can be displayed in a 2x2 array (where the term column come from) in the workspace switcher doesn't do anything for cube behaviour.

[COLOR="Blue"][B]That doesn't help as long as I don't have that workspace switcher option on the right corner of my screen. None of you have told me how to add columns, as I mentioned earlier. 

1. Do you know how to add columns, like I mentioned?
2. Would you tell me how _you_ or others get the 3D cube-effect to work without the workspace-switcher feature?
3. Why isn't the workspace switcher where both of you told me it would be?[/B][/COLOR]

---

### Post by ace007 on 2008-02-17
I tried to explain to you that the columns are just a term he used to describe the number of workspaces.  There are 2 workspaces side by side by default.  Adding two more, gives you another "column" or makes the workspace switcher display 2 columns of 2. Or 2 rows of 2, whatever you want to call it.  If you are not using the workspace switcher than "adding columns" is irrelevant.  

In my experience, in Feisty, the workspace switcher has not activated the cube animation.  I activated it by using gnome-compiz-preferences.  The workspace switcher is just a gnome panel object you can add to manage the amount of workspaces you have.

---

### Post by ace007 on 2008-02-17
I got the 3-D cube animation to work by:

1.) launching gnome-compiz-preferences
2.) selecting Workspaces tabs.
3.) Under Effects selecting cube and rotation
4.) setting viewports to 4
5. ) Under Cube set skydome on and animate on
6.) Under rotation set all to on

I know gutsy has more advanced options from the compiz-fusion-preferences GUI but this is all I have found in Feisty

---

### Post by bumanie on 2008-02-17
I personally have been unable to get compiz-fusion to work in feisty. The only time I had any sort of luck with advanced effects was when I used beryl before the project was fused with compiz.

---

