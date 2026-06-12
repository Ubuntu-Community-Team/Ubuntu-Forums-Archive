---
title: "Need help with Ubuntu Bugs."
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by personal-data-removed on 2007-10-12
I am using Ubuntu 7.04.
I have found some bugs, that are disapointing.

BUG 1
The "Aplication local system" bar and "trash can" bar, i want to place on top of screen the  "Aplication local system", then bellow it the "trash can bar", on restart the ubuntu switches the 2 bars.

BUG 2
Icons, i place many icons on the "aplication local system" bar, but at restart half of the icons desapear.

BUG 3
Splash screen, i loaded one. Then i decided to deleted, and chose another. The one i installed first doesnt delete.

BUG 4
Graphical bug on firefox windows, sometimes using Firefox, i must maximize the window to see images on page. 
I am using nvidia card with all the drivers well configured in ubuntu.

And i have some trouble in doing some things, i need help.

1. I want to have super user privilegies. 
I only manage to be super user by using krusader on special mode.

2. Wine. I have installed, avernum IV. Mouse too slow, unplayable.
I decided to delete. But because of error, the avernum briefcase is still in aplications-wine , i could not delete it. I manage to delete all the game in wine. I want to delete the shorcuts on the bar, but it seams impossible.

3. aMSN. How to configure it to activate by itself at ubuntu start.

English is not my first language, sorry for mistakes typing, i need some advice to solve the bugs. 
Kubuntu as less bugs than Ubuntu ?
I prefer gnome and firefox, but i prefer better stuff with no bugs.

---

### Post by aspen_dv on 2007-10-12
Answer in blue
> **jocampeao said:**
> I am using Ubuntu 7.04.
I have found some bugs, that are disapointing.

BUG 1
The "Aplication local system" bar and "trash can" bar, i want to place on top of screen the  "Aplication local system", then bellow it the "trash can bar", on restart the ubuntu switches the 2 bars.
[COLOR="Blue"]No idea what you want! Do you want to put the trash icon on the top bar? Right click on empty space at the top bar, then "add to this panel", select the trash icon[/COLOR]

BUG 2
Icons, i place many icons on the "aplication local system" bar, but at restart half of the icons desapear.
[COLOR="Blue"]Again, not sure what you want! Add apps to the top panel the same way as above. It works fine for me. [/COLOR]
BUG 3
Splash screen, i loaded one. Then i decided to deleted, and chose another. The one i installed first doesnt delete.
[COLOR="Blue"]Does this mean the splash image does not change? or you can't delete it from local disk drive?
Ok, here the steps to change splash image
How to change the gnome splashimage.
1. Put the splash image you want in "png" format and store it in /usr/share/pixmaps/splash. (You can use Nautilus or the "cp" or the "mv" command from the terminal window if you want. Just remember to use "sudo" before your command. )
2. Press ALT-F2 then at the prompt type "gconf-editor" (without the quotes).
3. Click on "apps" then "gnome-session" then "options".
4. To the right of the Name "splash_image" double click on the Value "splash/ubuntu-splash.png".
5. Change "splash/ubuntu-splash.png" to reflect your new splash image: "splash/newsplash.png".
6. Click on "File" then "Quit".
7. Logout then login in again to see your new splashimage.
[/COLOR]

BUG 4
Graphical bug on firefox windows, sometimes using Firefox, i must maximize the window to see images on page. 
I am using nvidia card with all the drivers well configured in ubuntu.

[COLOR="Blue"]not sure if its a bug?[/COLOR]

And i have some trouble in doing some things, i need help.

1. I want to have super user privilegies. 
I only manage to be super user by using krusader on special mode.
[COLOR="Blue"]As root, please do "/usr/sbin/visudo".

That will open the visudoers file in vi. Search for the line that says;

root    ALL=(ALL)       ALL

and add below it the following line;

yourloginname ALL=(ALL)       NOPASSWD: ALL

then write and quit.[/COLOR]

2. Wine. I have installed, avernum IV. Mouse too slow, unplayable.
I decided to delete. But because of error, the avernum briefcase is still in aplications-wine , i could not delete it. I manage to delete all the game in wine. I want to delete the shorcuts on the bar, but it seams impossible.
[COLOR="Blue"]No idea[/COLOR]

3. aMSN. How to configure it to activate by itself at ubuntu start.
[COLOR="Blue"]System-Preferences-Sections, Start-up tab, then add your program[/COLOR]

English is not my first language, sorry for mistakes typing, i need some advice to solve the bugs. 
Kubuntu as less bugs than Ubuntu ?
I prefer gnome and firefox, but i prefer better stuff with no bugs.

---

### Post by phr0ze on 2007-10-12
2. Wine. I have installed, avernum IV. Mouse too slow, unplayable.
I decided to delete. But because of error, the avernum briefcase is still in aplications-wine , i could not delete it. I manage to delete all the game in wine. I want to delete the shorcuts on the bar, but it seams impossible.


[COLOR="Blue"]SYSTEM->Preferences->Main Menu, Then delete the items you don't want.[/COLOR]

---

### Post by Ink-Jet on 2007-10-12
Running as super-user is silly.

---

### Post by phr0ze on 2007-10-12
I second Ink-Jet. Why would you want to do this. Sudo has always been sufficient for me.

---

### Post by personal-data-removed on 2007-10-12
"Running as super-user is silly."

Thanks for trying to help, but please dont post this kind of answers. 
This is of no use, what i can use is the information. 

@aspen_dv
Thanks for the information.

No idea what you want! 

The "Aplication local system" bar and "trash can" bar, i want to place on top of screen the "Aplication local system", then bellow it the "trash can bar", on restart the ubuntu switches the 2 bars.

Do you want to put the trash icon on the top bar?
No. I want to use the 2 bars the Aplication-locals-system bar AND the bar who as trash can as default on the top on the screen. 
I want the bar on the top of the 2 to be the Aplication-locals-system, but at restart the system always switch  the bars. Is a bug, there is any trick to overcame it ?

"Add apps to the top panel the same way as above. It works fine for me."
It doesnt work for me. I add icons (applications shortcuts) to Application-locals-system bar, and it works fine, but at restart half of the icons desapear, why ?

"Ok, here the steps to change splash image"
I can change the splash image. What i can not do is to delete one that i downloaded and activated. I delete... but at restart it appears again. I delete in system-preferences-splash screen application.

"Click on "apps" then "gnome-session" then "options".
My system is in portuguese. I think i have a session icon on system not on apps, i followed the steps, after this i restart to see if worked.

"sometimes using Firefox, i must maximize the window to see images on page." This is a video card driver bug, or firefox bug ?

1. I want to have super user privilegies.
I only manage to be super user by using krusader on special mode.

Super user. 

0. As root, please do "/usr/sbin/visudo".

1. open the visudoers file in vi. 

2. Search for the line that says; root ALL=(ALL) ALL

3. add below it the following line;
yourloginname ALL=(ALL) NOPASSWD: ALL

4.  write and quit.

Thanks, im going to try.


"Wine. No idea."
I have on the "Aplication-locals-system" bar a dead link (Avernum IV) on wine, how can i delete this dead link ?

3. aMSN. How to configure it to activate by itself at ubuntu start.
System-Preferences-Sections, Start-up tab, then add your program.
I dont have start-up tab on preferences, but i have it inside sessions.
Ok, i added aMSN and Beryl, after this i restart, and should be fine.

---

### Post by personal-data-removed on 2007-10-12
After restart.

Problems solved:

a) Aplication icons are now saved. Probably the save session fixed it.
b) aMSn and Beryl now start at system start.
c) Splash image deleted.
d) Dead link at wine.

Not solved:
a) System still switch the bars.
b) Could not test firefox/graphic card bug, only happens sometimes.

---

### Post by personal-data-removed on 2007-10-12
@phr0ze  	
Thanks for the info.

Problem solved.

---

