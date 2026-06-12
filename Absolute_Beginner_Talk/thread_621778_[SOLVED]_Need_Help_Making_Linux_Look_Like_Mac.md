---
title: "[SOLVED] Need Help Making Linux Look Like Mac"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2007-11-20
Ok so i've seen alot of videos on you tube where the linux's have mac like tool bars. how do i get that? i'm pretty sure i use the widget bar in compiz?

---

### Post by Paul820 on 2007-11-20
Do you mean this? [http://wiki.awn-project.org/index.php?title=Main_Page]("http://wiki.awn-project.org/index.php?title=Main_Page")
If so you can get a .deb file from here [http://www.getdeb.net/]("http://www.getdeb.net/")

---

### Post by RadiationHazard on 2007-11-20
Yes sir! That's what i want. Now i'm new to linux. like one day new. haha. can you step by step me through what to do?

---

### Post by DutyDuty on 2007-11-20
Click his/her (who am I kidding. His.) second link. Download. Open file. Follow instructions on screen. .deb files are usually easy to install.

---

### Post by santiagoward2000 on 2007-11-20
There's [kiba-dock]("http://www.kiba-dock.org") too. It has a really cool physics engine!
Here's a video:
[http://youtube.com/watch?v=VekgyKQoTeM]("http://youtube.com/watch?v=VekgyKQoTeM")

---

### Post by RadiationHazard on 2007-11-20
alright thanks guys! both seem really nice. could i ask you to give me the direct download like please?

---

### Post by Paul820 on 2007-11-20
What are you using? Feisty/gutsy 32bit/64bit?

---

### Post by santiagoward2000 on 2007-11-20
> **RadiationHazard said:**
> alright thanks guys! both seem really nice. could i ask you to give me the direct download like please?

About Kiba-Dock, there is no file, you'll have to compile it yourself. Here's a really good guide to do it:
[http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba]("http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba")

---

### Post by RadiationHazard on 2007-11-20
gusy 32bit

---

### Post by Paul820 on 2007-11-20
Second one on the list [http://www.getdeb.net/category.php?id=11]("http://www.getdeb.net/category.php?id=11")

---

### Post by RadiationHazard on 2007-11-20
ok. sorry i'm such a noob. but i have it installed. now what do i do man? do i do something in the widget bar thing?

---

### Post by Paul820 on 2007-11-20
You can drag icons from your menu and put them on it. You can change the way it looks by going to System->Preferences->Awn Manager and tweak it to you liking.

---

### Post by RadiationHazard on 2007-11-20
no. like how do i even make it show up on my desk top? by the way. thanks for all the help man!

---

### Post by Paul820 on 2007-11-20
Go to Applications->Accessories->Avant Window Navigator and click it to start.

---

### Post by RadiationHazard on 2007-11-20
alright thanks man i got it now! =D

---

### Post by Paul820 on 2007-11-20
No problem. Just one more thing though, if you want it to start when you boot your sytem go to System->Preferences->Sessions and make a new entry for it. Click on the **add** button, just call it AWN and for the command put **avant-window-navigator**. :)

---

### Post by RadiationHazard on 2007-11-20
k thanks buddy!

---

### Post by RadiationHazard on 2007-11-20
waittt!! i have another question!!!! how do change where i ant it?? =\\\\\\\\

---

### Post by Paul820 on 2007-11-20
You can't, it can only go at the bottom in the middle. :(

---

### Post by RadiationHazard on 2007-11-23
I'm using compiz right now. And I'm in love with all my effects like when i close and minimize pages and i love the cube and all that jazz. But is there anyway i can make my desktop look like a make and stuff but still keep all my effects?? =\ I was just wondering...

---

### Post by Partyboi2 on 2007-11-23
You probably be looking for something like awn
[http://wiki.awn-project.org/index.php?title=Main_Page](http://wiki.awn-project.org/index.php?title=Main_Page)
[http://thelinuxmovement.blogspot.com/2007/07/make-awn-look-like-mac-leopard-dock.html](http://thelinuxmovement.blogspot.com/2007/07/make-awn-look-like-mac-leopard-dock.html)

---

### Post by stefanza on 2007-11-23
Two excellent guides can be found at:

[http://www.taimila.com/?q=node/11](http://www.taimila.com/?q=node/11)
[http://camman3d.com/blog/?p=39](http://camman3d.com/blog/?p=39)

My desktop now looks like this:

---

### Post by RadiationHazard on 2007-11-23
ok that's what i want it too look like. but before i start. i'll still have all the effects i have now right??

---

### Post by Partyboi2 on 2007-11-23
Yes, you will still have all the bells and whistle that come with compiz

---

### Post by RadiationHazard on 2007-11-24
look at the screen shot. first look at the left firefox windos then look inside the right firefox window. why aren't the little red yellow and green dots on the windows like they should be it still has the linux title bars instead of the mac one.......:confused:

---

### Post by alwiap on 2007-11-24
> **RadiationHazard said:**
> look at the screen shot. first look at the left firefox windos then look inside the right firefox window. why aren't the little red yellow and green dots on the windows like they should be it still has the linux title bars instead of the mac one.......:confused:

no screenshot to look at!  wheres it!  :D

---

### Post by RadiationHazard on 2007-11-24
> **alwiap said:**
> no screenshot to look at!  wheres it!  :D

sorry. haha i forgot =P

---

### Post by FuturePilot on 2007-11-24
Looks like you're using Emerald. Try
```
gtk-window-decorator --replace
```

---

### Post by RadiationHazard on 2007-11-24
ok that worked amazing!! but once i close the terminal it starts messing all up until i do it again??

---

### Post by FuturePilot on 2007-11-24
Try it from Alt+F2
If you would like to use the gtk-window-decorator by default instead of Emerald just do this```
gedit .config/compiz/compiz-manager
```
Put this in the file
```
USE_EMERALD="no"
```
Next time you start Compiz it should still use the gtk-window-decorator.

---

### Post by RadiationHazard on 2007-11-24
it worked :) thank you very much friend!! :):):)

---

### Post by FuturePilot on 2007-11-24
No problem :)

---

### Post by RadiationHazard on 2007-11-24
alright if you go too [http://www.taimila.com/?q=node/11]("http://www.taimila.com/?q=node/11") and you go about 1/3 way down to where it says Boot Screen and then you go about halfway down the page to where it says Login Screen how do i do those? i've donw pretty much everything but that. and how do i change the Ubuntu icon in the top left hand corner to an Apple Icon? (look at screen shot)

---

### Post by stinger30au on 2007-11-24
whatever floats your boat i guess

---

### Post by ronmarley1 on 2007-11-24
Alternatively, if you would like to continue using Emerald, there are many Mac Emerald themes to be found at [http://www.gnome-look.org/](http://www.gnome-look.org/).  Look under Beryl for Emerald themes.
In fact, there are even some Leopard themes at [http://www.gnome-look.org/index.php?xsortmode=alpha&xcontentmode=103&page=17](http://www.gnome-look.org/index.php?xsortmode=alpha&xcontentmode=103&page=17)

---

