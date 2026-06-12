---
title: "Orig. 15in MBP Issues.."
date: 2007-12-23
forum: Apple Intel Users
---

### Post by benzmacx on 2007-12-23
Ok, I am very new to Ubuntu, I have been looking for something a little different.  One of my friends loves ubuntu, so I figured I would take it out for a try... Turns out to not be as easy as he said it was....

I am Running Gusty 7.1.  The initial install went fine, although I did not use bootcamp, I just reformatted to create a few partitions and am using rEFIt (don't like how apples boot manager calls my Ubuntu Winblows!)

I have a MBP 15in Core Duo 2.16GHz with 2gb of ram, 120gb drive.

Here are my problems:
 
1. Can't get the drivers to work for my ATI x1600, When I try to enable the restricted ATI drivers it tells me that It can't and I must fix the broken package first.  I have poked around about this and following directions for enabling/installing the drivers lead to the  same result.

2.  I can't listen to music!  If I open rhythembox and try to import an MP3 it throws an error - "The GStreamer plugins to decode MP3 files could not be found"
So then I tried to double click on them in the finder... err.. File Browser? and it opens them in movie player, when then tells me I need to install a few plugins, but when I try to install the last one (GStreamer extra plugins - hey that sounds familiar!) it tells me there is a compatibility error, and does not tell me with what it is incompatible.

3. Redraw isues - assume that has to do with my video driver

4. Non-native resolution - assume that has to with my video driver too

5. UI - I would like to change the UI to make it a little more mac-like.  Its a bit to windows xp for me.

6. Trackpad sensitivity - Apple has a feature that I never knew I needed so much... It will ignore accidental trackpad hits, and I apparently do it alot!  anyway Ubuntu can do this too?


Other than that it seems to work, and I am posting from Ubuntu,

Any help would be greatly appreciated!

Thanks,
Jim

---

### Post by cyberdork33 on 2007-12-23
> **benzmacx said:**
> 1. Can't get the drivers to work for my ATI x1600, When I try to enable the restricted ATI drivers it tells me that It can't and I must fix the broken package first.  I have poked around about this and following directions for enabling/installing the drivers lead to the  same result.

run this in a terminal:
```
 sudo apt-get -f install
```Hopefully that will fix it, and if not, should give some decent error messages.

> 2.  I can't listen to music!  If I open rhythembox and try to import an MP3 it throws an error - "The GStreamer plugins to decode MP3 files could not be found"
So then I tried to double click on them in the finder... err.. File Browser? and it opens them in movie player, when then tells me I need to install a few plugins, but when I try to install the last one (GStreamer extra plugins - hey that sounds familiar!) it tells me there is a compatibility error, and does not tell me with what it is incompatible.This may be related to the above. Try that first. BTW, the file browser is called 'nautilus' in default ubuntu (part of gnome), although you can change it to many different browsers if you like.

> 3. Redraw isues - assume that has to do with my video driverlikely

> 4. Non-native resolution - assume that has to with my video driver too yep

> 5. UI - I would like to change the UI to make it a little more mac-like.  Its a bit to windows xp for me.There are many different community-produced themes available.
[http://www.gnome-look.org](http://www.gnome-look.org)
Metacity and gtk themes should work for you. You can set the color scheme, theme, icons, etc in Preferences > Appearance

> 6. Trackpad sensitivity - Apple has a feature that I never knew I needed so much... It will ignore accidental trackpad hits, and I apparently do it alot!  anyway Ubuntu can do this too?There are many many option you can configure with the synaptics trackpad driver. run 'man synaptics' from a terminal to get a description of them all. There are also several variations of configurations that people have posted in the forums here that you can use. Check out the FAQ, I think there is a tutorial in there.

---

### Post by benzmacx on 2007-12-23
I was looking into the track pad thing, looks like that really wont be a problem at all.

as for the broken packages thing:

I ran sudo apt-get -f install and it returned this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Doesn't seem to answer much...
Did I start off with bad install or something?  I don't really understand why it would do this only for my Install...

Thanks for the reply!
Jim

---

### Post by DGortze380 on 2007-12-25
Were you connected to the internet during the install?  My first install on my Macbook was done while not connected and I could never get packages to install correctly after that. Re-installed while connected to the internet (hard wire, not wireless) and it was fine; then did a fresh install of Gusty a few months later and haven't had another problem with it.

---

### Post by benzmacx on 2007-12-26
Thanks, I will be very busy during the next couple days, but I will give it a try when I get some time.

---

### Post by benzmacx on 2007-12-28
> **DGortze380 said:**
> Were you connected to the internet during the install?  My first install on my Macbook was done while not connected and I could never get packages to install correctly after that. Re-installed while connected to the internet (hard wire, not wireless) and it was fine; then did a fresh install of Gusty a few months later and haven't had another problem with it.


That was it!  Connected with an Internet connection and re-installed.  The restricted ATI driver installed just fine the first time!

Thanks for the Good advise guys!
Jim

---

