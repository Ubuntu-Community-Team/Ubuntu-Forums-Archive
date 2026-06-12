---
title: "Installing programs?!?!?!"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by yota99 on 2006-04-21
Everytime I've tried to install something it gives me the same error "Failed to apply all changes"

then in the terminal below it says 

Preconfiguring packages ...
dpkg: parese error, in file '/var/lib/dpkg/available' near line 18310 package 'li
bgtk2.0-bin';
 `Depends' field, reference to `libcairo2' : version contains ` '

so I went to the update thing and downloaded libcairo2 and when it was done downloading it said "Failed to apply all changes" !!!! which has happened with every single package I've tried installing.

man Im starting to get pissed off with Ubuntu. Why does nothing work? I can't even listen to my damn mp3s.

---

### Post by 3rdalbum on 2006-04-21
Try enabling all the repositories. In Synaptic, go "Settings > Repositories" and enable all of the items in there. That may solve your problems. If it does, then do a search for "gstreamer" and download everything there. That will get your MP3s playing, as well as quite a lot of other formats.

---

### Post by linuxa on 2006-04-21
What are you using to install software.

If you are new to Linux/Ubuntu, I'd suggest a GUI tool install of the command line, since the former generally takes care of all the dependency issues for you.

See if you can find under your Menu -> System any programs described as a package manager (e.g. synaptic, adept).

---

### Post by yota99 on 2006-04-22
[QUOTE=3rdalbum]Try enabling all the repositories. In Synaptic, go "Settings > Repositories" and enable all of the items in there. That may solve your problems. If it does, then do a search for "gstreamer" and download everything there. That will get your MP3s playing, as well as quite a lot of other formats.[/QUOTE]
Enabling all the repositories didnt work. 

>  	What are you using to install software.

If you are new to Linux/Ubuntu, I'd suggest a GUI tool install of the command line, since the former generally takes care of all the dependency issues for you.

See if you can find under your Menu -> System any programs described as a package manager (e.g. synaptic, adept).


I tried using synaptic,  "add applications" and the update utility
should I try re installing ubuntu or something?

oh and my clock, as I posted in another post, is wrong then when I change it and boot windows windows is wrong. what the ?

---

### Post by trent dillman on 2006-04-22
Ok, for installing programs...open your favorite terminal program (gnome-terminal or konsole or whatever) and see if

```
sudo apt-get -f install
```

helps....


As for the clock, it's because Linux likes to have the system clock set to UTC, whereas Windows wants it as your local time.

---

### Post by yota99 on 2006-04-22
[QUOTE=trent dillman]Ok, for installing programs...open your favorite terminal program (gnome-terminal or konsole or whatever) and see if

```
sudo apt-get -f install
```

helps....


As for the clock, it's because Linux likes to have the system clock set to UTC, whereas Windows wants it as your local time.[/QUOTE]

I tried that in the terminal and it said this:

```
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 90 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
dpkg: parse error, in file `/var/lib/dpkg/available' near line 18310 package `libgtk2.0-bin':
 `Depends' field, reference to `libcairo2': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)

```
:confused: :confused:

Im going to resort to booting windows up if I cant get this figured out soon

---

### Post by linuxa on 2006-04-22
OK, with the time thing. I'm assuming here that your Windows' time is correct?

Now if I understand correctly, Windows changes the Bios to Local time upon boot, whereas Linux will adjust the Bios to Greenwich Mean Time (GMT aka UTC) and adjust the clock that gets shown when it gets to X. Linux by the way is doing things the right way :D

And because we can't change the way Windows does things, you have to change the way Linux does it. To do this, edit 

**/etc/default/rcS**

And change the UTC option to No. That should fix the time problem.

Your issue with apt/dpkg is somewhat more complicated. Your list of available software seem to be corrupt (/var/lib/dpkg/available). Go into a Terminal. Back up your current version of the list:

**sudo mv /var/lib/dpkg/available /var/lib/dpkg/available.corrupt**

Generate a new list:

**sudo dselect update**

You should now get a available file in the directory. Try installing the application you want with apt-get now. If it works, you can delete the package.corrupt file that you backed up earlier.

Tell us how that goes.

---

### Post by yota99 on 2006-04-22
HOLY CRAP!! Thank you that worked!!!
Im listening to music via linux right now :D

Thanks again for all the help everyone.

why did that happen though?

---

### Post by linuxa on 2006-04-22
Glad things worked out for you man.

No idea why it was corrupt to begin with though. Bad source list, bad Ubuntu iso? The possibilities are endless :P

You know what they say:

S**t happens :D

---

