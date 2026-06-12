---
title: "Startup Programs - Fluxbox, server install"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by avalonpimp on 2006-09-03
Setup -
Dapper alternative CD install - server.
THen installed Xorg and Fluxbox (old labtop cant handle much - inspiron 3800)

Problem - 

I would like to run several commands at startup, all programs that require Xserver to be running. My first thoughts was to edit ~/.fluxbox/startup and the lines...

/usr/bin/tilda &

I added this before the part about 'exec fluxbox', i also tired adding these lines after the 'exec fluxbox'. I found that if i execute the ~/.fluxbox/startup file...BOOM the scripts works and the programs open, but the terminal gives an error of another windows Xserver running. 

So in what file in Ubuntu can i put these commands in, so they run after login, and X has started. (i tired a few files in /etc/X11/ but nothing working there either)

Thx

---

### Post by croak77 on 2006-09-03
You can put them in ~/.xinitrc.

tilda &
exec fluxbox

---

### Post by avalonpimp on 2006-09-03
in my home folder /~ i have no .xinitrc file. Should i make one and put those commands in it, with that filename. Any other possible places to put these startup commanads??

---

### Post by croak77 on 2006-09-03
Yeah...just make a ~/.xinitrc

---

### Post by avalonpimp on 2006-09-03
Just tired it, created the file with those two commands in it, inside the home directed. Restart = nothing. I even tired to chmod 755 the file to make it exec OK...nothing.

Its like that file ~/.fluxbox/startup isnt even gettin executed at startup. That someother file is inializing X and fluxbox. Any idea of where that is?
(Cuz if i run the ~/.fluxbox/startup file in X, then the programs i want get run, but then complains of another instance of windows manager)

---

### Post by croak77 on 2006-09-04
You should not have to chmod anything. The defualt 644 is fine. All you do is create a file called ~/.xinitrc. Put any commands you want when you startx in that file. Then just type startx and it will execute all the commands starting with the first. Make sure exec fluxbox comes after everything else in your ~/.xinitrc. Make sure you remove any commands you put in your ~/.fluxbox/startup that are also in your ~/.xinitrc.

---

### Post by kerry_s on 2006-09-04
The /.fluxbox/startup is used to start programs and fluxbox. Did you install a login manager or are you just running startx? Here's how i do mine->

at the prompt login
sudo su    <makes you root
nano /etc/apt/sources.list
comment(#) out the cd and uncomment the other repos
apt-get update
apt-get install x-window-system-core xterm eterm gdm synaptic
reboot

That's it just select fluxbox for session and login to gdm with your user name and password. I usally change gdmsetup to auto log me in so i don't see that any more(it will be in the right click menu) then i use synaptic to trim my install down farther then install what i want. Here's my startup that fluxbox makes and i just add my apps and settings->
```
# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# You can set your favourite wallpaper here if you don't want
# to do it from your style.
#
# bsetbg -f ~/pictures/wallpaper.png
#
# This sets a black background

#/usr/bin/fbsetroot -solid black

# This shows the fluxbox-splash-screen
# fbsetbg -C /usr/share/fluxbox/splash.jpg

# Other examples. Check man xset for details.
#
# Turn off beeps:
# xset -b
#
# Increase the keyboard repeat-rate:
# xset r rate 195 35
#
# Your own fonts-dir:
# xset +fp /home/user/.font
#
# Your favourite mouse cursor:
# xsetroot -cursor_name right_ptr
#
# Change your keymap:
# xmodmap ~/.Xmodmap



# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &


wmix &
mount.app &
xset s off off &
xset +dpms &
xset dpms 0 0 300 &
sudo athcool on &
sudo conky &


# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec /usr/bin/fluxbox
# or if you want to keep a log:
# exec /usr/bin/fluxbox -log ~/.fluxbox/log

```

---

### Post by avalonpimp on 2006-09-04
Thx guyz, i forgot a crucial piece of info....that i use xdm to login. and dont have to run startx manually. Well after much trial and error i found if i edit /etc/X11/Xsession.d/50xorg-common_determine-startup 
 - then add the programs i want
  xterm &
  xmms &

They start up, wonderful. Never did get but the ~/.xinitrc way to work, but im guessin cuz i use xdm to login. Thx so much...oh and beauitful desktop pics, could u fill me in on what fluxbox theme that is (i like the transpancy) and what conky theme?? thx

---

### Post by kerry_s on 2006-09-04
> **avalonpimp said:**
> 
They start up, wonderful. Never did get but the ~/.xinitrc way to work, but im guessin cuz i use xdm to login. Thx so much...oh and beauitful desktop pics, could u fill me in on what fluxbox theme that is (i like the transpancy) and what conky theme?? thx

The theme is Nuevat3k-Glacier, i forget where i got the background from, i uploaded it to image shack, just right click and save as ( [http://img245.imageshack.us/img245/6281/openya4.jpg](http://img245.imageshack.us/img245/6281/openya4.jpg) ) you should be able to do the transparency to, just right click and set the alpha to "0" for the task bar and in configuration>transparency for the rest. The them really doesn't matter to much when you go transparent, but some work better than others. Conky is just transparent .

Let us know if you need anything else, take care.

---

