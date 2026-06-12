---
title: "Enabling Compiz"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by wanchai on 2008-03-24
Is there any documentation anywhere that really _explains_ how to enable Compiz? :confused:

All I find with Google are forum posts where people list steps, do this, do this and do that. But no explanation is given why these steps are carried out, what the prerequisites and what the expected results are. People like me follow these steps, if they're lucky it works, if not, they have no clue why not. (If it does work, they don't have a clue either, but that doesn't seem bother anyone.)

I got Compiz working in my Gutsy install, but I don't remember how. It was a lot of trial and error, and after disabling or uninstalling something it suddenly did work. Now I booted Hardy from the CD, tried to enable it and got the nice message "Desktop effects could not be enabled". And why not?? So, back to Google. Someone said somewhere "install xserver-xgl." Tried that. Now the desktop effects work. Booted back into the Gutsy install, checked, no xserver-xgl installed there. Apparently it isn't necessary, or it's just one way out of many.

What I'd like is some documentation that allows me to understand how this stuff is supposed to work. Does that exist anywhere?

---

### Post by drs305 on 2008-03-24
> **wanchai said:**
> I got Compiz working in my Gutsy install, but I don't remember how. It was a lot of trial and error, and after disabling or uninstalling something it suddenly did work

I feel your pain and can't answer your main question. However, if Hardy is like Gutsy, ONCE you do have everything working, there is a way to back things up. In Gutsy, you use Syst, Prefs, Adv Desktop Effects, Preferences, Profile, Export and save your settings for future reference should things turn bad later. Hopefully Hardy has something similar.

Hope you get your answers.

---

### Post by brownknight on 2008-03-24
I suggest going first at the Ubuntu documentation > System > Help and Support > Customizing your Desktop > Desktop Effects.

---

### Post by wanchai on 2008-03-24
brownknight, are you referring to this [documentation]("https://help.ubuntu.com/7.10/desktop-effects/C/index.html")? That explains how to switch desktop on and off...

---

### Post by Het Irv on 2008-03-24
Sometimes (as in my case) I had to disable the compatibility check for Compiz for it to work.  The graphics driver in my laptop is blacklisted, so I told Compiz to use it anyway.  I can't remember how to do this, but I hope it will help someone get on the right track.

---

### Post by Therion on 2008-03-24
Well [this link](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) explains how to set up some of the more common Compiz settings.  And [this link](http://wiki.opencompositing.org/PluginsMain) explains what all the different plugins do.  Since many people are interested, specifically, in the animations that compiz uses (or can use) [this link](http://wiki.opencompositing.org/Plugins/Animation) explains those.  A lot of the time, figuring all this stuff out requires you to do your own research, often from several sources, and then kind of piece it all together.  Hopefully some of those links will help answer your questions.

---

### Post by kalesh7 on 2008-03-24
first of all what graphics card do you have?
are the drivers installed?

heres the steps as I did them
system->administration->resticted drivers manager
select enable for the drivers
it wants to install some software(drivers apperantly) let it do so.
install compizconfig-settings-manager and emrald with sypnatic(it will want to install a number of additional things let it)
system->preferences->advanced desktop effects settings
select the stuff you need
system->preferences->emrald theme manager 
select theme
if you don't see any changes open a terminal and enter the command
> compiz --replace
for me everytime I logout and in (or restart) the settings were disabled
so I added the command compiz --replace to system->preferences->sessions

the steps should be self explanatory but if you are stuck, need more explanation or it doesn't work post again.

---

### Post by wanchai on 2008-03-27
I suppose my big question about explanations has been answered with "no" and it's back to trial and error...

Anyhow, starting compiz from the shell (thanks kalesh7) gave me a hint because it printed error messages which prompted me to look into /usr/bin/compiz. I found that laptops with ATI cards are blocked from running compiz unless you are running closed source drivers or Xgl. After seeing that I understood what Het Irv meant, so thanks to you as well.

The problem is discussed at length in [thread 722943]("http://ubuntuforums.org/showthread.php?t=722943"). The trick described in post [#92]("http://ubuntuforums.org/showpost.php?p=4593007&postcount=92") on page 10 works fine for me (HP Compaq NC6000 laptop with ATI Mobility Radeon 9600 and Ubuntu's default driver, no xserver-xgl).

---

