---
title: "Menu item for Realaudio appears in wrong catagory (graphics) after synaptic install."
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by LostInSwiss on 2006-07-11
I installed Realplayer 10 using synaptic install.

Method: I did some messing with the synaptic package manager reposotories see:  How to apt-get the easy way (Synaptic)
[http://ubuntuguide.org/wiki/Dapper#How_to_apt-get_the_easy_way_.28Synaptic.29](http://ubuntuguide.org/wiki/Dapper#How_to_apt-get_the_easy_way_.28Synaptic.29)

Had to do some updates and had an issue with a missing dependancy (also fixed using synaptic package manager). Firefox plugins work and am listeng to the world service as I type.

However...
The shortcut to RealPlayer 10 appears under Applications>Graphics>
I added it again to Applications>Sound and Vidio> using 'Alacarte Menu Editor' but the delete option is greyed out under the Graphics catagory.

I have scanned through: [http://www.gnome.org/start/2.0/menuediting.html](http://www.gnome.org/start/2.0/menuediting.html)
but 1 dont fully understand things. 
Extract from my user applications.menu file:

<Menu>
<Name>Graphics</Name>
<AppDir>/home/lostinswiss/.local/share/applications</AppDir>
</Menu>

Looks to me like AppDir is under the wrong menu however editing this does nothing.

Could somone tell me how to fix this please.

Also
I tried and tried to install Realplayer manualy but could not figure out where to install (not on desktop) it or how to get firefox plugins working with it. In the end I used synaptic (as described). If somone can tell me a nice method of installing manualy would apreciate it.

p.s. sorry about the spelling

---

### Post by Kilz on 2006-07-11
> **LostInSwiss said:**
> I installed Realplayer 10 using synaptic install.

Method: I did some messing with the synaptic package manager reposotories see:  How to apt-get the easy way (Synaptic)
[http://ubuntuguide.org/wiki/Dapper#How_to_apt-get_the_easy_way_.28Synaptic.29](http://ubuntuguide.org/wiki/Dapper#How_to_apt-get_the_easy_way_.28Synaptic.29)

Had to do some updates and had an issue with a missing dependancy (also fixed using synaptic package manager). Firefox plugins work and am listeng to the world service as I type.

However...
The shortcut to RealPlayer 10 appears under Applications>Graphics>
I added it again to Applications>Sound and Vidio> using 'Alacarte Menu Editor' but the delete option is greyed out under the Graphics catagory.

I have scanned through: [http://www.gnome.org/start/2.0/menuediting.html](http://www.gnome.org/start/2.0/menuediting.html)
but 1 dont fully understand things. 
Extract from my user applications.menu file:

<Menu>
<Name>Graphics</Name>
<AppDir>/home/lostinswiss/.local/share/applications</AppDir>
</Menu>

Looks to me like AppDir is under the wrong menu however editing this does nothing.

Could somone tell me how to fix this please.

Also
I tried and tried to install Realplayer manualy but could not figure out where to install (not on desktop) it or how to get firefox plugins working with it. In the end I used synaptic (as described). If somone can tell me a nice method of installing manualy would apreciate it.

p.s. sorry about the spelling

In the Alacarte Menue editor, just uncheck the box next to the entry you dont want to see in the menu. To add it were you want it, highlight the catagory, click file, new entry. Use the same settings from the entry you just unchecked. You can read those settings by right clicking on it, then selecting properties.

---

### Post by LostInSwiss on 2006-07-11
Thanks for the quick reply. I understand that I can do that (and have done) but it troubels me that its worong in the first place (call me a geek). Would like to fix the issue at source (in settings file?) as a learning exercise.

Cheers

---

### Post by LostInSwiss on 2006-07-12
After a quick reply things go quiet. Did I put this post in the wrong place?

---

