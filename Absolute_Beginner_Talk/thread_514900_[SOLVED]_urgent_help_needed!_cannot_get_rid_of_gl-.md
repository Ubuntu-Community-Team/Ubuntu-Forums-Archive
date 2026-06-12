---
title: "[SOLVED] urgent help needed! cannot get rid of gl-desktop"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Korrontean on 2007-08-01
:(:(:(

This time, I gotta admit, it was ALL my fault. Yesterday night I was just playing around in the desktop, totally bored, and I tried something called, I think "GL-desktop". The screen went blank and now, when I turn on my latop, just after the splash screen, the screen goes totally white.

How can I recover from my recovery mode terminal? I mean, how can I turn off the "GL-desktop" (or something similar) from there?

:):)THANK YOU VERY MUCH:):)

---

### Post by Gadren on 2007-08-01
Can you do a "sudo apt-get remove gl-desktop"?

I think that when you're at the login screen, you can change your session to a "Safe" GNOME session, so you have a GUI to fix the problem.

---

### Post by Korrontean on 2007-08-01
:KS
I'm gonna try in a minute....thanks Gadren.

---

### Post by Korrontean on 2007-08-01
:(The terminal tells me there is no package kwnow as "gl-desktop":(

Any other ideas?

---

### Post by kerry_s on 2007-08-01
sudo nano /etc/X11/xorg.conf

you should really have "mc" for things like this, it's a command line filemanager.
sudo apt-get install mc

use> sudo mc <to run as root or> mc <for normal use.

---

### Post by Korrontean on 2007-08-01
Thanks kerry_s!

How can I edit xorg.conf so that my session does not load gl-desktop?

I did not understand how the file manager will help me :confused:

THANKS :)

---

### Post by kerry_s on 2007-08-01
did you install it?

if yes, than type this->

sudo mcedit /etc/X11/xorg.conf

than just change back what ever you changed.

---

### Post by Immolatus on 2007-08-01
in failsafe gnome do in terminal:

sudo apt-get remove_compiz

or sudo apt-get uninstall_compiz

one of these will fix the white screen but if you ever want desktop effects you'll have to reinstall compiz or use beryl.

Just for curiousity's sake did you install any effects? (aiglx and compiz are installed and running by default in feisty). if you installed xgl along with the aforementioned and present aiglx, the presence of both might cause the "whiteout".

---

### Post by benry on 2007-08-03
For future reference, if you enable GL Desktop, you can push Ctrl + Alt + F1, then login.

Now, run ```
top -bu <your username>
```.

Anything command with "compiz" in it, kill by typing ```
kill <pid>
```.

To get back to your desktop, just push Ctrl + Alt + F7.

Hope that helps later!

---

### Post by coolen on 2007-08-03
Best solution I can think of: failsafe Gnome session, then see if you can disable it. It might be under System -> Preferences. If so, just untick it.
Editing your xorg.conf file may just make things worse. Compiz is a program. It's not part of your X server, and can't be disabled from there. You have to stop it from running.

---

### Post by Korrontean on 2007-08-03
:(
Thank you all for your help...........

I tried Immolatus' solution, because it seemed easier........I succesfully removed compiz, but the "white screen of death" is still there.

I don't think I installed any effects in my Ubuntu Feisty. I remember I tried once, but I think it was on my previous Ubuntu, 6.06.

Kerry_s: I'm a little confused with your advice:

> did you install it?

if yes, than type this->

sudo mcedit /etc/X11/xorg.conf

than just change back what ever you changed.

I don't feel comfortable editing xorg.conf, and I don't know what I have to look for. What caused the problem was clicking on gl-desktop from system/preferences

Thanks again for your help......and patience!!! :):):)

---

### Post by Korrontean on 2007-08-03
By the way, login in the safe mode was the first solution I tried, on my own, but the "white screen of death" is exactly the same as in the normal mode.

---

### Post by anewguy on 2007-08-03
Log in to a terminal window at boot up, then try the following:

cd /etc/X11

ls -al xorg.conf*

if a xorg.conf~  or perhaps something like xorg.conf-backup shows, copy it via the following:

sudo cp xorg.conf~  xorg.conf   (obviously, if a backup is used, change the tilde to the backup name)

sudo gdm start  


then ctrl-alt-F7 and see if you now have a logon.  If so try logging on again.  If not, post back here again with the error.:)

---

### Post by Korrontean on 2007-08-03
Thank you very much, anewguy!!!

> Log in to a terminal window at boot up, then try the following:

cd /etc/X11

ls -al xorg.conf*

if a xorg.conf~ or perhaps something like xorg.conf-backup shows, copy it via the following:

sudo cp xorg.conf~ xorg.conf (obviously, if a backup is used, change the tilde to the backup name)

There was nothing like these. Only
xorg.conf
xorg.conf.20070519162152
xorg.conf.20070519162749

> sudo gdm start 

I had a message telling me gdm was already working, and that it was going to be aborted.

> then ctrl-alt-F7 and see if you now have a logon. If so try logging on again. If not, post back here again with the error.

I tried ctrl-alt-F7, nothing happened.

I tried sudo gdm start again, and I get a screen (I am translating, the original is in Basque) telling me:

> "It looks like server X is being executed in screen :0. Shall we try another screen number? If you reply NO, GDM will try to restart the server in :0 again. (You can switch consoles by pressing ctrl-alt and a function key. Usually server X is executed in number 7 and higher)"

Any other ideas???? Thanks:)

---

### Post by Korrontean on 2007-08-03
More info: I tried to log in after all this, and after the splash screen I could see my desktop :):):)

Until I got my "white screen of death" again :confused::confused::confused:

THANKS!

---

### Post by forestpixie on 2007-08-03
> **Korrontean said:**
> 
There was nothing like these. Only
xorg.conf
xorg.conf.20070519162152
xorg.conf.20070519162749

these are your xorg.conf and xorg.conf backups - instead of xorg.conf~ or xorg.conf.bak they have a timestamp.


try anewguy's thread but using the last one of these

so command would be

```
sudo cp xorg.conf.20070519162749 xorg.conf
``` instead of the example 

sudo cp xorg.conf~ xorg.conf


then carry on from there - obviously if anything else had been changed since that backup without a backup being done then it will be lost

---

### Post by Korrontean on 2007-08-03
Thanks, forestpixie!

Does it mean I'll lose all changes made in configuration or all files changed since this date???:(

---

### Post by forestpixie on 2007-08-03
it means you'll lose changes that have been made to the xorg.conf file - so if you had for instance got a new graphics card - changed resolution in the xorg.conf you'd lose them

but it only affects the files in the command
sudo cp xorg.conf.20070519162749 xorg.conf - is overwriting xorg.conf with the other timestamped file - 

so any other files are safe :)

I guess if it really goes belly up you could resort to reconfiguring your xorg.conf

---

### Post by Korrontean on 2007-08-03
Well, I copied the xorg.conf as you suggested, forestpixie, and although there is some change (I think I have my initial screen resolution that does not fit my laptop widescreen) I still get to a blank white screen after the login....... :(

---

### Post by Korrontean on 2007-08-03
Maybe I should backup my files from the terminal........(is it possible?) and install Ubuntu from zero again.

What do you think?

---

### Post by forestpixie on 2007-08-03
you could try reconfiguring your xserver - been looking for the command - can never remember how to do it - [http://ubuntuforums.org/showthread.php?t=514296](http://ubuntuforums.org/showthread.php?t=514296)

in a terminal

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

answer the questions as best as you can, have a search in the forum for reconfiguring xserver/graphics etc and you should at least get a screen back - you'll be able to specify resolutions in there - but I don't know what graphics cad you've got etc.

as an aside once I got my graphics working properly I made a copy of it so that I could get back to it if I needed to

---

### Post by Korrontean on 2007-08-03
Thanks forestpixie: now my screen resolution is back to normal.

However, I still get a blank screen after the splash screen. It now varies from session to session, in shapes and colours: white, black, combined.........

I can't believe I started this all just by clicking on gl-desktop ](*,) #-o

Soooo......the question still is.....how to switch off gl-desktop without access to the desktop.........

Thank you everyone for trying to help

Gotta leave the computer now for a while, so I'll be back in a few hours.

THANKS AGAIN ):P

---

### Post by forestpixie on 2007-08-03
have you seen these pages I don't know if they'll help you - I personally haven't doen any of the eye-candy stuff not being interested but a seaarch for GL-Desktop gets these

[http://gentoo-wiki.com/HOWTO_nVidia_GL_Desktop_Effects](http://gentoo-wiki.com/HOWTO_nVidia_GL_Desktop_Effects)
[http://sheehantu.wordpress.com/2007/05/28/customize-compiz-with-gl-desktop/](http://sheehantu.wordpress.com/2007/05/28/customize-compiz-with-gl-desktop/) - this one suggests that it's in the universla repos

any way good luck with it :)

---

### Post by anewguy on 2007-08-03
Sorry I didn't think of having you try this before:

when you get to the log on screen, look in the lower left of that screen and if the word "Options" is there, click on it, then click on "Sessions" then on the selection window that comes up select "gnome" and ok, then try logging in and post back here.:)

---

### Post by todh on 2007-08-07
Old post but hopefully help for future users.

I just had the same issue.  After stumbling around a bit I cured the problem by clearing the contents of a gnome config file in my home directory.

When you get to the "White Screen of Death" do the following.

1) press ctl+alt+f6
2) log in with your username and password
3) go to the proper config section - cd ~/.gconf/desktop/gnome/applications/window_manager
4) make a backup - cp %gconf.xml %gconf.xml.bak
5) edit the config file - nano %gconf.xml

[INDENT]You should see some xml formatted text something like this:
<?xml version="1.0"?>
<gconf>
        <entry name="current" mtime="1186467884" type="string">
                <stringvalue>/usr/bin/compiz</stringvalue>
        </entry>
        <entry name="default" mtime="1186467652" type="string">
                <stringvalue>/usr/bin/compiz</stringvalue>
        </entry>
</gconf>[/INDENT]

6) Delete the all contents
7) press ctl+O to save it
8) press ctl+X to exit nano
9) reboot - sudo shutdown -r 0
10) boot-up and login as normal

All should be well at this point

No guarantees, but it would like a charm for me.

Good Luck...

---

### Post by Korrontean on 2007-08-07
Thanks todh!

I'm trying to find the folder

cd ~/.gconf/desktop/gnome/applications/window_manager

But I'm not able to.............where is it?

Thanks!:)

---

### Post by Korrontean on 2007-08-07
Anewguy: I tried to login in a "gnome" session (it was one of the first solutions I tried), but I got to the "white screen of death" anyway............ :(

---

### Post by coolen on 2007-08-07
~/ is your home folder, if that's what you mean.
If you're trying to locate the file with ls, you'll need to specify the -a option (and be prepared for a lot of output) to show hidden files.

---

### Post by Korrontean on 2007-08-07
Todh: I'm already on the 9th step.

The terminal tells me "-r" is not a valid option and tells me to

> Try "reboot --help" for more information.

---

### Post by coolen on 2007-08-07
If simply deleting the content didn't work, restore the backup, and try changing compiz to metacity.

---

### Post by coolen on 2007-08-07
sudo reboot now

Always works for me :)

---

### Post by Korrontean on 2007-08-07
Thank you, Coolen!
Thank you, Todh!
You've been very helpful..............
[SIZE="7"]I've got my desktop back!!![/SIZE]
:guitar::guitar::guitar:
Deleting the content of **%gconf.xml **worked perfectly fine............

---

### Post by dougfractal on 2007-08-07
the command you where looking for> 
sudo apt-get remove desktop-effects

---

### Post by anewguy on 2007-08-07
> **Korrontean said:**
> Anewguy: I tried to login in a "gnome" session (it was one of the first solutions I tried), but I got to the "white screen of death" anyway............ :(

Sorry - I had a similar problem so I was hoping it would help!  Glad you got it fixed anyway!:)

---

### Post by coolen on 2007-08-08
Hey Korrontean, just wondering, did you install fusion-icon?
Just thinking, it seems that your default manager was changed to compiz (as opposed to the old method, which was to launch it upon login).

---

