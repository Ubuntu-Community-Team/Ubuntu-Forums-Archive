---
title: "I'm a Beginner:: Would you please kindly help me install the Cario Dock?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by ahuman on 2008-02-25
[CENTER][COLOR="Green"][FONT="Palatino Linotype"][SIZE="4"]Would any of you be patient enough to please help me & others who don't quite understand exactly how to install the Cario Dock on our computers. In my case, I'm using a Dell Inspiron 531s which is installed with Ubuntu 7.10 (Gusty Gibbons) it has a built-in NVidia video card (drivers included) and it's running on the AMD64 (64Bits) system?

I'll start by highlighting the problems I've been having with the installation-instructions (which I have listed 1-7):

Instruction #1:[/SIZE][/FONT][/COLOR][/CENTER]
**1.** Your system should be capable of and **running Desktop Effects**. Without it, Cairo Dock works but doesn't look as good as it can (no transparency for instance). If you have a NVidea or ATI graphics card, you might have to take a few more steps to get at this point. There are a lot of threads and How-to's on that on these forums. For good instructions on installing the latest ATI drivers using AIGLX on *Gutsy*, see _[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually)_.

[COLOR="DarkBlue"][FONT="Palatino Linotype"][SIZE="4"]Problem 1: I don't know if I need the AIGLX thing. Would you tell me if the NVidia video card needs to be using AIGLX (to make the Cario Dock appear transparent for instance)?[/SIZE][/FONT][/COLOR]

[SIZE="4"][COLOR="Green"][CENTER][FONT="Palatino Linotype"]Instruction #2:[/SIZE][/FONT][/COLOR][/CENTER]
**2.** Also, the **Cairo libraries** should be installed. It is not called Cairo Dock for nothing ;)
```
sudo apt-get install libcairo2 librsvg2-2 libglitz1 libglitz-glx1 dbus libdbus-1-3 libdbus-glib-1-2 libvte9 libxxf86vm1
```
NOTE: Since version 1.5.0.1, there are separate dependencies for the Cairo Dock Plug-ins package. The above command should take care of those dependencies...

[COLOR="Green"][FONT="Palatino Linotype"][SIZE="4"]*No Problem:* Those instructions made perfect sense to me, and that code seemed to work.:[/SIZE][/FONT][/COLOR]

[SIZE="4"][COLOR="Green"][CENTER][FONT="Palatino Linotype"]Instruction #3:[/SIZE][/FONT][/COLOR][/CENTER]
**3.** You will need to have the excellent 32bit library dependency tool that should be on EVERY 64bit system called **Getlibs** installed on your system. If you did not do so already, follow instructions on _[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)_.

[COLOR="DarkBlue"][FONT="Palatino Linotype"][SIZE="4"]Problem 2: I don't know if all of the instructions on that [forum-thread](http://ubuntuforums.org/showthread.php?t=474790) are necessary to follow, in my case. Would you tell me which of those examples on that [webpage](http://ubuntuforums.org/showthread.php?t=474790) are necessary to follow, in order to make the Cario Dock work on my computer?[/SIZE][/FONT][/COLOR]

[SIZE="4"][COLOR="Green"][CENTER][FONT="Palatino Linotype"]Instruction #4:[/SIZE][/FONT][/COLOR][/CENTER]
**4.** Download the latest cairo-dock 32bit deb files.

[COLOR="Green"][FONT="Palatino Linotype"][SIZE="4"]*No Problem:* I went to the previously mentioned [webpage](http://developer.berlios.de/project/showfiles.php?group_id=8724), and downloaded all 4 of those files:

Here's a screenshot from the files I found on that  [webpage](http://developer.berlios.de/project/showfiles.php?group_id=8724):
[IMG]http://img141.imageshack.us/img141/4687/0wenttoberliosdeveloperer1.png[/IMG]

I successfully installed those 2 .deb-files: cairo-dock-plug-ins_v1.5.1_i686-32bits.deb &  cairo-dock_v1.5.1_i686-32bits.deb (as seen in the 2 following screenshots):
[img]http://img84.imageshack.us/img84/377/2gdebigtkunstalledpart3gn5.png[/img]

[img]http://img206.imageshack.us/img206/7/4installedcariodockplugtr7.png[/img][/SIZE][/FONT][/COLOR]

[SIZE="4"][COLOR="Green"][CENTER][FONT="Palatino Linotype"]Instruction #5:[/SIZE][/FONT][/COLOR][/CENTER]
**5.**...You need two deb files, one called **cairo-dock_vX.X.X.X_i686-32bits.deb** and the other **cairo-dock-plug-ins_vX.X.X.X_i686-32bits.deb** (where the X's represent the latest version number, 1.5.0.1 at the time of writing this) from _[http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724)_ to your home folder.

[COLOR="DarkBlue"][FONT="Palatino Linotype"][SIZE="4"]Problem 3: I don't know exactly what this part of instruction #5 means: "...from _[http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724)_ to your home folder."

Two questions about *problem 3*:
 Would any of you please tell what that means?To get the *Cairo Dock* to install correctly, would I have to drag & drop those .deb files to my home folder or "Extract" them in that same folder?

Problem 4: I don't know what to do with cairo-dock-sources-20080219.tar.bz2. 

One question about *problem 4*:
Please give me step-by-step instructions about what I should do with this package/file: cairo-dock-sources-20080219.tar.bz2[/SIZE][/FONT][/COLOR]

[SIZE="4"][COLOR="Green"][CENTER][FONT="Palatino Linotype"]Instruction #6:[/SIZE][/FONT][/COLOR][/CENTER]
**6.** Open a terminal screen and run
```
sudo dpkg -i --force-all cairo-dock*.deb
```
```
sudo getlibs /usr/bin/cairo-dock
``` (see prerequisite 3 above if this results in an error)

[COLOR="DarkBlue"][FONT="Palatino Linotype"][SIZE="4"]I haven't tried any of those commands  in instruction #7, yet, but I will do so, after problem 1-3 are solved. Please help me.[/SIZE][/FONT][/COLOR]

[SIZE="4"][COLOR="Green"][CENTER][FONT="Palatino Linotype"]Instruction #7:[/SIZE][/FONT][/COLOR][/CENTER]
**7.** Try to fire up Cairo-Dock by giving the command ```
cairo-dock
``` in the same terminal screen and see if there are any dependency errors left. If so, use the 'manual 32bit libs installation' described on the getlibs page above to get them. **If no dependencies are left open, cairo-dock should run and present you it's first-time theme manager dialog**.

[COLOR="DarkBlue"][FONT="Palatino Linotype"][SIZE="4"]Like I mentioned before, I haven't tried any of those commands in instruction #7, yet, but I will do so, after problem 1-4 are solved.  I'd appreciate any future-help given to me, in this case.[/SIZE][/FONT][/COLOR]

---

### Post by ahuman on 2008-02-25
[SIZE="4"][FONT="Georgia"][COLOR="DarkBrown"]:) Please tell me if I shouldn't have asked so many questions in my 1st post. I really want to understand how to install Cario Dock. That's why I asked so much about it.[/COLOR][/FONT][/SIZE]

---

### Post by tact on 2008-02-25
> **ahuman said:**
> 
Instruction #1:
**1.** Your system should be capable of and **running Desktop Effects**. Without it, Cairo Dock works but doesn't look as good as it can (no transparency for instance). 

Problem 1: I don't know if I need the AIGLX thing. Would you tell me if the NVidia video card needs to be using AIGLX (to make the Cario Dock appear transparent for instance)?


Sorry I have no experience with NVidia video cards but you can try turning on the desktop effects that come built in with ubuntu 7.10.  If it works then you need not go any further. 

To turn it on... CLick:   System>Preferences>Appearance.   Click on the visual effects tab and select "Extra" effects.  If you get no error message AND you notice that menus have some transparency and windows wobble like jelly when you grab the title bar and give it a shake...  then your "desktop effects" are working.

> **ahuman said:**
> 
Two questions about *problem 3*:
 Would any of you please tell what that means?To get the *Cairo Dock* to install correctly, would I have to drag & drop those .deb files to my home folder or "Extract" them in that same folder?

No need to do anything more here...  you have the debs.  Thats enough for now.  You need not extract them or even move them to home folder if you don't want to.

> **ahuman said:**
> 
Problem 4: I don't know what to do with cairo-dock-sources-20080219.tar.bz2. 

One question about *problem 4*:
Please give me step-by-step instructions about what I should do with this package/file: cairo-dock-sources-20080219.tar.bz2

Just delete it.  You dont need the program source files.

> **ahuman said:**
> 
Instruction #6:[/SIZE][/FONT][/COLOR]
**6.** Open a terminal screen and run
```
sudo dpkg -i --force-all cairo-dock*.deb
```


This installs the debs for you.  Simply double clicking on them on your desktop (or whatever folder you have placed them) will also do the trick.

---

### Post by tact on 2008-02-25
Provided your desktop effects work - BIG proviso there....   all you need to do to install cairo dock is"

First install the packages libcairo2 and librsvg2-2.
```
sudo apt-get install libcairo2 librsvg2-2
```
(this bypasses the need to figure out how to install the getlibs tool)

Then install the two .deb files you already downloaded by double-clicking on the downloaded files.  (Do the dock first and plug-ins later.)

Ciao

---

### Post by stoodleysnow on 2008-02-25
AIGLX is for ATI video/graphics cards.

You may need the restricted *Nvidia* driver to make your Nvidia card support Compiz Fusion effects, but otherwise Cairo should install as shown above. If you don't see it straight away on your desktop, you may need to check your Applications menu (Accessories) to click the icon to get it going.

---

### Post by ahuman on 2008-02-25
> **tact said:**
> Sorry I have no experience with NVidia video cards but you can try turning on the desktop effects that come built in with ubuntu 7.10.  If it works then you need not go any further.
[COLOR="Purple"]**The Desktop Effects do not seem to be related to the installation of the Cairo Dock. I need to know how to get that on my computer, without skipping any of the instructions that I listed in my introductory/original post (in this forum-thread).**[/COLOR] 

> **tact said:**
> To turn it on... CLick:   System>Preferences>Appearance.   Click on the visual effects tab and select "Extra" effects.  If you get no error message AND you notice that menus have some transparency and windows wobble like jelly when you grab the title bar and give it a shake...  then your "desktop effects" are working.
[COLOR="Purple"]**Like I mentioned above, I don't see how any of that is related to the installation of the Cairo Dock. I need advice that's relevant to my original post. I'm dealing with the instructions (1-7)**[/COLOR] 

> **tact said:**
> No need to do anything more here...  you have the debs.  Thats enough for now.  You need not extract them or even move them to home folder if you don't want to.

Just delete it.  You dont need the program source files.

This installs the debs for you.  Simply double clicking on them on your desktop (or whatever folder you have placed them) will also do the trick.
[COLOR="Purple"]**How am I going to get the Cario Dock if I get rid of the files that were recommended in those instructions (1-7), about which I started discussing in my original post, above?**[/COLOR] 

[COLOR="Green"][B][FONT="Book Antiqua"]I appreciate your help Tact. I would also appreciate it if someone would tell me what I really need to do in order to get that Cairo Dock on my computer.

I already installed those plug-ins: cairo-dock-plug-ins_v1.5.1_i686-32bits.deb, which I mention in my original-post. 

Here's a screenshot of my Terminal after I installed them:
[img]http://img292.imageshack.us/img292/9396/screenshottruthseeker4xxf7.png[/img]
[/FONT][/B][/COLOR]
> **tact said:**
> Provided your desktop effects work - BIG proviso there....   all you need to do to install cairo dock is"
First install the packages libcairo2 and librsvg2-2.
```
sudo apt-get install libcairo2 librsvg2-2
```
(this bypasses the need to figure out how to install the getlibs tool)
Then install the two .deb files you already downloaded by double-clicking on the downloaded files.  (Do the dock first and plug-ins later.)
Ciao

[COLOR="Green"][B][FONT="Book Antiqua"]I also installed libcairo2 and librsvg2, as you can see below (in my 2nd screenshot of my Terminal):

[IMG]http://img134.imageshack.us/img134/8529/screenshottruthseeker4xyo2.png[/IMG]

Would any of you please tell me what I should do with to salve the problems, which I mentioned in my original-post? [/FONT][/B][/COLOR]

---

### Post by ahuman on 2008-02-25
**[COLOR="DarkRed"]I'm sorry for double-posting, so soon.  I still need to know what  I should do to get those problems solved?[/COLOR]**

---

### Post by ahuman on 2008-02-25
[SIZE="4"][FONT="Georgia"][COLOR="Purple"]My problems #1-3 were solved. I've installed all of the package/files (and libraries) that were mentioned in instructions #1-7, except for this package/file: cairo-dock-sources-20080219.tar.bz2.

I still need help solving this problem:
I don't know what to do with cairo-dock-sources-20080219.tar.bz2.

Please give me step-by-step instructions about what I should do with this package/file: cairo-dock-sources-20080219.tar.bz2[/COLOR][/FONT][/SIZE]

---

### Post by ahuman on 2008-02-25
I successfully installed those 2 .deb-files: cairo-dock-plug-ins_v1.5.1_i686-32bits.deb &  cairo-dock_v1.5.1_i686-32bits.deb, however I don't know how to properly install cairo-dock-sources-20080219.tar.bz2. 

If any of you know how to install the Cairo Dock, would you please give me step-by-step instructions about what I should do with this package/file: cairo-dock-sources-20080219.tar.bz2?

---

### Post by tact on 2008-02-25
> **ahuman said:**
> I successfully installed those 2 .deb-files: cairo-dock-plug-ins_v1.5.1_i686-32bits.deb &  cairo-dock_v1.5.1_i686-32bits.deb, however I don't know how to properly install cairo-dock-sources-20080219.tar.bz2. 

If any of you know how to install the Cairo Dock, would you please give me step-by-step instructions about what I should do with this package/file: cairo-dock-sources-20080219.tar.bz2?

There are two ways to install cairo-dock:
1.  by compiling the source yourself (needs source package and a LOT of dependencies and some skill at the art of compiling software ....   OR....

2.  use the pre-compiled binary packages (the .deb packages).  This needs less dependencies and no need to do any compiling of source.

So...  since you have installed the dependencies needed for the deb packages, and also installed the deb packages...  you are done.  You can delete the source package as I mentioned.  It is superfluous now.

The big thing is that "desktop effects" should be working or cairo-dock will not work (nor will other docks like kiba dock or AWN)....   all these docks rely on you having an (already) working "compositing window manager".   Ubuntu gutsy comes with a compositing window manager (its called compiz) but it is turned off by default.    You have to turn it on.

Hopefully your video card is supported and turning it (desktop effects, otherwise known as compiz) is as simple as clicking on System>Preferences>Appearance and going to the Visual Effects tab and enabling it.  (choose "extra" effects and the test if its working is...  no error message and menus now have ttransparency and windows are "wobbly")

Thats the relevance of turning on desktop effects...  your dock (any dock) needs that "compositing" window manager enabled.  Ok?

If you cannot enable desktop effects.... likely if your video card needs special drivers (sorry I am not up on NVidia cards needs)...  then your dock will not work.  

If desktop effects do work...  then to start the dock press "ALT-F2" and type in "cairo-dock"

Let us know how you go.

---

### Post by steveneddy on 2008-02-25
Why are there two threads on the same subject by the same person?

Please only start one thread.

Maybe mark one as solved or point one thread to the other.

Maybe a mod or admin will see this and merge the two threads.

It seems as if you are getting plenty of help, though.

Hope you get this working.

---

### Post by sayakb on 2008-02-25
A really irrelevant question wrt the topic, but is cairo-dock better than awn?

---

### Post by tact on 2008-02-25
> **ahuman said:**
> Like I mentioned above, I don't see how any of that is related to the installation of the Cairo Dock. I need advice that's relevant to my original post. I'm dealing with the instructions (1-7) 


The very first sentence in step 1 of the instruction you are following says 
"1. Your system should be capable of and running Desktop Effects"

THIS is the relevance of the instructions given to you for checking and enabling those desktop effects.

If you want to follow those instructions without skipping you need to..... do as it says... check that your system is "...capable of ***_and running_*** Desktop Effects".

I cannot give you more relevant advice than already given. 

If you cannot get desktop effects working then maybe start another thread (or use the search function) and ask for help specific to NVidia cards etc...

As mentioned...if desktop effects can be made to work just by enabling it as described a few times already - then you have completed the installation and all you need to do is press ALT-F2 and type in cairo-dock

CHeers

---

### Post by tact on 2008-02-25
> **LinuxIsInnovation said:**
> A really irrelevant question wrt the topic, but is cairo-dock better than awn?

A potentially irrelevant opinion - yes I think so.  :)

I have been using AWN for some months and it is good and often updated with new features (I still have it installed - just do not run it).  

Just for the heck of it I gave the latest cairo-dock a try a few weeks ago and like it better.  SUbjective stuff like "look and feel" seems nicer to my taste.  Some objective stuff like better stability and not needing a scripted time delay so it starts after compiz and after my desktop is also a bonus.
(On my system I have to call a script in my "startup sessions" with a 10second "sleep" in it to ensure AWN starts after desktop/compiz.   cairo-dock doesnt seem to need that - I call it directly, no script)

---

### Post by sayakb on 2008-02-25
> **tact said:**
> A potentially irrelevant opinion - yes I think so.  :)

I have been using AWN for some months and it is good and often updated with new features (I still have it installed - just do not run it).  

Just for the heck of it I gave the latest cairo-dock a try a few weeks ago and like it better.  SUbjective stuff like "look and feel" seems nicer to my taste.  Some objective stuff like better stability and not needing a scripted time delay so it starts after compiz and after my desktop is also a bonus.
(On my system I have to call a script in my "startup sessions" with a 10second "sleep" in it to ensure AWN starts after desktop/compiz.   cairo-dock doesnt seem to need that - I call it directly, no script)

Well, I'll give it a try then.. I'm kinda bored with AWN these days.. ;)

---

### Post by tact on 2008-02-25
> **LinuxIsInnovation said:**
> Well, I'll give it a try then.. I'm kinda bored with AWN these days.. ;)

Just be very aware of the two check boxes "Use New Theme's Behaviours" and "Use New Theme's Launchers" when you first install and want to run thru and just see what the different themes all look like and how they behave....

By default those boxes are not checked (a good thing when you are using it for-real) and if you change themes without checking those boxes well...  guess what...  the launchers and behaviours don't change when you change theme.   They all (themes)  seem to have same look and feel - just different colours.

If you remember to check the boxes when changing themes you get to see different behaviours as well as colours etc...

Once you settle on a theme and decide to customise it (remove launchers you dont want and add your own) etc...  Its a really cool feature to be able to change theme later and choose whether or not you also want to change beaviours ...yet still keep the launchers you have set up.

---

### Post by xamoi on 2008-02-28
Greetings!

I have the same problem here. I followed the steps on the first page (steps 1-7), I downloaded the debs and install them in order. But my problem is the dock won't start. I tried Alt+F2 then run cairo-dock, but nothing happens.

Can you guys help me please? Thank you very much!

---

