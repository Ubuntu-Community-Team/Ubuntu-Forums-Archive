---
title: "After installing Games via Synaptic only 10% have Icons in the Menu !"
date: 2005-07-19
forum: Bug Reports / Support
---

### Post by redlabour on 2005-07-19
[https://bugzilla.ubuntu.com/show_bug.cgi?id=12798](https://bugzilla.ubuntu.com/show_bug.cgi?id=12798)

Hi,

i think there is something to make better at the Packages for all Games at the 
Repisitories (Main , Backports etc.).

After i go to install about 100 Games via Synaptic there are still only 25 Icons at 
KMenu and the Gnome Menu.

How can that be ? :-(

---

### Post by dave9191 on 2005-07-19
Not every program installed using synaptic automatically shows in the menus. I find most packages add a menu entry to the debian menu which the last time i used gnome (back in warty) didnt have the debian menu in gnome. And even so, not all programs are configured to add a menu item at all. Try typing the name of the program into a console to start it. 

Dave

---

### Post by redlabour on 2005-07-19
[QUOTE=dave9191]Not every program installed using synaptic automatically shows in the menus. I find most packages add a menu entry to the debian menu which the last time i used gnome (back in warty) didnt have the debian menu in gnome. And even so, not all programs are configured to add a menu item at all. Try typing the name of the program into a console to start it. 

Dave[/QUOTE]
 Sure dave9191 - but no - i use Ubuntu and not Gentoo.  ;)

I believe Ubuntu stands for Usability and not for Consolegangbangs. ;)

---

### Post by Lord Illidan on 2005-07-19
yeah, it happened to me too..I just use the Debian menu...

---

### Post by Lord Illidan on 2005-07-19
[QUOTE=redlabour]Sure dave9191 - but no - i use Ubuntu and not Gentoo.  ;)[/QUOTE]

What do you mean? You can use a terminal from Ubuntu..in fact you can use a terminal from any distro..just go on Applications menu --> System Tools --> Terminal

---

### Post by redlabour on 2005-07-19
[QUOTE=Lord Illidan]What do you mean? You can use a terminal from Ubuntu..in fact you can use a terminal from any distro..just go on Applications menu --> System Tools --> Terminal[/QUOTE]
 Welcome to the Year 2005 ! 

Windows -> 1 Klick and a few Mouse moves
Mandriva, SUSE, Fedora -> 1 Klick and a few Mouse moves

Ubuntu -> 1 Klick for Synaptic -> another Klick to the Games Sections -> looking for the Games installed -> 1 Click opening Console -> Typing Gamename ..... :D

Any other Questions ??

---

### Post by dave9191 on 2005-07-19
I think that he means that he's not using ubuntu to use the command line, but rather a graphical enviroment. 

But if you know the location of a the executable binary file then just add it to the menu yourself. The same applies to windows, sometimes programs dont give you a start menu entry and you need to know where they are to make a menu item or icon. 

Also you can use the run dialog to start programs, i find that quicker and more convinetnt then having to navigate menu and click on the program i want. Hit the keyboard shortcut for thr run dialog, type the command and presto.

---

### Post by dave9191 on 2005-07-19
Or just setup keyboard bindings for every program that you want to use, ive done that and i dont even need to move my hand of the keyboard to the mouse... 0 clicks :)

Dave

---

### Post by redlabour on 2005-07-19
[QUOTE=dave9191]Or just setup keyboard bindings for every program that you want to use, ive done that and i dont even need to move my hand of the keyboard to the mouse... 0 clicks :)

Dave[/QUOTE]
 @dave9191 - You are right in something of your Answer. 

I am not using Ubuntu to use the Console. ;) (Ok - sometimes at the first Configuration after a fresh Installation !)

And of course it is possible to edit the Menu by my own.  But why ? 

It works fine at 99,9 % of SUSE, Mandriva or Fedorapackages - and at Ubuntu only 20% ?? 

I think first of all the Packagers have to make a better work. I respect their work - but that are 2 Minutes more for one Menuentry for every Game for GNOME and KDE. And i think this isnt to much time . ;)


But i don´t know when was you´re last Time you used Windows ??? :D In the last 5 years i didn´t fund any Application with no Startmenuentry !? :P

---

### Post by dave9191 on 2005-07-19
I run windows on my other computer and I get annoyed at everything it does. Like fill my start menu with junk and spit icons on the desktop. 

But like I said most of the packages put an entry to the debian menu which ubuntu doesnt use (well it didnt in the last version). If you run kde you'll have access to it. 

Dave

---

### Post by redlabour on 2005-07-19
[QUOTE=dave9191]I run windows on my other computer and I get annoyed at everything it does. Like fill my start menu with junk and spit icons on the desktop. 

But like I said most of the packages put an entry to the debian menu which ubuntu doesnt use (well it didnt in the last version). If you run kde you'll have access to it. 

Dave[/QUOTE]
 Ok thx so far ...... but this can´t be the final solution. ;)

---

### Post by dave9191 on 2005-07-19
Well ubuntu is still a work in progress and a farily new distro :) And a solution would be to put the debian menu into the gnome panel. But they are discussing and considering it. 

Dave

---

### Post by MikeyXX on 2005-07-19
Well, how can he (we) create the icons in the menu if he (we) choose to do this manually?

---

### Post by redlabour on 2005-07-19
[QUOTE=MikeyXX]Well, how can he (we) create the icons in the menu if he (we) choose to do this manually?[/QUOTE]

 Some of them with kappfinder, the other ones with Kmenuedit or smeg.

---

### Post by dave9191 on 2005-07-19
If you have gnome you should be able to right click in the submenu and create a new item. But I cant be more spesific then that. I dont know if they added the menu editor yet. And in kde there is a menu editor if you right click on the kmenu. 

Dave

---

### Post by redlabour on 2005-07-19
[QUOTE=dave9191] And in kde there is a menu editor if you right click on the kmenu. 

Dave[/QUOTE]

That is Kmenuedit for KDE ! ;)

For GNOME there is SMEG : [http://www.ubuntuforums.org/forumdisplay.php?f=67](http://www.ubuntuforums.org/forumdisplay.php?f=67)

---

### Post by ep_ on 2005-07-20
[QUOTE=dave9191]I run windows on my other computer and I get annoyed at everything it does. Like fill my start menu with junk and spit icons on the desktop. 

But like I said most of the packages put an entry to the debian menu which ubuntu doesnt use (well it didnt in the last version). If you run kde you'll have access to it. 

Dave[/QUOTE]
 I use KDE.  If I add a Debian menu entry, will the packages I install (or some of them) start adding menu entries there?  Also, question on adding them manually.  Do any of them use switches?

---

### Post by dave9191 on 2005-07-20
You should have a submenu in the k menu called debian. that should have a list of all the apps installed on your comp using deb packages. And what do you mean do they use switches ?

Dave

---

### Post by redlabour on 2005-07-20
[QUOTE=dave9191]You should have a submenu in the k menu called debian. that should have a list of all the apps installed on your comp using deb packages. And what do you mean do they use switches ?

Dave[/QUOTE]
 Maybe i did not understand you dave9191 - but there is no Debianmenu (and i know what you mean) either under GNOME and KDE.

Under GNOME it is showable with SMEG but it is empty. Under KDE it isnt anywhere.

---

### Post by dave9191 on 2005-07-20
In my K menu at the top of it above games or whatever is at the top I had an entry called "Debian". And no in fluxbox I have a submenu called apps that has the same programs. I dont run KDE anymore, but here is a fluxbox snap shot. 

Dave

---

### Post by Juergen on 2005-07-20
I have the Debian menu in Gnome.

AFAIR it appeared after updating from Warty to Hoary via apt-get.

Hm, maybe I can find out which package creates it...

---

### Post by ep_ on 2005-07-20
[QUOTE=dave9191]You should have a submenu in the k menu called debian. that should have a list of all the apps installed on your comp using deb packages. And what do you mean do they use switches ?

Dave[/QUOTE]


I did apt-get Install kubuntu-desktop and I don't have  a submenu called Debain on the K-menu.  I could make one but I wasn't sure whether or not that would do me and good.  By "switches", I meant command-line arguments or something that looks like  similar to a command line switch.  Seems some menu items use them.

How might one determine what arguments to use if making a menu item from scratch?.  Ordinarily, one would copy the item from Debian menu, but alas it isn't there.

---

### Post by TravisNewman on 2005-07-20
[http://www.ubuntuforums.org/showthread.php?t=32220&highlight=debian+menu](http://www.ubuntuforums.org/showthread.php?t=32220&highlight=debian+menu)

That tells you how to install the debian menu.

---

### Post by redlabour on 2005-07-20
[QUOTE=panickedthumb][http://www.ubuntuforums.org/showthread.php?t=32220&highlight=debian+menu](http://www.ubuntuforums.org/showthread.php?t=32220&highlight=debian+menu)

That tells you how to install the debian menu.[/QUOTE]
 THX ! :D

---

### Post by dave9191 on 2005-07-20
I thought that the debian menu was standard with kubuntu. And if you have ubuntu apt-get kde would give you one as well. But now everyone can have it with the howto link :)

Dave

---

### Post by charlieg on 2005-07-24
What is the solution to this?
[list=1][*]Wait for the applications to patch themselves with .desktop files
[*]Create .desktop files and package them with the .debs
[*]Send .desktop file patches upstream[/list]
Somebody who knows a thing or two about a thing or two pick one of the above so that we lay users can start poking the people that matter and providing .desktop files to get the apps into the menu without resorting to using the debian menu.

---

### Post by Burgundavia on 2005-07-24
As charlieg said, all applications need a .desktop file. If you want a game to have a menu entry, create a .desktop file, file a bug in malone on the package and place the .desktop there. 

If you need examples, all .desktop files in Ubuntu are stored in /usr/share/applicaions.

Corey

---

### Post by DirtDawg on 2005-07-25
Okay, Redlabour brings up a "problem" with Hoary near and dear to my heart. One of my absolute favorite things about Warty was the ability to click the RMB over any menu to edit not only the menu items, but the icons that accompany them.
Last week I finally upgraded to Hoary which has been an improvement in almost every way, BUT, I cannot figure out how to customize the menu items or their icons! Why did the developers change this? I miss this ability dearly.

---

