---
title: "a question about /etc/X11/xorg.conf files......"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-06-02
hello.
ok, ive got an nvidia 7600gs agp card, and ive installed the latest driver for it (used envy, installed ok)
the question is that ive been messing around with the xorg.conf files to get more resolutions into the file so i can have more choice in games, basically if i try and use a resolution in game that isnt in the xorg.conf then the game doesnt display on all of the screen and i cant see half of it, which causes problems, but while i was messing around with the xorg.conf i noticed that if i open up the nvida settings (ive got a launcher on one of my panels) and mess about with the settings, i can then save the configuration file, if i select preview theres different stuff in that file than the stuff i see if i open xorg.conf in a text editor.
so for example - if i open xorg.conf (sudo gedit /etc/X11/xorg.conf) and go to the "screen" section i can then see the resolutions and i might for example see - "1280x800"  "1152x864" and some others and then they are repeated on a few more lines as you run down the list.
but if i open the xorg.conf preview when im saving the configuration file through the nvidia setting i get a different set of resolutions, well not different as such but i might get - "1280 x900" "1280x800" "1152x864"
so are there 2 xorg configuration files ? 
and is it best to have as many resolutions as your monitor is capable of displaying in the xorg.conf file ?
cheers

---

### Post by bodhi.zazen on 2007-06-02
> **techno-mole said:**
> hello.
ok, ive got an nvidia 7600gs agp card, and ive installed the latest driver for it (used envy, installed ok)
the question is that ive been messing around with the xorg.conf files

Very nice example of a long and run on sentance. I *almost posted a run-on answer, but decided to be nice 

> Very nice example of a long and run on sentance. I *almost posted a run-on answer, but decided to be nice, at this point I would advise you use nvidia-settings to manage xorg.conf but, in order to save any changes you make you need to launch nvidia settings as root, so, in  a terminal, gksudo nvidia-settings, that is because you can not save the changes you made via nvidia-settings if you are not running as root, it is a permissions thing, you can not edit system files as a user, so, you can not edit /etc/X11/xorg.conf if you are running nvidia-settings as a user, so run as root, as above, look back, "There can be only 1", you just can not edit it without running as root, with the nvidia driver, using nvidia settings, jsut set the highest resolution you need and go from there, if you need to edit /etc/X11/xorg.conf, make a back up first, then : gksudo gedit /etc/X11/xorg.conf, add each resolution you need, do not add ones you do not want.


:lolflag:

At this point I would advise you use nvidia-settings to manage xorg.conf.

But, in order to save any changes you make you need to launch nvidia settings as root ...

So, in  a terminal, 

```
gksudo nvidia-settings
```

> to get more resolutions into the file so i can have more choice in games, basically if i try and use a resolution in game that isnt in the xorg.conf then the game doesnt display on all of the screen and i cant see half of it, which causes problems, but while i was messing around with the xorg.conf i noticed that if i open up the nvida settings (ive got a launcher on one of my panels) and mess about with the settings, i can then save the configuration file, if i select preview theres different stuff in that file than the stuff i see if i open xorg.conf in a text editor.

That is because you can not save the changes you made via nvidia-settings if you are not running as root (it is a permissions thing).

You can not edit system files as a user. So, you can not edit /etc/X11/xorg.conf if you are running nvidia-settings as a user ...

So run as root (as above).

> so for example - if i open xorg.conf (sudo gedit /etc/X11/xorg.conf) and go to the "screen" section i can then see the resolutions and i might for example see - "1280x800"  "1152x864" and some others and then they are repeated on a few more lines as you run down the list.
but if i open the xorg.conf preview when im saving the configuration file through the nvidia setting i get a different set of resolutions, well not different as such but i might get - "1280 x900" "1280x800" "1152x864"
so are there 2 xorg configuration files ? 

Look up ... "There can be only 1", you just can not edit it without running as root.

> and is it best to have as many resolutions as your monitor is capable of displaying in the xorg.conf file ?
cheers

With the nvidia driver, using nvidia settings, jsut set the highest resolution you need and go from there.

If you need to edit /etc/X11/xorg.conf, make a back up first.

Then :```
gksudo gedit /etc/X11/xorg.conf
```

Add each resolution you need, do not add ones you do not want.

---

### Post by techno-mole on 2007-06-02
cheers, figures it would be a permissions thing, i always forget about that, i guess its a hang up from using windows as an administrator, i personally think that having run things s root to do certain things is a good idea, its stopped me from making a big mess of things. :D
i'll apologize for the massive sentence that was my first post.
i do tend to forget about paragraphs now and then.
cheers for the help.

---

### Post by acutu on 2007-06-02
Take care here, I just edited myetc/X11/xorg.conf  for my Nvidia geforce go 7300 and I saved the file, rebooted and have white text on black background saying cannot open display! I still get nice colour Ubuntu as its loading and unloading but cannot use the computer! Being dealt with in another thread, but just to say take care. I think I will need to reinstall.:(

Al C.

---

### Post by bodhi.zazen on 2007-06-02
> **acutu said:**
> Take care here, I just edited myetc/X11/xorg.conf  for my Nvidia geforce go 7300 and I saved the file, rebooted and have white text on black background saying cannot open display! I still get nice colour Ubuntu as its loading and unloading but cannot use the computer! Being dealt with in another thread, but just to say take care. I think I will need to reinstall.:(

Al C.

LOL

That is why we back up our system files before we edit them :)

On the command line enter the following :

```
sudo nvidia-xconfig
```

---

### Post by acutu on 2007-06-02
I did backup, I saw it in the folder, same name but with a date and time in the name with it, but seems the backup didn't kick in.

Al C

---

### Post by dpzektor on 2007-06-02
> **acutu said:**
> Take care here, I just edited myetc/X11/xorg.conf  for my Nvidia geforce go 7300 and I saved the file, rebooted and have white text on black background saying cannot open display! I still get nice colour Ubuntu as its loading and unloading but cannot use the computer! Being dealt with in another thread, but just to say take care. I think I will need to reinstall.:(

Al C.


No need to reinstall:

sudo dpkg -reconfigure xserver-xorg

This will restore the default xorg.conf, get you back in, and you can try your nvidia settings again:

sudo nvidia-settings

This will allow you to adjust your nvidia settings (tv-out, resolutions, etc) and since you are using it as root you will be able to save the xorg.conf. Works fine for me on my 7600GS.

---

### Post by acutu on 2007-06-02
Thx Dpzektor, Just rebooting.

Al C

---

### Post by acutu on 2007-06-02
Unfortunately, doesn't seem to be working. I get a blue screen with wierd black text pattern and message :

'Failed to start the X server [your graphical interface] It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?'

I have tried both, to no avail.
It is on a triple boot system, and I still have graphical interface ok for Kubuntu.

Al C.

---

### Post by bodhi.zazen on 2007-06-02
> **dpzektor said:**
> No need to reinstall:

sudo dpkg -reconfigure xserver-xorg

bodhi hands dpzektor sudo nvidia-xconfig

> nvidia-xconfig generates one from scratch using default settings

[man nvidia-xconfig](http://olympus.het.brown.edu/cgi-bin/man/man2html?nvidia-xconfig+1)

Another very cool comand :

```
sudo nvidia-xconfig -composite; sudo nvidia-xconfig -allow-glx-with-composite; sudo nvidia-xconfig -render-accel; sudo nvidia-xconfig -add-argb-glx-visuals
```

*All one line

This series of commands will configure X for Beryl, no need to manually edit xorg.conf

~ Bodhi thinks that is very cool ! !

Oh, if you want to reconfigure X with new users, consider : > sudo dpkg-reconfigure -phigh xserver-xorg

The -phigh flag selects defaults for everything but resolution (easier for new users).

> This will restore the default xorg.conf, get you back in, and you can try your nvidia settings again:

sudo nvidia-settings

This will allow you to adjust your nvidia settings (tv-out, resolutions, etc) and since you are using it as root you will be able to save the xorg.conf. Works fine for me on my 7600GS.

You should gksudo that last command :)

```
gksudo nvidia-settings
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by acutu on 2007-06-02
Thx Bodhi.zazen

Will give it a go.

Al C

---

### Post by acutu on 2007-06-02
Well, Bodhi.zazen, 
I have typed that in for X for Beryl to get to work on, then I did the gksudo, it asked for my password, then login incorrect, then asked for my user then password, then it says [gksudo:5753]: Gtk-WARNING **: cannot open display: computername:$

Al C.

---

### Post by bodhi.zazen on 2007-06-02
> **acutu said:**
> Well, Bodhi.zazen, 
I have typed that in for X for Beryl to get to work on, then I did the gksudo, it asked for my password, then login incorrect, then asked for my user then password, then it says [gksudo:5753]: Gtk-WARNING **: cannot open display: computername:$

Al C.

Yea, that is a well known "bug"

You can ignore it, the application *should start

If not, well you can fall back to sudo, although that is somewhat less optimal.

---

### Post by acutu on 2007-06-02
Hi, bodhi.zazen I rebooted again and back to blue screen with X server failed start message. Maybe I will need to reinstall after all.

Thx for your help anyway, sorry to have wasted your time.

Al C.

---

### Post by acutu on 2007-06-02
bodhi.zazen Thx, success at last. I decided to do the reconfigure X with new users tip, and that worked. I don't think theresolution is quiter right, I chose the setting on the list above vga, but we are out of the black and white or blue screens!

Cheers!

Al C.

Resolved.

---

