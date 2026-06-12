---
title: "Fedora Infinity Changing Wallpaper"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by capitocapito on 2007-10-14
Does anybody know how to install the Infinity wallpapers from Fedora 8? (Seen [Here]("http://fedoraproject.org/wiki/Artwork/F8Themes/Infinity/Round3Final#head-0afce1582af5a054f81558f0e4148b3b6a445bbd"))

The wallpaper changes colors based on the time of day.  Cool, no?

---

### Post by NeBiRuSs on 2007-10-14
First thing you need to know Fedora Distro uses RPM pkgs so you need to convert this packages to Debian ( Ubuntu ) format ... in order to do this you need to Alien the RPM's

sudo apt-get install alien

sudo alien -i /path/to/file.rpm

If you are using GUI just double click to the file if not use your terminal and go to the location of the file and do this

sudo dpkg -i *.deb

And thats it ... this can give you and idea.

---

### Post by capitocapito on 2007-10-14
Thanks, but... did you visit the site?  I couldn't find any RPMs.  Still stuck.

---

### Post by kalpik on 2007-12-03
Bump.. I need this one too! :)

---

### Post by Vladimir_BG on 2007-12-29
I ditto that. I'd love to get both nodoka and infinity on Ubuntu...

---

### Post by CatKiller on 2007-12-29
I don't know how they do it in Fedora, but all of the individual images are linked from that page. It's reasonably straightforward to change the background in a script, so you could download all of the images to a folder and have a short script that picks the appropriate background for the time of day and sets it as the background. Erm, ```
gconf.client_get_default().set_string(
    '/desktop/gnome/background/picture_filename',
    nameoffile)
``` for use in a Python script, I think. Then you could just run that script every hour as a **cron** job.

---

### Post by arijit on 2008-01-03
I use fedora 8 on my laptop.
Here's the magic, There are set of wallpapers with a .xml file for the settings according to the time of the day...
Its really cool!

---

### Post by hellfire_bg on 2008-01-23
And how do you make other distributions change their GNOME wallpaper like Fedora does. I have downloaded all the wallpaper and the additional files but how can i make GNOME behave like Fedora`s GNOME?

---

### Post by joeamined on 2008-02-15
I have a nice and clean solution for you :guitar:
[http://joeamined.wordpress.com/2008/02/15/automatically-changing-wallpaper-relatively-to-daytime-in-ubuntu/](http://joeamined.wordpress.com/2008/02/15/automatically-changing-wallpaper-relatively-to-daytime-in-ubuntu/)
:popcorn:

---

### Post by DanaG on 2008-04-27
Oh hey, it turns out that Gnome, in Hardy, now has that feature -- apparently it's been pushed upstream, but not "flaunted" as a feature.
All you need are the images and the XML file.  Just run 'gnome-appearance-properties /blah/file.xml' -- but be aware that the XML file will have hardcoded paths in /usr/share/backgrounds, so put the folder there.

The nice fading effect is much better than the hard changes created by that script.

You can find some other nice wallpapers by searching for "slideshow" on gnome-look, and you can 'hack' together your own theme by making an appropriate XML file, modeled after the others.

I've even adapted images from the "Teahouse" theme for "iGoogle" with an xml file, so now I have a wallpaper that fades between the various parts of the day, with the fox doing various things.  Before I distribute it, though, I should probably find out a bit more about licensing and permissions.

---

### Post by randomnick on 2008-04-29
Nice! I was looking for this too.

Here's the Fedora 8 Nodoka theme install instructions for Ubuntu.

[http://www.ubuntu-unleashed.com/2007/09/howto-make-ubuntu-look-like-fedora-with.html](http://www.ubuntu-unleashed.com/2007/09/howto-make-ubuntu-look-like-fedora-with.html)

---

### Post by BananaJoe on 2008-05-09
> **DanaG said:**
> 
All you need are the images and the XML file.  Just run 'gnome-appearance-properties /blah/file.xml' -- but be aware that the XML file will have hardcoded paths in /usr/share/backgrounds, so put the folder there.


Hmmm, not on my machine (Hardy)

I copied the infintiy folder from a FC8 installation into /usr/share/backgrounds on my hardy

```
:/usr/share/backgrounds$ ls
heron-simple.png   space-01.jpg  space-04.jpg
infinity           space-02.jpg  space-05.jpg
simple-ubuntu.png  space-03.jpg  warty-final-ubuntu.png

```

After that i ran gnome-appearance-properties Programme/infinity.xml (i have the rights to run) in the gnome-terminal.

After that, this picture popps up and no fedora wallpapers :(.
Hmm?

regards

---

### Post by hlustik on 2008-05-14
Hi,

i had the same problem as you.
just check if you have read rights on the images

or otherwise just run:

```
sudo chmod a+r /usr/share/backgrounds/infinity -R
```

after this it worked for me like a charm :)

---

### Post by jpoRS on 2008-05-17
To the people that got this working in Hardy:

I ran the gnome-appearance-properties after chmodding the directory, and still no luck.  When I run gnome-appearance-properties I get this message

(gnome-appearance-properties:21256): Gtk-WARNING **: Theme directory 96x96/action of theme Human_Ultra_Black has no size field


(gnome-appearance-properties:21256): Gtk-WARNING **: Theme directory 96x96/action of theme Human_Ultra_Gray has no size field


(gnome-appearance-properties:21256): Gtk-WARNING **: Theme directory 96x96/action of theme Human_Effect_LightBlue has no size field


(gnome-appearance-properties:21256): Gtk-WARNING **: Theme directory 96x96/action of theme Human_Effect_Light has no size field



Thanks,
jim

---

