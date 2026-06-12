---
title: "xplanet"
date: 2005-01-24
forum: Art &amp; Design
---

### Post by scott_b on 2005-01-24
can anyone tell me how to get xplanet working?  
I tried this:  [http://stef.tvk.rwth-aachen.de/~nazgul/files/xplanet-gnome](http://stef.tvk.rwth-aachen.de/~nazgul/files/xplanet-gnome)
but didn't have any luck.

any suggestions?
-scott

---

### Post by scott_b on 2005-04-28
From what i can tell, nautilus is the problem. If it is killed, or not allowed to start up, then xplanet works fine. It'd be nice to run them both.

---

### Post by francisco_athens on 2006-02-17
no, no, no... you dont have to kill nautilus!
this page: [http://stef.tvk.rwth-aachen.de/~nazgul/linux-hacks.php]("http://stef.tvk.rwth-aachen.de/~nazgul/linux-hacks.php") has a great script and instructions on how to use, but you will need to modify the script to suit where you want the images to be generated and change
```
gconftool -t str -s /desktop/gnome/background/picture_filename "$PREFIX$OUTPUT"

```
to:
```
gconftool -t str -s /apps/nautilus/preferences/background_filename "$PREFIX$OUTPUT"
```

be sure the script is executable
you can make it run at startup with the system=>preferences=>sessions tool

also, start up your
applications=>system tools=>configuration editor
and be sure to set
/apps/nautilus/preferences/background_set to "on" (checked)

another useful hint is to make a .xplanet folder in your home folder and set up some other nice scripts for clouds and other neat stuff as described here:
[http://joffie.selwerd.nl/xplanet/]("http://joffie.selwerd.nl/xplanet/")
enjoy!

Francisco

---

### Post by tasism on 2006-12-19
Hi all,

I realise this is an old post but perhaps someone can offer a helping hand: I have followed all the instructions and it works - ALMOST!

I get the xplanet background but only inside Nautilus windows (even Desktop if I open it from inside a Nautilus window). I have been unsuccessful in having the same image displayed by Nautilus on the root background window... (Gnome shows a solid colour).

My desktop system is Ubuntu 6.10.

Any ideas please? I realise this is more of an Nautilus issue than xplanet, but perhaps someone can help.

Thanks!

---

### Post by bytecode on 2006-12-21
Hi tasism,
I got into XPlanet myself this week on Ubuntu 6.10 Edgy Eft, Gnome2.

Are you able to post your configuration? Any error messages etc. that you may receive?
When first trying to configure XPlanet, it is good to call it from the shell, leaving the shell open and waiting to see whether any error messages appear for further diagnosis.

I appreciate that you state that you "have followed all the instructions" but we need more details so as to help you effectively

For instance, I myself have based my configuration on this popular script found over on Christian Kirbachs site: [http://stef.tvk.rwth-aachen.de/~nazgul/linux-hacks.php#xplanet-gnome2](http://stef.tvk.rwth-aachen.de/~nazgul/linux-hacks.php#xplanet-gnome2)

Which periodically calls xplanet to render an image, and then gconf to update your desktop wallpaper.

You will find that the script assumes the existence of following folder / directory with appropriate read/write permissions:

/multimedia/wallpapers/

but you can change this to whichever folder you wish by modifying the line:
PREFIX=/multimedia/wallpapers/
Do you have any other scripts / apps running that may also be trying to modify your wallpaper?

---

### Post by kq6up on 2007-01-23
I am running 6.10.  I can't get this setup to work.  It seems as if some other application is controlling what image is displayed on the desktop.

Any ideas?

---

### Post by BLTicklemonster on 2007-01-27
I found xplanet in icewm, and wondered what the heck it was. Now that I see that it DOES stuff, I want to use it. But all this is confusing to me. I went to the xplanet scripts site, but being a newb to linux, it all makes no sense to me as to what I actually have to do.

---

### Post by cactaur on 2007-01-30
Ok, I installed xplanet-images, then changed the PREFIX to "/usr/share/xplanet/images/". When I run it, I get

```
rm: remove write-protected regular file `/usr/share/xplanet/images/xplanet.png'? y
rm: cannot remove `/usr/share/xplanet/images/xplanet.png': Permission denied
Error: Can't create /usr/share/xplanet/images/2xplanet.png.
Exiting from DisplayOutput.cpp at line 68

```

I tried running the script as root, and nothing happens at all. No errors, nothing.

---

### Post by durand on 2007-01-31
the prefix should be something you have write access to so u can do ```
sudo chmod 777 -Rf /usr/share/xplanet/images/
``` and it should work... .wysiwyg { background-attachment: scroll; background-repeat: repeat; background-position: 0% 0%; background-color: #ffffff; background-image: none; color: #666666; font-family: "Verdana [microsoft]", "Lucida [B&h]", "Arial [monotype]", "Helvetica [Adobe]", "Arial [monotype]"; font-style: normal; font-variant: normal; font-weight: 400; font-size: 10pt; line-height: normal } p { margin: 0px; }

---

### Post by Martin on 2007-05-15
I 've got xplanet working sometimes. I got the scripts working, changed the paths to suit and now have an xplanet desktop background with cloud, without clouds, flat or aa a globe, with bumps withuot bumps - so it works. But only sometimes. 50% of the time when I logging in I have the xplanet background the other times I don't. Has anybody else had this?

---

### Post by shamrock_uk on 2007-07-05
The HOWTO [here](http://ubuntuforums.org/showthread.php?t=351341&highlight=xplanet) explains how to get it working.

(Note that unless you want the picture in the background of your nautilus as well, then you **don't** want to do the steps posted in this thread above - leave nautilus background unchecked in gconf-editor and make sure the line in the script says "picture_filename" not "background_filename".)

Change these two lines so they reflect a write-able location:

```
PREFIX=/home/user/.xplanet/
OUTPUT=xplanet.png
```

Then run the script from the terminal. Eg. if its saved at /home/user/gnome-planet then do ```
./gnome-planet
```

You'll get an error about a .png file, ignore it and ctrl+c to end the script if needed. Then go to select a wallpaper as normal, navigate to the .png and choose it as the wallpaper. It should now be automatically updated.

Edit: Forgot to mention that you'll also need to make the script file executable. Right click on the file -> properties -> permissions then check the 'execute' box.

---

