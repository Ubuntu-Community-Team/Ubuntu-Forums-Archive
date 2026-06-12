---
title: "Changing Application Menu Icon"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by ssharps711 on 2008-03-17
Running Gutsy.

I'd like to change that Ubuntu icon, you know the one to the top left of your default Gutsy UI. 

Also, whenever I try to replace anything in /usr/share/icons/hicolor/48x48/apps, I get an error.
"You do not have permissions to write to this folder."

huh?

---

### Post by sayakb on 2008-03-17
Start terminal and type

```
gksudo nautilus
```

Go to /usr/share/icons and then to your active icon theme folder. There either under 22x22 or 24x24, find the icon "start_here.png" and replace it with whatever you like.

---

### Post by ssharps711 on 2008-03-17
Didn't work. 

Why is this so difficult?

---

### Post by ssharps711 on 2008-03-17
There is no start-here.png in my active icon folder... It's just icons.

---

### Post by ssharps711 on 2008-03-17
Bump.

Anyone know how to do this?

---

### Post by munkyeetr on 2008-03-17
I have experimented around with the icons found in /usr/share/icons/<theme>/<size>/places

There is a start-here.png, but when I tried to change it the change didn't happen. I even rebooted each time. I also tried several different <size> folders.

I am stumped, and adding to the bump.

---

### Post by Lord Illidan on 2008-03-17
[http://www.teamteabag.com/2008/03/13/howto-change-the-application-menu-icon-in-linux/](http://www.teamteabag.com/2008/03/13/howto-change-the-application-menu-icon-in-linux/)

---

### Post by Ardrias on 2008-03-17
Not having tried this myself, I'd assume it's the .svg ones, not the png. They are located in ```
/usr/share/icons/*Theme*/scalable/places/start-here.svg
```.

---

### Post by munkyeetr on 2008-03-18
> **Lord Illidan said:**
> [http://www.teamteabag.com/2008/03/13/howto-change-the-application-menu-icon-in-linux/](http://www.teamteabag.com/2008/03/13/howto-change-the-application-menu-icon-in-linux/)

I followed the instructions in this guide and it did not work for me. Not only did I change the start-here.svg file in my current icon theme, i changed it in *every* theme on my computer. I also rebooted in case that was an issue. No dice. I used the file /usr/share/pixmaps/gnome-logo-white.svg

Has anyone had this procedure work/not work on Gutsy?

Are there any issues (however slight) that may cause this to not work.

---

### Post by ssharps711 on 2008-03-18
This is pretty crazy. Should I move this post elsewhere?

---

### Post by munkyeetr on 2008-03-18
> **ssharps711 said:**
> This is pretty crazy. Should I move this post elsewhere?

Are you still trying to get it to work also?

---

### Post by Miller12 on 2008-03-18
I pretty sure you need to use

```

gconf-editor
``` in the terminal

This is taken from TheRob on gnome-look:

Set the custom menu graphic, you need to open the Configuration Editor under the "System Tools" menu - or for you hardcore types, "gconf-editor" at the command line. Go to apps->panel->objects and you'll see a series of object_x subitems. Click through them until you find the one where the value for "object_type" is "menu-object". Check the "use_custom_icon" option and then set the "custom_icon" value to the path to your custom button graphic, i.e. "/home/username/Pictures/menu.png". The graphic should update immediately.

---

### Post by ssharps711 on 2008-03-18
Nah, no go on that one either. I am doing everything correctly and it's just not working. 

Does anyone have experience with this actually working?

---

### Post by munkyeetr on 2008-03-18
This is insane...I just tried the above instructions using the gconf-editor and it still doesn't work.  There were two sections in gconf-editor that looked promising:

**apps -> panel -> objects -> menu_bar_screen0**

and

**apps -> panel -> default_setup -> objects -> menu_bar**

both of which had a checkbox setting to **use_custom_icon** and a string setting **custom_icon** (in which I put the path to the svg file)

(*NOTE: There was nothing under any of the **object_x** keys that mentioned "menu" or "menu-object"*)

As I said above, these did not work. I have toggled other settings in these sections and seen them take effect immediately, but even after a reboot, the icon does not change.

I am wondering if there is another preliminary setting that needs to be changed before this change can be made?

Arrrggh!

---

### Post by SmellyGeekBoy on 2008-03-19
Hey, I guess I should chip in as I wrote the guide at teamteabag.com, and obviously I want to know if people are having problems with it so I can amend it! I wrote the guide as I did it, using Hardy Alpha 6, and as it happens, I had to use it again when an update broke my Ubuntu install completely (Alpha FTW!) so I followed my own guide and all went well. Anyway, I think in Gutsy a different file from that same directory was used, possibly the distributor-icon.svg file. Unfortunatley I don't have a running copy of Gutsy anymore to try it out.

Anyway if anything is unclear at all or if it just plain doesn't work let me know, I'm willing to help out a fellow Ubuntu user!

---

### Post by munkyeetr on 2008-03-19
There is a distributor-logo.svg, but it is a symbolic link to start-here.svg

Also I have searched through every subfolder of /usr/share/icons and I don't have a single .svg file of the Ubuntu logo. I've changed them all to the one I want. Odd.

I am really curious why this doesn't work in Gutsy? I am sure these methods work for the people who posted them on whatever version they used - they all appear like they *should* work - but for some reason it is a no go in Gutsy, at least for me.

Any more suggestions floating around out there? And again, has anyone using Gusty gotten these methods to work?

---

### Post by sayakb on 2008-03-19
@ssharps711

Open /usr/share/icons/active icon folder/24x24/places

If you do not find any "start-here.png", then copy the image you wish to apply as the menu icon, but make sure it is scaled to 24x24. If an image exists, then replace the image with the new one.

---

### Post by sayakb on 2008-03-19
> **munkyeetr said:**
> There is a distributor-logo.svg, but it is a symbolic link to start-here.svg

Also I have searched through every subfolder of /usr/share/icons and I don't have a single .svg file of the Ubuntu logo. I've changed them all to the one I want. Odd.

I am really curious why this doesn't work in Gutsy? I am sure these methods work for the people who posted them on whatever version they used - they all appear like they *should* work - but for some reason it is a no go in Gutsy, at least for me.

Any more suggestions floating around out there? And again, has anyone using Gusty gotten these methods to work?

Well, try my last post. I changed my menu icon like that (I made my own Icon theme: a mix of Nuovo + OSX + Vista Aero + Antares icons)

---

### Post by sayakb on 2008-03-19
Plus, check this out:
/usr/share/icons/gnome/24x24/places

You would find the default start-here.png image here.

---

### Post by munkyeetr on 2008-03-19
I tried replacing both /usr/share/icons/active icon folder/24x24/places and
/usr/share/icons/gnome/24x24/places with a 24x24 copy of the .png image I want.

Still no change. I have run killall gnome-panel after each try, logged out and back in, rebooted. I then used the gconf-editor method and pointed to the new 24x24 png image. Nada.

I'm starting to think it's not such a big deal to get this to work.](*,)

But I'm now obsessed!

---

### Post by FreewareFan on 2008-03-19
It's not just you.....  I've been folowing this thread from the start, and doing everything suggested..  No dice here, either.

I'll continue to follow this thread, to the bitter end... or the happy end, whichever happens first...  lol

---

### Post by munkyeetr on 2008-03-19
> **FreewareFan said:**
> It's not just you.....  I've been folowing this thread from the start, and doing everything suggested..  No dice here, either.

I'll continue to follow this thread, to the bitter end... or the happy end, whichever happens first...  lol

LOL, rock on! :guitar:

---

### Post by munkyeetr on 2008-03-20
Okay, so I changed my icon theme to CrashBit (which has a gnome logo for the start-here.png file) and my Application menu icon changed when I changed themes.

I am going to play around a little more and see if I can find out more about why it wouldn't let me change it before.

---

### Post by FreewareFan on 2008-03-20
Good.  Sounds like you're making progress.  Let us know what you find out, yes?

---

### Post by Sugi on 2008-03-20
This may or may not help and hopefully this is something new.

Terminal
$ gksudo nautilus
(opens up the GUI folder manager with the power of the super user)
-than search for /usr/share/icons/human/22x22/places
(or any size IE 24x24 32x32, depending on what size your panel is. default is 22x22)
-make your own custom start menu, label it "start-here.png".
-BACK UP /usr/share/icons/Human/22x22/places/
Somewhere else
(back up whatever size folder you are tweaking)
- click and drag the "start-here.ong to the location and press ok for replacing the ico

Now, add a new button to your panel
Right Click on Panel
Add to Panel
Scoll down to Utilities
Main Menu
Add
(This allows you to see if your changes worked or not.)

Tips:  Make sure you know what size your panel is.  Default is 22x22.  So, if you have the default size for the panel.  Make sure you only change /usr/share/icons/human/22x22/place

I had to use the scalable folder for a panel that was 32x32.

Good luck,
Sugi

---

### Post by sayakb on 2008-03-20
> **munkyeetr said:**
> Okay, so I changed my icon theme to CrashBit (which has a gnome logo for the start-here.png file) and my Application menu icon changed when I changed themes.

I am going to play around a little more and see if I can find out more about why it wouldn't let me change it before.


Goto the System->Preferences->Appearance->Customize->Icon
Then click on some other icon theme and then click on the previous theme of which you wanted to change the icon of. Idon't know why it isn't working for you. I checked and rechecked an hour ago and this was working really fine for me.

Oh yes, also, do this to your icon theme:

```
sudo bash
chmod +w  /usr/share/icons/themename/24x24/places/start-here.png
```

---

### Post by munkyeetr on 2008-03-20
Okay, I have found that it works for me with any icon theme that I download, but not with any of the defaults (Crux, Gnome, HiConstrast, Human, Mist, Tangerine) Every other theme I download from gnome-look.org, I copy in my custom 24x24 start-here.png file into the places folder and it changes.

I have been using a Custom Theme with the Human iconset.

---

### Post by SmellyGeekBoy on 2008-03-20
How strange, so Gnome is only using the SVG icons for odd-sized panels? (and the default apparently, I had mine set to whatever the default is and mine uses the scalable icon.)

We will get to the bottom of this!

Oh, silly question, but you are killing your gnome panel and letting it restart each time, aren't you?

```
killall gnome-panel
```

in a Terminal.

---

### Post by munkyeetr on 2008-03-20
> **SmellyGeekBoy said:**
> Oh, silly question, but you are killing your gnome panel and letting it restart each time, aren't you?


Yes, I am.

---

### Post by munkyeetr on 2008-03-20
> **SmellyGeekBoy said:**
> How strange, so Gnome is only using the SVG icons for odd-sized panels? (and the default apparently, I had mine set to whatever the default is and mine uses the scalable icon.)
.

I don't know if this is true (and I may be misunderstanding your theory). I changed my icon theme back to Human and in that theme I have the .svg files changed. I resized my panel +1, then tested from sizes 24 to 30 and it didn't change. At 29 the gnome-panel app wouldn't restart and I had to reboot (for lack of a better way to recover).

**Also, just for the record, the icon change works fine (for me) with any theme other than the ones installed with Ubuntu by default.**

---

### Post by sayakb on 2008-03-22
> **munkyeetr said:**
> Yes, I am.

Instead of killing the panel, drag it to make it vertical on the left edge of the screen, and then drag it back to it's original position. This sounds weird but it works.. :)

---

### Post by munkyeetr on 2008-03-22
> **LinuxIsInnovation said:**
> Instead of killing the panel, drag it to make it vertical on the left edge of the screen, and then drag it back to it's original position. This sounds weird but it works.. :)

Is that just sort of a "lazy-man's" killall gnome-panel?

---

