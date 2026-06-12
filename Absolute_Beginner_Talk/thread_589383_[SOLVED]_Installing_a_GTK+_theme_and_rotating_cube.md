---
title: "[SOLVED] Installing a GTK+ theme and rotating cube problem"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by ohmycar on 2007-10-24
Hi everyone, I just installed 6.10 and so far it is amazing. I want to install a particular theme on deviantArt I saw. This one:

[http://lokheed.deviantart.com/art/Graphite-Suite-2-0-28688856](http://lokheed.deviantart.com/art/Graphite-Suite-2-0-28688856)

How would I install that theme because when I download it, it downloads a .zip and I could not install it from the "Appearance" menu.

Also, I enabled the desktop cube, except when I hold down Ctrl+Alt and hold down my mouse to move the cube or press <-- or --> , it is not really a cube, its more like a page that flips over and i noticed it stays in the same desktop. Does anyone know how to make it an actual cube or has encountered this problem?

Thanks,
Ash

---

### Post by kaboodle_fish on 2007-10-24
In the Desktop Size tab of the General Options setting within the CompizConfig Settings Manager, increase the Horizontal Virtual Size to 4 and that will give you a cube

---

### Post by derred on 2007-10-24
The cube option is not enabled by default. instead Ubuntu uses something called Desktop Plane
You will need to install the CompizConfig Settings Manager. To do so open a terminal window and type in: "sudo apt-get install compizconfig-settings-manager" without hte quotes :) You may need to confirm the install (press Y if it askes for it) 
After that's installed go to it in System/Preferences/Advanced Desktop Effects Settings
Under Desktop enable "Desktop Cube" and "Rotate Cube" it will ask you to disable "Desktop Plane", agree again.
That's it

---

### Post by Caffeine_Junky on 2007-10-24
> **derred said:**
> The cube option is not enabled by default. instead Ubuntu uses something called Desktop Plane
You will need to install the CompizConfig Settings Manager. To do so open a terminal window and type in: "sudo apt-get install compizconfig-settings-manager" without hte quotes :) You may need to confirm the install (press Y if it askes for it) 
After that's installed go to it in System/Preferences/Advanced Desktop Effects Settings
Under Desktop enable "Desktop Cube" and "Rotate Cube" it will ask you to disable "Desktop Plane", agree again.
That's it

and don't forget to Perform this step as well:

> In the Desktop Size tab of the General Options setting within the CompizConfig Settings Manager, increase the Horizontal Virtual Size to 4 and that will give you a cube   Because you need 4 "work spaces" (bottom bar right-hand side by default) to make a cube.

---

### Post by ohmycar on 2007-10-24
Ah , thank you for the help. It now is a cube! :)

Anyone have any idea about the theme?

---

### Post by Caffeine_Junky on 2007-10-24
Ok, I found a way to convert your theme to .tar.bz2 format (because the theme installer in Ubuntu would not install .zip)

BTW, I am using Ubuntu 7.10, I am not sure which version you are using as your original post says "6.10"  ...typo?

>  Artist's Comments
A graphical suite for the GNOME desktop environment. This suite requires several outside components. GTK-Engines-2.7.3 or higher must be installed to meet the Clearlooks/Cairo dependencies. The gperfection icon set must also be installed as the graphite icon theme is merely an expansion.

So, first install the following from Synaptic Package Manager.  Search synaptic for **gperfection** and install both packages that the search finds (they should be the only items in the window anyway)

Now go to the following site: Link >   [http://www.zamzar.com/](http://www.zamzar.com/)

Follow the instructions there to convert your .zip theme file to .tar.bz2
..they will send you an email with instructions on where to download the converted file.

Once you have your converted file simply install it by opening: System > Preferences > Appearance >Theme,  click "Install" and browse to your "new theme file.tar.bz2" and select it, ...  then click the "Customize" tab and set up your theme...

There may be another way to convert that .zip file to .tar.bz2, but this is what I found when doing a Google Search. (it was my first time at doing something like this and I was successful YAY :p )

Best of luck :)

PS:  I uploaded the converted file (lol took me a while to think of it)

---

### Post by ohmycar on 2007-10-24
Wow, you are AWESOME! haha, yeah it was a typo, I meant 7.10. Thank you so much for helping me out with that. ahh This theme is so slick!!!!!! Thank you thank you thank you! lol:biggrin:=D>

btw: I noticed your home folder was called ash? My name is Ash and my home folder is called ash. CRAZY?!...

---

### Post by Caffeine_Junky on 2007-10-24
Cool,  no problem!   heh yeah I just noticed that you signed your original post "Ash" lol spooky :)

As you are the starter of the thread you will have an option to mark the thread **[solved]** , ..so if you have no further questions on this topic it would be a great help to others if you could do that...

Glad I could help, ..enjoy your new theme...

cheers

---

