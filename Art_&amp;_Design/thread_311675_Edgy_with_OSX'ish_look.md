---
title: "Edgy with OSX'ish look"
date: 2006-12-03
forum: Art &amp; Design
---

### Post by macewan on 2006-12-03
Not sure where to post this, but this was the closest I could find.

---

### Post by jhaitas on 2006-12-03
what package do i install to get the Dock there at the bottom

---

### Post by pay on 2006-12-03
Everyone dresses their Linux systems up as OS X. Linux really needs it's own distinguishable look. The screenshot looks good though.

---

### Post by noneofthem on 2006-12-03
If you wanna get a more acurate MacOS-look try this link:

[http://www.taimila.com/ubuntuosx.php](http://www.taimila.com/ubuntuosx.php)

Cheers

Amir

---

### Post by PurplePenguin on 2006-12-03
You get the dock with gdesklets.

Who cares if people dress their system up as OSX?  If they like the look, they're free to do it.  If they don't like the look, they are free to make it look like something else.  That's the good thing about linux... nobody's trapped into a uniform style. :)

---

### Post by noneofthem on 2006-12-03
Yeah! That's right!

And it is free! Not like the themes you can get for M$ Windows where you have to purchase a 3rd party software in order to change the look.

---

### Post by macewan on 2006-12-03
> **jhaitas said:**
> what package do i install to get the Dock there at the bottom

that is kiba-dock

---

### Post by macewan on 2006-12-03
> **pay said:**
> Everyone dresses their Linux systems up as OS X. Linux really needs it's own distinguishable look. The screenshot looks good though.

For me it's the journey not so much the finished product. It's fun to experiment with what does and does not work. Screwing up and having to fix it so that you're able to help with suggestions for others that are trying the same thing. With Windows and OSX there isn't as much freedom without having to pay.

This was fun without spending a dime.

---

### Post by pay on 2006-12-03
> **pay said:**
> Everyone dresses their Linux systems up as OS X. Linux really needs it's own distinguishable look. The screenshot looks good though.

What I meant was the OS-X is pretty, and that is why people skin Linux to look like it. What I believe though is Gnome and KDE should be made so that they are pretty and then people on other operating systems might skin their's to look like a Linux desktop, or use Linux and ditch their operating system.

---

### Post by PurplePenguin on 2006-12-03
> **pay said:**
> What I meant was the OS-X is pretty, and that is why people skin Linux to look like it. What I believe though is Gnome and KDE should be made so that they are pretty and then people on other operating systems might skin their's to look like a Linux desktop, or use Linux and ditch their operating system.

Ah, yes, now I see what you're talking about.  I agree to that (although it seems as if the hardcore linux guys like their minimalism - blackbox and so on).  

Maybe the spinning desktop from XGL/Compiz and stuff like that will make people jealous. :)  I actually can't wait to see what the next generations of 3D desktops will be like! :KS 

By the way, I think we used the same Tux for our avatars... yours looks better, though! #-o

---

### Post by atoponce on 2006-12-03
> **pay said:**
> Everyone dresses their Linux systems up as OS X. Linux really needs it's own distinguishable look. The screenshot looks good though.

We DO have our own distinguishable look.  Gnome, KDE, XFCE, Fluxbox and Window Maker just to name a few.  We have several distinguishable looks.

---

### Post by jhaitas on 2006-12-03
is kiba-dock the package name? i couldn't find it in the repos

---

### Post by Rodneyck on 2006-12-03
Scan the forums for it, there is a how-to. I hear it's a b*tch to set up. Good luck.

---

### Post by PurplePenguin on 2006-12-03
As I mentioned before, you can get this kind of taskbar in gdesklets.  It's a Mac-style icon bar at the bottom of your screen (or wherever you want to put it) and the icons zoom larger when you put the mouse cursor over it.

Gdesklets is quite easy to install.  I think it is one of the packages in Automatix 2.  If not, I just installed it via Synaptic (but I'm about 80% sure it was through Automatix).  Gdesklets also lets you put different kinds of applets onto your desktop, showing you CPU usage and whatnot.

---

### Post by graabein on 2006-12-04
I like the wallpaper. Can you post a link to it please?

---

### Post by HanZo on 2006-12-04
I never understood what people find so interesting about the osx look... it sure is a lot better than XP-luna... but it still is kind of kitch. Personally I think ubuntu with the standard theme looks great!
Anyway, the good thing about tiger is that the interface is really clean, polished, and usable. none of the osx-like themes for linux or win I've seen until now deliver that. they all look like a cheap copy of the negative aspects of the acqua style, but miss the actual strong points.

---

### Post by keeb on 2006-12-04
Edgy / Xgl / Beryl using a Metacity'esque theme:

[http://nick.stinemates.org/desktop.png](http://nick.stinemates.org/desktop.png)

---

### Post by PurplePenguin on 2006-12-04
> **keeb said:**
> Edgy / Xgl / Beryl using a Metacity'esque theme:

[http://nick.stinemates.org/desktop.png](http://nick.stinemates.org/desktop.png)

That is _awesome_!  What a nice, clean look! :KS

---

### Post by macewan on 2006-12-04
> **graabein said:**
> I like the wallpaper. Can you post a link to it please?

Sure, here it is.

---

### Post by macewan on 2006-12-04
I've noticed that others have been searching around for how to change their Applications icon which is usually found in the upper left corner of your screen.

Found that if you copy an image to 22/places it tends to work. Image should be 22x22 and needs to be named start-here.png to work.

The attached image is an example of an image to use. I've, according to some of the comments, be fairly brutal in my attempt at changing a copy of Tango icon theme to display an OSX flavored desktop. I used Tux in place of the Apple icon to show my respect to my Linux homies, yo. The icon attached is called start-here.png. My icon theme is located in ~/.icons/TangOSX. To copy the attached image to the icon theme so that it replaces the standard Ubuntu logo I did this from a terminal:

macewan@moc:~$ ls
start-here.png

macewan@moc:~$ cp start-here.png .icons/TangOSX/22x22/places

Now either do:

macewan@moc:~$ killall gnome-panel

or change to another theme and back to TangOSX.

---

### Post by macewan on 2006-12-04
> **PurplePenguin said:**
> As I mentioned before, you can get this kind of taskbar in gdesklets.  It's a Mac-style icon bar at the bottom of your screen (or wherever you want to put it) and the icons zoom larger when you put the mouse cursor over it.

But gdesklets icons can't be made to bounce around, spin in place or other crazyness like kiba-dock.

Attached is a .deb of kiba-dock to install do this:

sudo dpkg -i kiba-dock_0.1-1.2_i386.deb

I've attached a copy for you.

Use it with xcompmgr or beryl so that their transparent - minus the back backgrounds.

cheers

---

### Post by graabein on 2006-12-05
Thanks for the background and the Tux tip. I prefer having Tux to both the Ubuntu logo and the Tango feet. Maybe I like the GNOME foot best though. It sure as **** beats the apple! 

:shock:

---

### Post by macewan on 2006-12-06
back with Ubuntu logo & theme - the Apple experiment was done just to see if I could

hopefully it might help some else that's giving it a try

> **graabein said:**
> Thanks for the background and the Tux tip. I prefer having Tux to both the Ubuntu logo and the Tango feet. Maybe I like the GNOME foot best though. It sure as **** beats the apple! 

:shock:

---

### Post by ajeetraj on 2006-12-07
> **macewan said:**
> But gdesklets icons can't be made to bounce around, spin in place or other crazyness like kiba-dock.

Attached is a .deb of kiba-dock to install do this:

sudo dpkg -i kiba-dock_0.1-1.2_i386.deb

I've attached a copy for you.

Use it with xcompmgr or beryl so that their transparent - minus the back backgrounds.

cheers


I just installed the file you put there, but what to do after that? I mean i see this blue stuff on this black background....can you please help me with the configuration? Thank you so much in advance :)](*,)

---

### Post by macewan on 2006-12-07
> **ajeetraj said:**
> I just installed the file you put there, but what to do after that? I mean i see this blue stuff on this black background....can you please help me with the configuration? Thank you so much in advance :)](*,)

[SIZE=5]sudo apt-get install xcompmgr[/SIZE]

then

[SIZE=5]xcompmgr[/SIZE]


after it's installed the icons on the kiba-dock will be transparent

---

### Post by ajeetraj on 2006-12-07
> **macewan said:**
> [SIZE=5]sudo apt-get install xcompmgr[/SIZE]

then

[SIZE=5]xcompmgr[/SIZE]


after it's installed the icons on the kiba-dock will be transparent

I did that as well, but still the same blue icon. is there any link where there is step by step configuration guide available? i am new to ubuntu btw, just to let you know :( please help me out...i have spent the whole day looking for this dock to work and your idea seems promising :) please help!

thanks for your quick response :)

---

### Post by happy-and-lost on 2007-01-06
> **noneofthem said:**
> And it is free! Not like the themes you can get for M$ Windows where you have to purchase a 3rd party software in order to change the look.

It's easy. Just patch your uxtheme.dll, find a cool theme on dA and install the Tango Icon patcher ;)

---

### Post by Ptero-4 on 2007-02-17
Hi macewan. I have kiba-dock installed and wanted to know something. I got the launchers set to the 64x64 size and noticed that the dock is small and doesn`t cover the icons, How did you do to make it cover the icons entirelly?

---

