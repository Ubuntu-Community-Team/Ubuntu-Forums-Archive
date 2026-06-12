---
title: "problem with themes under Hardy"
date: 2008-04-26
forum: Art &amp; Design
---

### Post by mitza on 2008-04-26
i installed the new version yesterday and today i tried some themes, the only thing that bugs me is that my icon themes don't apply everywhere, so in nautilus the icons remain the ugly (gnome default), but everywhere else the icons change. this doesn't happen only with some of the icon themes, for example noia ! what should i do? please help me  :(

---

### Post by Half-Left on 2008-04-26
It's probably due to icon theme being old and not working with the new gnome icon spec. It's just a matter of doing is manually or naming the icons the same names as the gnome icon theme or default one.

---

### Post by the8thstar on 2008-04-26
> **mitza said:**
> i installed the new version yesterday and today i tried some themes, the only thing that bugs me is that my icon themes don't apply everywhere, so in nautilus the icons remain the ugly (gnome default), but everywhere else the icons change. this doesn't happen only with some of the icon themes, for example noia ! what should i do? please help me  :(

Agreed with Half-Left. Gnome changed its ways a little bit in this new version, which means that icons developers need to update their icon packages to match.

---

### Post by mitza on 2008-04-26
thanks. i deleted in usr/share/icons/gnome the default icons and replaced them with noia... and now unfortunately i don't have icons at all... i'll just reinstall hardy

---

### Post by Half-Left on 2008-04-26
Just reinstall the gnome-icons-theme package

---

### Post by stansford on 2008-04-28
> **Half-Left said:**
> It's probably due to icon theme being old and not working with the new gnome icon spec. It's just a matter of doing is manually or naming the icons the same names as the gnome icon theme or default one.

Hi Half-left, could you be a bit more specific on what to do to fix these icons, what do you mean by "naming the icons the same names as the gnome icon theme or default one"?

thanks

---

### Post by Half-Left on 2008-04-28
> **stansford said:**
> Hi Half-left, could you be a bit more specific on what to do to fix these icons, what do you mean by "naming the icons the same names as the gnome icon theme or default one"?

thanks

Some of the icon names have changed or are in differently named folders from the icons file. Your best off looking in /usr/share/icons/gnome and looking at the index.theme and matching your broken icon theme to match that and it's directories names.

You could also email and ask the maker of the icons to update them.

---

### Post by stansford on 2008-04-28
> **Half-Left said:**
> Some of the icon names have changed or are in differently named folders from the icons file. Your best off looking in /usr/share/icons/gnome and looking at the index.theme and matching your broken icon theme to match that and it's directories names.

You could also email and ask the maker of the icons to update them.

Half-left - thanks, that's a good idea to match what is used in: /usr/share/icons/gnome. I'll have a go. 
Do you know whether it's true that GNOME 2.22 only supports .svg icons and not .png ones? 
It's just that some of the icons I want to use are .png, so if they are no longer supported, then I'd be wasting my time fiddling with the directory structures!

---

### Post by Half-Left on 2008-04-28
yes it supports .png, you just point your index.theme file to the directory.

---

### Post by mitza on 2008-04-28
i have lots of icons installed but i don't seem to find their folders in usr/share/icons.
anyhow i figured out what to do with them so that they change everywhere. you see the gnome default has some additional icon sizes like 24x24 so i figured that all i need to do is make such a folder and copy the icons from the 22x22 folder.
ps: the icons i'm trying to find are vista inspirate nuovo aero and noia so if you could help me out with  this one i'd appreciate it.

---

### Post by stansford on 2008-04-28
> **mitza said:**
> i have lots of icons installed but i don't seem to find their folders in usr/share/icons.
anyhow i figured out what to do with them so that they change everywhere. you see the gnome default has some additional icon sizes like 24x24 so i figured that all i need to do is make such a folder and copy the icons from the 22x22 folder.
ps: the icons i'm trying to find are vista inspirate nuovo aero and noia so if you could help me out with  this one i'd appreciate it.



Guys,
I've fixed this issue - at least for me.
I'll share it and see if it does the same for you:

I've done a clean Hardy install and then installed my two fav icon sets "dropline-etiquette" and CrystalforGnome-Kids.
Neither of these display the full set of icons anymore (they did in Gutsy). Some show the default Gnome grey icon set which is very annoying and so naff.

The icons I really wanted to change were the folder icons shown in Nautilus under tree view, but I guess once you get the principle right, and find out what the icons are called it will probably work for whatever icons you want to change. OK here's what I did:

1. Compare the folder structure of standard icon sets that come with Hardy as installed in /usr/share/icons/ with your favourite sets installed probably in /home/.icons/<fav icons set name>. I looked at the default set called "Gnome" and another set called "Crux" both of which work but have different structures.

You need to do this to find out what the differences are between the folder structure in the sets that work and yours that don't work.

I discovered that in the "dropline-etiquette" (art.gnome.org) set, the difference was that the default Gnome set under the folder "scalable" there was a "places" folder. My set didn't have this places folder, instead it had a "filesystems" folder.

So the first thing I did was rename the folder called "filesystems" to "places" under /home/angus/.icons/dlg-etiquette/scalable.

2. The next thing to do is edit the "index.theme" file found in /home/angus/.icons/dlg-etiquette folder and using find and replace change all occurrences of "filesystems" to "places".

3. The last thing to do is to go back to the /home/angus/.icons/dlg-etiquette/scalable/places folder and make sure there is an icon called "folder.svg" or "folder.png" depending on which type of icons your icon set uses. 

For me this last point was key. Obviously if you can find the name of the icon you want to replace then you can make sure your set has one with the right name in the right place. For me I needed an icon called "folder.svg" in the places folder.

Then reload the icon set and bingo - the old grey default folder icons in Nautilus were gone.

Now there is one other scenario worth covering and that is what to do if there is no "scalable" folder in your icon set.

My "kids" icon set was like this and that is where the "Crux" defualt theme I mentioned earlier comes in. It too has no scalable folder so if your set is like that and just has a number of folders with the different sizes of icons on eg 16x16, 32x32 etc then below each of these folders you should still find your hierarchy of folders with names like "places", "apps" etc. Again all I had to do was follow the steps above and replace the folders called "filesystems" with ones called "places". 

Unfortunately, I didn't know which sized icons were being used, so I just changed them all. It seems sense to do this, but it's more work though!

Then reload the set again and you should see the icons you want.

So there you are! Hope this works for you like it worked for me.

---

### Post by acelin on 2008-04-30
Great info!

---

### Post by prashantjois on 2008-04-30
Thanks for figuring that out stansford.  Here's a quick script to automate that.  Go to your icon theme folder (e.g. /home/angus/.icons/dlg-etiquette) and run the following:

```

find . -name "filesystems" | sed s'/\(.*\)\/filesystems/mv \1\/filesystems \1\/places/' > tmp; sh tmp; rm tmp

sed index.theme -i -e s'/filesystems/places/'

find . -name "**FOLDER ICON NAME**" | sed s'/\(.*\)**FOLDER ICON NAME**/cp & \1folder.png/' > tmp; sh tmp; rm tmp


```


in the last command, change **FOLDER ICON NAME** to the filename of the folder icon, e.g. gnome-fs-directory.png

---

### Post by stansford on 2008-04-30
> **prashantjois said:**
> Thanks for figuring that out stansford.  Here's a quick script to automate that.  Go to your icon theme folder (e.g. /home/angus/.icons/dlg-etiquette) and run the following:

```

find . -name "filesystems" | sed s'/\(.*\)\/filesystems/mv \1\/filesystems \1\/places/' > tmp; sh tmp; rm tmp

sed index.theme -i -e s'/filesystems/places/'

find . -name "**FOLDER ICON NAME**" | sed s'/\(.*\)**FOLDER ICON NAME**/cp & \1folder.png/' > tmp; sh tmp; rm tmp


```


in the last command, change **FOLDER ICON NAME** to the filename of the folder icon, e.g. gnome-fs-directory.png

prashantjois - thanks for the script and no problem. I'm glad I could help. I've had so much help in the past from others. It's what the forums are all about isn't it?

---

### Post by mitza on 2008-04-30
thanks guys, you've been a great help... i love ubuntu and it's comunity !!!:guitar: .... i just realized that i don't know how to use the script :( so i made it manually (the theme to work that is). could you please help me getting a script to run.

---

