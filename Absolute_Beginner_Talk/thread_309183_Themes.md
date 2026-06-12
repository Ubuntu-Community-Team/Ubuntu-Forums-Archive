---
title: "Themes"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2006-11-29
i tried the gnome-looks, but couldn't find any files that i can open up as theme in theme manager. I want complete themes like Human, Crystal, Outdoors, Silicon, Mist etc, i.e. a single installated theme with different looks on icons, menus and bars..... anybody have any idea what i am saying? suggest a complete link...

---

### Post by Ben Sprinkle on 2006-11-29
[http://gnome-look.org](http://gnome-look.org)

Look again, there are plenty there.
If you need more icons look in the section, you may have to install manually.

---

### Post by shoaibi on 2006-11-29
i need full fledged themes like Mist, silicon etc, and i even tried downloading GDK 2.0 or 1,0 themes but every files is save in .tar.gz and when i click it in Theme Manager's install theme after some file copying it says inavlid file format.....

---

### Post by Ben Sprinkle on 2006-11-29
That's what I am talking about, inside the tar.gz is your theme. To extract, type this in terminal.

```

sudo tar -xvf theme.tar.gz

```
Replace theme with your filename.

---

### Post by shoaibi on 2006-11-29
and what's the name of full fledged themes? GDK?

---

### Post by Ben Sprinkle on 2006-11-29
No, GTK is a library.

Things of that sort are theme engines which control what the buttons etc. look like.

Themes are just using another installed engine. A theme makes the window appearance look different. (Colors and buttons on window)

So I think you are wanting a new engine, icons and theme?

---

### Post by shoaibi on 2006-11-29
Hmmmm i want a complete theme in one file, no separate installation of icons, and all that.... a single download which i can import in theme managers and the looks change i.e. menu bar's color and style, icons all that....

---

### Post by Ben Sprinkle on 2006-11-29
Well your out of luck then. :)
I don't think that's possible unless someone made a tarball resembling the structure. (/usr etc)

---

### Post by nickburns on 2006-11-29
You can get some extra themes with:

sudo apt-get install gnome-themes-extras 

don't know if this is all your looking for...

---

### Post by Ben Sprinkle on 2006-11-29
I am getting a picture, I think he's trying to download a tarball from gnome-look with a theme engine, a new theme, and new icons.

He just wants to import it and does not realize sometimes you have to do it manually.

---

### Post by shoaibi on 2006-11-29
I am just a newbie, with not much experience with linux, i.e. not more then these 3 days since i installed Ubuntu again.... :( , what i wanna say is that have any of you used themes in windows? remember of windows98 [i will quote it to make the example easy]  if we  downloaded a theme, then that theme wil include its own set of icons, its own looks and etc. So i wanna if there is something like that here as well? if yes then what's its name and where to download it?

---

### Post by Ben Sprinkle on 2006-11-29
Yes there is but it's a pain to make them all in one tarball (tar.gz) so people do it seperate. Most of the time you will have to install manually which isn't that hard.

---

### Post by shoaibi on 2006-11-29
Hmmm does that mean i will have to install icon set, then looks and then wallpaper? am i correct? [hmm i am starting to get a hold of it ;) :P ]

---

### Post by Ben Sprinkle on 2006-11-29
Yeah, but look in /usr/share/themes at one of the .theme files to add which new icon set you want.

To install a new icon set:

Download the tar.gz

Open a terminal and type:
```

sudo cd /usr/share/icons
sudo tar -xvf /home/YOURUSER!/Desktop/ICONSET.tar.gz

```
Replace your user and the filename of course.

Icon set is installed, now you need to make your current theme to use them. :)

Type this:
```

gksudo nautilus /usr/share/themes

```

Find your current theme and go in it.
Open the .theme or .desktop file in Gedit.

Find the spot that says icon= or something about icons.
Replace the spot after the = sign with the name of the icon set you downloaded.

If you can't remember the name type:
```

gksudo nautilus /usr/share/icons

```
And find the folder name of your icons.
The folder name is the thing you put in that .desktop or .theme file.

After that restart computer and there you go.
If you need help installing a new GTK engine or theme also tell me. I just told you how to install icons. :)

---

### Post by shoaibi on 2006-11-29
such a long procedure, out of which i don't get somethings :(, hmmm may be i will do it later when i get some familiar with Ubuntu

---

### Post by Ben Sprinkle on 2006-11-29
Naw, think of it as a 3 step procedure for each thing, icons, engine (which is a 2 step), and theme (3 step). :)

---

### Post by CowzRule on 2006-11-29
To install a theme you downloaded in a "tar.gz" format. Open your theme manager (Preferences/Theme). Drag and drop the "tar.gz" file onto the theme manager window.


Hey, Hey..This is my 50th bean :)

---

### Post by Ben Sprinkle on 2006-11-29
Actually cow, that does not always work so it is important to know the manual way.

---

### Post by Vord on 2006-12-01
Edit: Fixed it.

---

### Post by Zerocool10482 on 2006-12-01
You could also use the **Gnome Art Manager.** 

[http://www.miketech.net/gnome-art/](http://www.miketech.net/gnome-art/)

You can install it from Synaptic Package Manager by searching for gnome-art.

Or the command line - sudo apt-get install gnome-art
Press enter
Give your password.
Then go System > Preferences > Art Manager.

---

### Post by rpradeep on 2006-12-01
Actually the thing is GNOME is too much customizable than windows. This freedom sometimes will make you think things are much tougher than Windows. But in the long run you will realize that it is highly fit your taste in each and every items you like to customize. 

Basically it is like you are served with a cup of tea.. or served with milk, tea, sugar.. to make the tea exactly the way you like.

Good Luck.

---

