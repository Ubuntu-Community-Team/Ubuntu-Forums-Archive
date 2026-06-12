---
title: "Resolution problem, I cant figure it out!"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by Bohlio on 2007-07-20
I know that there are tons of threads about resolution already, but I can seem to figure it out!
I have an ATI X300 with the FGLRX driver and am using XGL and Compiz

The highest resolution I can select is 1024X768, and I want to get 1280X1024...
Ive added the extra resolution to the xorg.conf file, logged out and back in, and have had no change.
Some threads suggest using "sudo dpkg-reconfigure xserver-xorg" but I am unsure about what this will do as I dont want to mess up any of my graphics settings, It took a while to get it to work correctly and I dont want to have to set it up all over again. All I want to do is add one more resolution to the list that I know both my card and my monitor can support.

Any help would be awsome! I'm sorry If you guys get tons of threads about this... :(

Bohlio

---

### Post by Wiebelhaus on 2007-07-20
We as a community really need to work on a solution to this, it's a huge problem for many people , maybe programming the server to select all resolutions by default , I'm sure there would be issues with that but anyway..

run this in the terminal
> sudo dpkg-reconfigure -phigh xserver-xorg
Select the resolution you want with the space bar hit tab to select ok hit enter , restart , no worries this won't screw it up.

---

### Post by bobplano on 2007-07-20
the reconfigure command just changes your xorg.conf for you. i don't know if it makes a difference but you might try restarting X instead of logging out, then back in again. the default for log off doesn't restart X so i don't think that will cut it. (btw restarting X is ctrl+alt+backspace)

---

### Post by kittyhawk63 on 2007-07-20
You need to make a backup file for xorg.conf just in case you do mess up your present settings.


Just for your peace of mind. The following will give you a copy of your xorg.conf file when you need it.

In the terminal "copy and paste" the following.

sudo cp -i /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

Hit <enter>

Sorry for the original typo.

---

### Post by kittyhawk63 on 2007-07-20
Any time you need to reinstall your "favorite" xorg.conf type the line command I gave in terminal or in recovery mode and hit <enter> The file will automatically exchanged (overwrite) the one giving you trouble. Keep it updated when you have made changes and there are absolutely "no" problems or minimal problems you can work with.
kh

---

### Post by Bohlio on 2007-07-20
> **sx66gns said:**
> We as a community really need to work on a solution to this, it's a huge problem for many people , maybe programming the server to select all resolutions by default , I'm sure there would be issues with that but anyway..

run this in the terminal

Select the resolution you want with the space bar hit tab to select ok hit enter , restart , no worries this won't screw it up.

After doing this I was allowed to pick the correct resolution in the "screen resolution" application under system>preferences.
I don't know exactly what It did, but it worked :D
Thank you very much

And KittyHawk, Thank you for the tips on backing up the settings, that will be very useful for when I inevitably mess something up 

Thanks :)
Bohlio

---

