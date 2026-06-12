---
title: "My List of Problems"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by Spoken on 2008-02-08
Alright, i have a few problems going on with my computer right now, so let me just give you my specs and then the problems, lets see if we cant pin point the issues.

[SIZE="5"]My Computer Specs[/SIZE]

I use Gutsy 7.10, and i have Compiz Fusion open on startup.  All of these problems still happen even with compiz turned off except for #6

Inspiron 1420N - Intel® Core&#8482; 2 Duo T7500 (2.2GHz/800Mhz FSB/4MB cache) - Intel Graphics Media Accelerator X3100 - 2GB Shared Dual Channel DDR2 at 667MHz - 160GB SATA Hard Drive (7200RPM) - 85Whr Lithium Ion Battery (9 cell)

[SIZE="5"]My Computer Problems[/SIZE]

1)When i login, sometimes it will take a unusual amount of time to load, and i dont see why because i have decent components.

2)Sometimes after i login, my panel (that contains my clock, main menu, and all of that, which is located at the bottom of my screen) wont show up, but if i do the cube effect (ALT + CTRL + CLICK) then it will appear and stay there. Why cant i see it?

EDIT: The panel is like invisable, cause if i hover my mouse over the area it is supposed to be at, i can still click on stuff.

3)I recently installed "freewins" plugin for Compiz fusion, and after using it for about...i dont know, 15 mins, my computer "hitched" up i guess, i dont really know what happened, but ALL of my compiz fusion settings that i configured, for ALL of the plugins i used, went back to default.  Why did it do that?

4)I cant change my cursor, the "cursor selection" thing under preferences is broken.  When i click "install" or "theme folder" , they dont do anything, and i cant drag and drop any .tar files into the list.  I have a new cursor install that i want to put to use :o

5)Sometimes when im watching vids on youtube, and i click on another vid, the window will freeze up and grey over, then i have to click the close button and hit "force quit", then reopen firefox.  Its super annoying.

6)When i have compiz fusion enabled, and i try to open "movie player" to listen to music or whatever, the movie player window will open up breifly but then close again.

---

### Post by nynoah on 2008-02-08
sounds like you are having graphics driver problems.  I would go to*System/administration/restricted drivers manager* and uninstall your restricted drivers.   Reboot your computer and reinstall them.  See what happens after that.  Follow any instructions if it says you need to download a dependency.

Hope that helps.

---

### Post by Spoken on 2008-02-08
kk, i will try it, give me a min and i will reply with my result.

---

### Post by Spoken on 2008-02-08
The only restricted drivers that are in there are the following

Conexant Modem Engine

and the

Intel(R) PRO/Wireless 3945 Network Connection Driver for Linux

They are both enabled and In use

First off, do i need to uninstall either of these, and if yes, how do i do that.

---

### Post by Spoken on 2008-02-08
.

---

### Post by nynoah on 2008-02-08
don't mess with your wireless driver.  Otherwise, you will have no internet through wireless.   Bad bad.

Are you telling me you have no video drivers that are installed?

---

### Post by Spoken on 2008-02-08
It looks as if i do not have any video drivers installed lol.....how do i make remedy of this?

---

### Post by nynoah on 2008-02-08
***system/administration/restricted driver manager***  when you open that does it prompt you about installing the correct drivers for your system?

---

### Post by Spoken on 2008-02-08
Nope, it just opens normally and shows me those 2 drivers that are already installed.  Am i in trouble lol?

---

### Post by aJayRoo on 2008-02-08
I don't think Intel requires a restricted driver so it is fine that you don't see one there. As regards the mouse cursor themes... compiz can/does override the theme with the one that was in use when it was started. To change the mouse theme in compiz you first need to install compiz config settings manager:
```
sudo apt-get install compizconfig-settings-manager
```
Then go to the system menu -> advanced desktop effects and click on the general settings part at the top. From there you can change the cursor theme for compiz. Hope some of that helps!

---

### Post by Spoken on 2008-02-08
I already have ccsm installed, but when i type in the name of the cursor theme i want, it doesnt do anything. :l

---

### Post by Spoken on 2008-02-08
.

---

### Post by nynoah on 2008-02-08
A good way to change your cursor is to go to ***System/preferences/appearence***  Then in there - click install  and install what you are talking about.  Then restart your computer and see if it shows up in the prefernces manager.  

You will find the new one in there.  You will need to hit customize - pointer and it should be in there.

---

