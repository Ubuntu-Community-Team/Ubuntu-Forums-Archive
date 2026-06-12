---
title: "How do I...."
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by kanati on 2007-07-22
So, I finally got Ubuntu up and running.  Now I need to know how to use this thing.  I figured I'd make this thread to ask a bunch of very basic question on how to use the OS.  These are probably going to sound stupid, but when it comes to Linux I am stupid.  

1.  I want to move my music and pictures over from my Vista partition.  Can I just copy and paste them over to my Linux partition, and if so, where should I put them?  I found a media directory but there isn't a music folder in it and I haven't figured out how to create a new directory.

2.  After installing my ATI driver whenever I click on desktop effects I get this "The Composite extension is not available".  It didn't do that before installing the video driver.

3. When I move a shortcut from the desktop to the trash am I only deleting the shortcut?

4. Where can I find more of those panel accessories (the wigety/gagety things)?

5. Anti-Virus/Anti-Spyware, do I need it?  And if so which one would you recommend? (I've always used AVG on windows)

6. Is there a way to spiff up the look of the GUI without going into beta software?

---

### Post by annda on 2007-07-22
hi!

1. the home folder is where you want to put all your files. click on the dekstop icon Home (if you have it) or go to places>home folder this will open the nautilus file manager in your directory. now you can use the right-click menu.

2. not an expert on ati, but which driver is it? how did you install it?

3. yes, if it is a shortcut.

4. right-click on the panel and you can add some things. more thingies are in gdesklets, you might want to install those (again, not a user, but you can search for gdesklets)

5. you don't need it very much, but some people use them. clam AV comes to mind.

6. [www.gnome-look.org](www.gnome-look.org) has themes and icons.

you can read this sticky thread to find out how to install applications and where useful documentation is:
[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)

---

### Post by kavon89 on 2007-07-22
> 
1. I want to move my music and pictures over from my Vista partition. Can I just copy and paste them over to my Linux partition, and if so, where should I put them? I found a media directory but there isn't a music folder in it and I haven't figured out how to create a new directory.

2. After installing my ATI driver whenever I click on desktop effects I get this "The Composite extension is not available". It didn't do that before installing the video driver.

3. When I move a shortcut from the desktop to the trash am I only deleting the shortcut?

4. Where can I find more of those panel accessories (the wigety/gagety things)?

5. Anti-Virus/Anti-Spyware, do I need it? And if so which one would you recommend? (I've always used AVG on windows)

6. Is there a way to spiff up the look of the GUI without going into beta software?

1. I'm pretty sure Vista still uses NTFS so it should be do able, I'll let someone with more experience answer that for ya. (I agree with the guy above me. keep everything inside your Home folder. Make a little Media -> Pictures, Movies, Music directory for those things. I have a Downloads folder and a Programs directory there too. Just about all I need. :D )

2. Yeah, I get that too. Blame the crappy ATI drivers. Use the standard driver with your ATI x100 series card, the restricted drivers don't help with performance and they don't like the wobbly windows etc.

3. Yes, I think Ubuntu calls them Links/Launchers. ;)

4. Browse through System -> Preferences I guess, I'm not sure. I think you will need EDIT: gdesklets for widgets, you should be able to search the Synaptic Package Manager for it, it will set it up for ya. :D

5. You really don't need it. I think AVG has a Linux version of their anti-virus, it is sort of useless in my opinion. Firewall is enabled already and in Stealth mode, viruses are hardly a threat because the administrator password is required for any system changes. Plus they are uncommon. I don't think you need spyware programs either, just clear your Cookies in Firefox once and a while, tracking cookies are just about the only threat there.

6. You can download themes. [http://art.gnome.org/themes](http://art.gnome.org/themes)  I prefer using the simple Mist theme included in Ubuntu, I'm not too concerned about a spiffy desktop unless I'm taking a screenshot to show off Ubuntu. Then I'll head into the Theme manager and switch to a nice one. ;)

To install themes, just open the Theme manager and choose Add Theme... , then point it to the .tar.gz file you probably downloaded and it will set everything up, unless specified by the author of the theme. :)

---

### Post by avik on 2007-07-22
> **kanati said:**
> So, I finally got Ubuntu up and running.  Now I need to know how to use this thing.  I figured I'd make this thread to ask a bunch of very basic question on how to use the OS.  These are probably going to sound stupid, but when it comes to Linux I am stupid.  

1.  I want to move my music and pictures over from my Vista partition.  Can I just copy and paste them over to my Linux partition, and if so, where should I put them?  I found a media directory but there isn't a music folder in it and I haven't figured out how to create a new directory.

<snip>

5. Anti-Virus/Anti-Spyware, do I need it?  And if so which one would you recommend? (I've always used AVG on windows)

6. Is there a way to spiff up the look of the GUI without going into beta software?

1. You can just copy them fro your Vista partition.  Remember, your /home/*<username>* directory is like your C:/Users/*<username>/Documents* folder.  And while Windows comes with Music, Pictures, etc. folders created, Linux doesn't.  You can create them, or not.

5.  No need.  Just make sure you have a strong password, and don't run any suspicious programs, and you'll be fine.

6. [http://art.gnome.org/]("http://art.gnome.org/") and [http://www.gnome-look.org/]("http://www.gnome-look.org/") are good for that.

---

### Post by kanati on 2007-07-22
"Use the standard driver with your ATI x100 series card"

How do I do that?  I don't remember exactly what I did to install the driver I currently have.  I found an older thread on this forum and followed the instructions there.  I copied a few lines through the command prompt (I think it was updating something).  Then I clicked on the restricted drivers option in the system>administration menu and checked the box that said ATI accelerated graphics driver.  On reboot my screen resolution went from 1024x768 to 1680x1050, which is what I wanted.  I'm not sure exactly what happened but I assumed the right driver was installed.
Strange, in the Vista world ATIs drivers are lightyears ahead of Nvidia's.


"5. No need. Just make sure you have a strong password, and don't run any suspicious programs, and you'll be fine."  

That's what I figured.  From when I first installed XP to when I upgraded to Vista a few months ago I did not have a single virus or spyware detection (with an exception to tracking cookies).  If I can manage that on Windows I should be fine here.

---

### Post by kavon89 on 2007-07-23
The standard open source default drivers allow the desktop effects. That's just about all I know. That is how it is on my system, You installed the ATI drivers, which allow more resolution probably, but they don't work with the desktop effects. 

There is probably a solution, but I think you can live without wobbly windows and the cube effect.  I say wait for the next version, Gusty Gibbon, which might fix that problem and add more effects by default.

---

