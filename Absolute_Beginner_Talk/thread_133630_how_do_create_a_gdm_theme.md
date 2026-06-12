---
title: "how do create a gdm theme"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by Ghetto_Smurf on 2006-02-20
again,

how do i create a gdm theme 

OR

how can i modify one (I.E. changing a gdm theme background)

---

### Post by ardchoille on 2006-02-20
I have been creating my own GDM themes for a couple years and the only way I have seen is to get a GDM theme from someone, or go to /usr/share/gdm/themes and get one, take it apart and see how it was made. It's mostly a set of graphics and two files that can be edited in a text editor. It's really simple to figure out. Just get one and unpack it and see how it was made. You can change things around and repackage it, then install it with the Login Screen gui.

---

### Post by Ghetto_Smurf on 2006-02-20
ill try that.. thx

if anyone has more sugestions, just shout it!

---

### Post by ardchoille on 2006-02-20
I uploaded one I made recently, see the attachment. Download it, open a term and type:

```

tar -xzf /path/to/variety-blue-gdm.tar.gz

```
and see what's inside. They are really easy to make.

You can take a screenshot of the GDM login screen with the following steps:

1) log out of your current session so that you are at the gdm login screen
2) CTRL+ALT+F2 to get to a tty
3) run the following command 
```

echo "chvt 7 ; sleep 5 ; XAUTHORITY=/var/lib/gdm/:0.Xauth DISPLAY=:0.0 import -window root /tmp/screenshot.png" > /tmp/capture

```
wait 10 seconds and the screenshot will be placed in /tmp/capture but you can change that part of the command to place the screenshot anywhere you want.

The easiest way to do the screenshot is to put the above command in a file by itself, then log out, then get into the tty and type "cat /path/to/file/containing_screenshot_command" so the command will be on the screen so you can type it as you read it.. it's long and kinda easy to forget :)

You'll need to create your gdm theme, install and enable it, then log out and take a screenshot. then log back in, uninstall it, place the new screenshot into the package, repackage, reinstall and you're done.

I wish there were a better way to handle all of this but I haven't found a way yet.

---

### Post by todderick on 2008-01-02
Thanks so much for the sample, your right it is easy!  So exciting! :D

---

### Post by k3lt01 on 2008-01-02
I am wanting to do the same thing but found this site, I will try it out later today but if anyone else has a go please let us know the results.

[http://live.gnome.org/GnomeArt/Tutorials/GdmThemes](http://live.gnome.org/GnomeArt/Tutorials/GdmThemes)

---

### Post by Thund3rstruck on 2008-01-10
Have you tried the GDM Maker script?
[http://forumubuntusoftware.info/viewtopic.php?f=23&t=427]("http://forumubuntusoftware.info/viewtopic.php?f=23&t=427")

---

