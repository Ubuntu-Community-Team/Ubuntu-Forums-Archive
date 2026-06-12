---
title: "fluxbox"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by syedn on 2006-08-29
A couple questions:

Is the fluxbox in the repos the same as the latest on fluxbox.sourceforge.net?  Does it matter really?

I downloaded the tar from sourceforge for that version, did the ./configure, make, make install and nothing went wrong.. but how do i get it running?

what would i do to uinstall that since it wasn't an aptitude install or package install or anything?

thanks a bunch!

Dan

---

### Post by meng on 2006-08-29
Try logging out, when you get to the login manager choose Sessions and see if fluxbox is an option.

---

### Post by croak77 on 2006-08-29
The fluxbox from fluxbox.sourceforge.net is newer. 

To uninstall cd to where you un-tared it and run sudo make uninstall.

---

### Post by kerry_s on 2006-08-29
The one for the fluxbox site is newer than the one in the repo, but the one in the repo is just as good. I tried both of them as well and don't like the newer one cause it dropped alot of duel monitor support that i use. I'm running dapper server install + flubox from the repos and it's working great. I wanted the maximum choice with my install, so i only have what i use. Here's a pic of mine after alot of tweaking :p

---

### Post by syedn on 2006-08-29
thanks for the posts!

when I log out, fluxbox is not available in the sessions menu though.. any ideas?

---

### Post by bodhi.zazen on 2006-08-29
Switch to tty1 -> Crtl-Alt-F1

Log in.

```
startx /usr/bin/startfluxbox
```

If this works you will need to edit GDM/KDM

---

### Post by syedn on 2006-08-29
i'm starting to think when i did the make install stuff i didn't do it right.

does it matter what directory i un-tar it in?

---

### Post by bodhi.zazen on 2006-08-29
> **syedn said:**
> i'm starting to think when i did the makene only fr install stuff i didn't do it right.

does it matter what directory i un-tar it in?

Good question, but no it should not matter what directory you un tar in.

Two questions:

You need to run make install as:
```
sudo make install
```

What do you get when you type
```
which fluxbox
```
in a terminal?

---

### Post by syedn on 2006-08-29
which fluxbox produced

/usr/local/bin/fluxbox


also switching to tty1 and typing

startx /usr/bin/startfluxbox

gave me a fatal error about Display 0 being in use by a server already.

---

### Post by bodhi.zazen on 2006-08-30
Thank you.

From tty1 you should be able to start fluxbox with
```
startx /usr/local/bin/startfluxbox -- :1
```

This starts fluxbox on tty9 (Ctrl-alt-F9)

If this works we can configure GDM

---

### Post by bodhi.zazen on 2006-08-30
If you are interested, I am willing to help you. It appears you will have to configure fluxbox manually.

Perhaps it would be easier to install fluxobx from the repositories?

```
sudo make uninstall #run this from the fluxbox directory where you ran make install
Enable the ubutnu repositories
aptitude install fluxbox
```

Otherwise you will have to configure GDM and possibly the fluxbox menu as well.

Ubuntu repositories: /etc/apt/sources.list should look like this:
> #
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by syedn on 2006-08-30
yeah, i have the repos all enabled and such, was just going for the newest version :) i've put all futzing with the desktop on halt right now though and am setting to work on a laptop i just obtained for very little $$ :D

thanks for the help though!

---

### Post by syedn on 2006-08-30
so continuing this fluxbox adventure.. when i do 'sudo make uninstall' in the fluxbox directory.. it returns a bunch of Error 1 messages.

any ideas?

```

dan@dualistic:~/fluxbox-1.0rc2$ sudo make uninstall
Making uninstall in data
make[1]: Entering directory `/home/dan/fluxbox-1.0rc2/data'
Making uninstall in styles
make[2]: Entering directory `/home/dan/fluxbox-1.0rc2/data/styles'
Making uninstall in Emerge
make[3]: Entering directory `/home/dan/fluxbox-1.0rc2/data/styles/Emerge'
Making uninstall in pixmaps
make[4]: Entering directory `/home/dan/fluxbox-1.0rc2/data/styles/Emerge/pixmaps'
 rm -f '/usr/local/share/fluxbox/styles/Emerge/pixmaps/bullet.xpm'
 rm -f '/usr/local/share/fluxbox/styles/Emerge/pixmaps/close.xpm'
 rm -f '/usr/local/share/fluxbox/styles/Emerge/pixmaps/icon.xpm'
 rm -f '/usr/local/share/fluxbox/styles/Emerge/pixmaps/max.xpm'
 rm -f '/usr/local/share/fluxbox/styles/Emerge/pixmaps/stick-unfocus.xpm'
 rm -f '/usr/local/share/fluxbox/styles/Emerge/pixmaps/stuck-unfocus.xpm'
 rm -f '/usr/local/share/fluxbox/styles/Emerge/pixmaps/close-pressed.xpm'
 rm -f '/usr/local/share/fluxbox/styles/Emerge/pixmaps/icon-pressed.xpm'
 rm -f '/usr/local/share/fluxbox/styles/Emerge/pixmaps/max-pressed.xpm'
 rm -f '/usr/local/share/fluxbox/styles/Emerge/pixmaps/selected.xpm'
 rm -f '/usr/local/share/fluxbox/styles/Emerge/pixmaps/stick.xpm'
 rm -f '/usr/local/share/fluxbox/styles/Emerge/pixmaps/stuck.xpm'
 rm -f '/usr/local/share/fluxbox/styles/Emerge/pixmaps/close-unfocus.xpm'
 rm -f '/usr/local/share/fluxbox/styles/Emerge/pixmaps/icon-unfocus.xpm'
 rm -f '/usr/local/share/fluxbox/styles/Emerge/pixmaps/max-unfocus.xpm'
 rm -f '/usr/local/share/fluxbox/styles/Emerge/pixmaps/stick-pressed.xpm'
 rm -f '/usr/local/share/fluxbox/styles/Emerge/pixmaps/stuck-pressed.xpm'
 rm -f '/usr/local/share/fluxbox/styles/Emerge/pixmaps/unselected.xpm'
make[4]: Leaving directory `/home/dan/fluxbox-1.0rc2/data/styles/Emerge/pixmaps'make[4]: Entering directory `/home/dan/fluxbox-1.0rc2/data/styles/Emerge'
 rm -f '/usr/local/share/fluxbox/styles/Emerge/theme.cfg'
make[4]: Leaving directory `/home/dan/fluxbox-1.0rc2/data/styles/Emerge'
make[3]: Leaving directory `/home/dan/fluxbox-1.0rc2/data/styles/Emerge'
Making uninstall in BlueFlux
make[3]: Entering directory `/home/dan/fluxbox-1.0rc2/data/styles/BlueFlux'
Making uninstall in pixmaps
make[4]: Entering directory `/home/dan/fluxbox-1.0rc2/data/styles/BlueFlux/pixmaps'
 rm -f '/usr/local/share/fluxbox/styles/BlueFlux/pixmaps/button_close_active.xpm'
 rm -f '/usr/local/share/fluxbox/styles/BlueFlux/pixmaps/button_close_pressed.xpm'
 rm -f '/usr/local/share/fluxbox/styles/BlueFlux/pixmaps/button_close_unfocus.xpm'
 rm -f '/usr/local/share/fluxbox/styles/BlueFlux/pixmaps/button_max_active.xpm'
 rm -f '/usr/local/share/fluxbox/styles/BlueFlux/pixmaps/button_max_pressed.xpm' rm -f '/usr/local/share/fluxbox/styles/BlueFlux/pixmaps/button_max_unfocus.xpm' rm -f '/usr/local/share/fluxbox/styles/BlueFlux/pixmaps/button_min_active.xpm'
 rm -f '/usr/local/share/fluxbox/styles/BlueFlux/pixmaps/button_min_pressed.xpm' rm -f '/usr/local/share/fluxbox/styles/BlueFlux/pixmaps/button_min_unfocus.xpm' rm -f '/usr/local/share/fluxbox/styles/BlueFlux/pixmaps/button_stick_active.xpm'
 rm -f '/usr/local/share/fluxbox/styles/BlueFlux/pixmaps/button_stick_pressed.xpm'
 rm -f '/usr/local/share/fluxbox/styles/BlueFlux/pixmaps/button_stick_unfocus.xpm'
 rm -f '/usr/local/share/fluxbox/styles/BlueFlux/pixmaps/button_stuck.xpm'
 rm -f '/usr/local/share/fluxbox/styles/BlueFlux/pixmaps/button_stuck_unfocus.xpm'
 rm -f '/usr/local/share/fluxbox/styles/BlueFlux/pixmaps/button_toolbar.xpm'
 rm -f '/usr/local/share/fluxbox/styles/BlueFlux/pixmaps/button_toolbar_pressed.xpm'
 rm -f '/usr/local/share/fluxbox/styles/BlueFlux/pixmaps/menu_frame.xpm'
 rm -f '/usr/local/share/fluxbox/styles/BlueFlux/pixmaps/title_bar.xpm'
 rm -f '/usr/local/share/fluxbox/styles/BlueFlux/pixmaps/title_bar_unfocus.xpm'
 rm -f '/usr/local/share/fluxbox/styles/BlueFlux/pixmaps/toolbar.xpm'
 rm -f '/usr/local/share/fluxbox/styles/BlueFlux/pixmaps/toolbar_label.xpm'
make[4]: Leaving directory `/home/dan/fluxbox-1.0rc2/data/styles/BlueFlux/pixmaps'
make[4]: Entering directory `/home/dan/fluxbox-1.0rc2/data/styles/BlueFlux'
 rm -f '/usr/local/share/fluxbox/styles/BlueFlux/theme.cfg'
make[4]: Leaving directory `/home/dan/fluxbox-1.0rc2/data/styles/BlueFlux'
make[3]: Leaving directory `/home/dan/fluxbox-1.0rc2/data/styles/BlueFlux'
make[3]: Entering directory `/home/dan/fluxbox-1.0rc2/data/styles'
rmdir /usr/local/share/fluxbox/styles
rmdir: /usr/local/share/fluxbox/styles: Directory not empty
make[3]: *** [uninstall-local] Error 1
make[3]: Leaving directory `/home/dan/fluxbox-1.0rc2/data/styles'
make[2]: *** [uninstall-recursive] Error 1
make[2]: Leaving directory `/home/dan/fluxbox-1.0rc2/data/styles'
make[1]: *** [uninstall-recursive] Error 1
make[1]: Leaving directory `/home/dan/fluxbox-1.0rc2/data'
make: *** [uninstall-recursive] Error 1


```

---

### Post by bodhi.zazen on 2006-08-31
These do not seem to be problematic per se,

Advise:
```
sudo rm -R /usr/share/fluxbox
sudo rm -R /home/dan/fluxbox-1.0rc2
```

re-run sudo make uninstall

---

