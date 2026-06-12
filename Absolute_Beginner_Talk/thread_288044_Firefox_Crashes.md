---
title: "Firefox Crashes"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by APNelson.L on 2006-10-29
I just installed ubuntu 6.10 and firefox now seems to crash when it tries to block pop ups but when I go on websites without any pop ups that firefox could try to block everything works fine. Has anyone else had a problem similar to this?

---

### Post by mariov on 2006-10-29
Same problem here.
Actaully I updated Firefox before updating my Ubuntu version. Firefox 2.0 was working fine until y upgraded to 6.10

---

### Post by PPAAUULL on 2006-10-29
Have you tried uninstalling it and then installing it again from the Edgy Repos?

---

### Post by APNelson.L on 2006-10-29
i have not tried doing that, how exactly would i do it?

---

### Post by Error_Msg on 2006-11-01
I get consistent, daily Epiphany crashes that freeze my system completely forcing me to shut down.
These two sites are notorious for crashing my machine:
[www.clarin.com.ar](www.clarin.com.ar)
[www.lanacion.com.ar](www.lanacion.com.ar)
Not the first page, but if I follow any links on it, it's a guaranteed crash.
I researched, and installed this thing that will keep flash content from loading until you activate it if you want to see it. This worked for a couple of days, but now it's back to crasharama.
I just avoid those sites, but some others crash me too.

E_M

---

### Post by think13 on 2006-11-01
The problem is most likely flash.  Try doing this:

> Note: if firefox crashes when visiting a website with flash content, do the following:

sudo gedit /usr/bin/firefox

and add the following line as last but one line of the file:

export XLIB_SKIP_ARGB_VISUALS=1

Now firefox shouldn't crash anymore. (Launchpad bug report: [1])

    * Restart Mozilla Firefox 

(taken from [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox))

---

