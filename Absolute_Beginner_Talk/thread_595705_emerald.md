---
title: "emerald"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by ubunt22rock on 2007-10-29
i have ubuntu7.10

compizfusion is rocking and i m quite sure i installed emerald

but i dont know how to change themes with emerald...i dont how to open emerald theme manager window

---

### Post by ed-koala on 2007-10-29
Emerald Theme Manager should be under System - Preferences if it is installed.  If you don't see it there, check Synaptic to be sure it is installed.

As for using it, not sure myself, tho I did go in and play around with it and made myself a cool blue transparent title bar and boarder for my windows.  Have not figured out how to fix the screenshot or buttons yet, but have not done that much with it yet.

Learning by fiddling is half the fun!

---

### Post by ubunt22rock on 2007-10-29
yep learnin s fun alrite :KS  

its installed in synaptic


but system->preferences-> has advanced desktop effects settings opens the ccms window 

cant find emerald nowhere

---

### Post by santiagoward2000 on 2007-10-29
> **ubunt22rock said:**
> yep learnin s fun alrite :KS  

its installed in synaptic


but system->preferences-> has advanced desktop effects settings opens the ccms window 

cant find emerald nowhere

Hi,
try opening a Terminal and type
```
emerald --replace
```
this should get emerald running.

---

### Post by ed-koala on 2007-10-29
Open up System - Preferences - Main Menu
Expand the Preferences button on the left side.
You should see an entry for Emerald Theme Manager - check the box.
Close and you should have it showing now under that Preferences menu.

If you do not see it listed to check:
Right click on your desktop
Choose create launcher
Name the launcher - ie Emerald Theme Manager
Browse to usr/share/applications and select Emerald Theme Manager
Optional - add a note
Click ok.
This adds a shortcut on your Desktop, if you want it in the panel, drag it up there. You may even be able to drag it into the Main Menu list (didn't try that)

---

### Post by ubunt22rock on 2007-10-29
@santiagoward2000

emerald --replace causes nothing i  had to abort it with ctrl+c to get my shell prompt

---

### Post by ed-koala on 2007-10-29
Oops!  Instead of part 2 above - Click on Add item in the right panel of Main Menu and add Emerald - you'll find the file as in part 2 above.

---

### Post by santiagoward2000 on 2007-10-29
> **ubunt22rock said:**
> @santiagoward2000

emerald --replace causes nothing i  had to abort it with ctrl+c to get my shell prompt

Hmmm, that's strange

---

### Post by ubunt22rock on 2007-10-29
@ed-koala

hey i added the launcher

but wen i double-clicked it 

an error box read:Details: Failed to execute child process "/usr/share/applications/emerald-theme-manager.desktop" (Permission denied)

---

### Post by santiagoward2000 on 2007-10-29
OK, I think I made a mistake. Instead of typing it on a Terminal, press Alt+F2 and type emerald --replace there.

---

### Post by ed-koala on 2007-10-29
NP - Go back into Main Menu and highlight Emerald Theme Manager
Right click it and select properties
Change text to read -- emerald-theme-manager -i
Close and you're in business.

Copied this from my main menu, so it should be perfect.

---

### Post by ubunt22rock on 2007-10-29
@ed-koala and @sandiagoward2000


i tried the revised solutions from both of u and the same errors persist

---

### Post by santiagoward2000 on 2007-10-29
OK, when you typed emerald --replace on the terminal, did it give you any error messages?

---

### Post by ubunt22rock on 2007-10-29
@santiago.....

nope no error msgs...

and hey most of the times my titlebar in all windows just vanish....

wat do i do??

---

### Post by ubunt22rock on 2007-10-29
@ed koala

xactly in which text box do i type it cos i dont find anything relevant to wat u have typed

---

### Post by santiagoward2000 on 2007-10-29
Have you already chosen the theme you want from Emerald Theme Manager? Just clicking on the one I want and then reloading emerald works for me.

---

### Post by ubunt22rock on 2007-10-29
if i have already installed it i am not awarw...and how exactly do i 'reload' emerald when its not running already

---

### Post by santiagoward2000 on 2007-10-29
> **ubunt22rock said:**
> if i have already installed it i am not awarw...and how exactly do i 'reload' emerald when its not running already

Type:
```
emerald-theme-manager
```
on a terminal and if at least the manager runs.

---

### Post by ubunt22rock on 2007-10-29
hey it runs...now how do i download themes

---

### Post by ubunt22rock on 2007-10-29
please help me with selecting themes with emerald

---

### Post by santiagoward2000 on 2007-10-29
> **ubunt22rock said:**
> hey it runs...now how do i download themes

There are some in:
[www.gnome-look.org]("www.gnome-look.org")
[http://compiz-themes.org/]("http:///compiz-themes.org/")
[www.kde-look.org]("www.kde-look.org")

They appear under Beryl, but they work on Compiz-Fusion too.

---

### Post by ubunt22rock on 2007-10-29
oh but in that window there are a few options lik create theme n export....
xactly to which path do i exoprt for my new theme to work

---

### Post by ubunt22rock on 2007-10-29
and i jus dwnloaded a theme it opens in emerald...how do i apply...
there is no change

---

### Post by santiagoward2000 on 2007-10-29
> **ubunt22rock said:**
> and i jus dwnloaded a theme it opens in emerald...how do i apply...
there is no change

Open the Emerald Theme Manager, click on Import and select the theme you dowloaded. The, click on it, and reload emerald with emerald --replace.

---

### Post by ubunt22rock on 2007-10-30
but its not the same as is shown in the preview

---

### Post by opferstad on 2007-10-30
I can't find Emerald in the Add/Remove Applications window. *sudo apt-get install emerald-theme-manager* doesn't work either.

---

### Post by ubunt22rock on 2007-10-30
@opferstad

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by santiagoward2000 on 2007-10-30
> **opferstad said:**
> I can't find Emerald in the Add/Remove Applications window. *sudo apt-get install emerald-theme-manager* doesn't work either.

Try sudo apt-get install emerald.
You can find it on Synaptic too.

---

### Post by Brian031168 on 2007-11-25
I am still having a problem applying themes with Emerald Theme Manager. I start the manager click on the theme I want and then hit ALT-F2 & type emerald --replace but nothing happens, no changes are made to my theme.

Any ideas?

---

