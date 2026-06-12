---
title: "GTK/Unity theming"
date: 2011-07-22
forum: Art &amp; Design
---

### Post by dragonboss on 2011-07-22
I would like to begin work creating themes for Ubuntu, I am currently running 11.04, so possibly the themes should be able to work with the unity interface. The themes i wish to make are based off the the following litestep themes for windows:

WTR by [novoo]("http://novoo.deviantart.com/") on deviant art
[http://fc05.deviantart.net/fs44/f/2009/102/c/e/WTR_by_novoo.jpg](http://fc05.deviantart.net/fs44/f/2009/102/c/e/WTR_by_novoo.jpg)

and

aftermath by [kowoolo]("http://kowoolo.deviantart.com/") on deviant art
[http://fc06.deviantart.net/fs30/f/2008/166/0/8/08633256c853290767138fc015a4191d.png](http://fc06.deviantart.net/fs30/f/2008/166/0/8/08633256c853290767138fc015a4191d.png)

Obviously some of the effects cannot be done with the default gtk theme, so these will be done with conky and lua, which I have done to some extent (I made a mod of the conky lunatico script) based on izobalanx work.
I have no experience creating themes for Ubuntu, so any help will be greatly appreciated.
Also pointers to where to begin are also appreciated
Attached is my Conky Lunatico mod

---

### Post by Frogs Hair on 2011-07-22
One piece of software to look into is the Widget Factory in the software center . Also look for GTK themes that are similar with a public License to use as a starting point . You will need to know how to change the gtkrc files to get the results you want . Keep in mind that 11.10 will not have Gnome 2.xx but it will be around in other distributions for a while.

[http://orford.org/gtk/](http://orford.org/gtk/) 

[http://en.wikibooks.org/wiki/GTK%2B_By_Example/Theming](http://en.wikibooks.org/wiki/GTK%2B_By_Example/Theming)

[http://live.gnome.org/GnomeArt/Tutorials/GtkThemes](http://live.gnome.org/GnomeArt/Tutorials/GtkThemes)

---

### Post by dragonboss on 2011-07-22
Thanks for the info

---

### Post by godhika on 2011-07-25
You should remember that 11.10 marks the switch to gtk3 which is theming wise a whole different beast. Also the Unity panel (the top bar and the dropdown menus) is now rendered by gtk3. So you might wanna look at themes that provide both gtk2 and 3 themes.
[http://lassekongo83.deviantart.com/art/Zukitwo-203936861]("http://lassekongo83.deviantart.com/art/Zukitwo-203936861") 
Is probably one of the most refined out there atm.
Also very interesting is the version of Ubuntus Ambiance theme currently in development (remember thats way more refined then the one currently in Oneiric but still WIP). That theme is probably also the best showcase for the capabilities of the new Unico theme engine [https://code.launchpad.net/~unico-team/unico/trunk]("https://code.launchpad.net/~unico-team/unico/trunk")
which also still WIP but as you can see Cimi is introducing kick *** new features almost by the hour. The only other Gtk3 theme engine currently out there is Gnomes own Adwaita but it is not really a match for Unico ;)
Hope that helps to get you started

---

### Post by dragonboss on 2011-07-26
Thank for the tip!

---

### Post by ladede on 2011-07-26
Great Man...

---

