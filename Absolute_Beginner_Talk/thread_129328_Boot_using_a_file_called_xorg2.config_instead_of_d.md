---
title: "Boot using a file called xorg2.config instead of default"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by noob_Lance on 2006-02-13
hey, i was wondering how i could make Ubuntu boot with a different xorg file instead of the default one. I have 2 monitors, my laptop monitor and a nice big 19" lcd. but the lcd has alot higher rez then my laptop. Thus 2 xorg files... one for my laptop and 1 for the LCD. its too much of a pain to reconfigure the xorg file every weekend.. 

anyone help

~Lance

---

### Post by noob_Lance on 2006-02-14
anyone???

---

### Post by heimo on 2006-02-14
When you use the external monitor, is it the only display in use? (I mean, there's no some kind of dual display setup with laptop's display.) As everything else than resolution stays same, why not just change the resolution from System menu (Screen Resolution). Or hit ctrl+alt+numpad's plus sign to switch different resolutions. (Am I missing something here?)

---

### Post by noob_Lance on 2006-02-14
there is no dual monitor goin on lol... for some reason i cant get that to work... and as for jsut changing the resolution... it dosnt work as the monitor has alot higher resolution then my laptop screen... so the only way to get it to work is to  either boot using a different file or deal with reconfiguring every night and morning.... <_<


~Lance

---

### Post by biguns on 2006-02-14
Check this out and see if it helps....

[http://gentoo-wiki.com/HOWTO_Dual_Monitors]("http://gentoo-wiki.com/HOWTO_Dual_Monitors")

---

### Post by noob_Lance on 2006-02-14
Nah, i dont need dual monitors really...too much going on... i tired it before and didnt like it lol... i just want to use one monitor at a time and thats all. But i will keep that link incase i ever change my mind :)

~Lance

---

### Post by David Corrales on 2006-02-14
Haven't tried something like this but it might work...
You could make the file */etc/X11/xorg.conf* a soft link pointing to whichever of the 2 files you want. For example, say you have 3 files:

[I]
/etc/X11/xorg.conf     (link)
/etc/X11/xorg-laptop.conf
/etc/X11/xorg-monitor.conf
[/I]

And make a small script that switches the link from one config file to the other. Then call that script during boot to get something like (during the boot process):
```

Select the preferred video display device:
1) Laptop
2) Monitor

```
You just select the one you need and the proper file gets linked for the session!

Again, I haven't done something like this but it sounds very doable in practice so you might want to try it out :)

---

### Post by noob_Lance on 2006-02-14
Hm... that sounds like a damn good idea actually :D

but how can i make it a link and such? I get what your saying... but i still lost lol :p

~Lance

---

### Post by David Corrales on 2006-02-14
For the link, first create the 2 different configuration files and make sure they work correctly.
[I]
/etc/X11/xorg-laptop.conf
/etc/X11/xorg-monitor.conf
[/I]

Then, we'll need to replace the regular */etc/X11/xorg.conf* with a link:

[B]
sudo rm /etc/X11/xorg.conf
sudo ln -s /etc/X11/xorg-laptop.conf /etc/X11/xorg.conf
[/B]

You can now try the following to check that everything worked as expected:

[B]
ls -l /etc/X11
[/B]

There should be a line that reads something like (I removed irrelevant info): 

[I]
-rw-r--r--   1 root root (...) xorg.conf -> /etc/X11/xorg-laptop.conf
[/I]

So basicaly the procedure to switch from one to the other would be like this: remove the link and recreate it pointing to the other configuration file.

From laptop to monitor:
[B]
sudo rm /etc/X11/xorg.conf
sudo ln -s /etc/X11/xorg-monitor.conf /etc/X11/xorg.conf
[/B]

From monitor to laptop:
[B]
sudo rm /etc/X11/xorg.conf
sudo ln -s /etc/X11/xorg-laptop.conf /etc/X11/xorg.conf
[/B]

---

### Post by heimo on 2006-02-14
I may have a suggestion for this solution, David. It doesn't work for my computer, but it may work in Lance's case. Maybe some of you could try what happens if you run xresprobe - it requires one parameter, driver (vesa, nv, nvidia, ati...). For me, output is empty:
```
xresprobe nv
id:
res:
freq:
disptype:

``` 
If it's not, then it shouldn't be too hard to make a script that changes configuration file during boot automatically based on the output (assuming it detects external monitor when connected). Just a thought.

EDIT: ddcprobe is interesting too
EDIT2: BTW, Shouldn't it be possible to configure both monitors to same configuration file in a way that both monitors show the same stuff and then use the laptop's fn+F10 (or what-ever) to switch which monitors get signal?

---

### Post by noob_Lance on 2006-02-14
OOOH lol ok i get it... this will be easy :)

---

### Post by David Corrales on 2006-02-14
Heimo, have you tried running the command as super user? I did run it as a regular user and got no results, running it with **sudo** produced results though.

---

### Post by noob_Lance on 2006-02-16
how can i get X to update when i use dual screen... my laptop with ubuntu will support it.. but it dosnt stretch it.. its jsut a copy of it. but it stays at the laptop rez instead of its highest.. and it gives me no other options..

~Lance

---

### Post by heimo on 2006-02-16
[quote=David Corrales]Heimo, have you tried running the command as super user? I did run it as a regular user and got no results, running it with **sudo** produced results though.[/quote] Yeah, I ran it both with user and root and it was blank. This has been the same always, my monitor (Hitachi CM752ET) doesn't seem to support autodetection (or it doesn't work). Thanks for suggestion.

---

### Post by icitall on 2008-01-05
I am in a similar situation.  I use my Laptop monitor along with an external monitor connected to a docking station at work.  At home I only use one monitor connected to my docking station.  I use an init script to figure out where I am at to configure my xorg.conf accordingly.  I look for the network subnet to figure out which configuration to use.  You will notice "touch" statements in the script.  I remark out the lines that do the work and un-remark these to test the script.

#! /bin/sh
#
#
### BEGIN INIT INFO
# Provides:          whereami
# Required-Start:    $network $local_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 6
### END INIT INFO
. /lib/lsb/init-functions
PATH="/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin"
echo "Configuring X"
echo ""
echo "Where the HELL am I ???"
case "$1" in
start)
        ifconfig |grep 10.1.7.255
        if [ $? = 0 ]
                then
                        rm /etc/X11/xorg.conf
                        ln -s /etc/X11/xorg.conf-dual /etc/X11/xorg.conf
                        echo "Work ;-("
#                       touch /etc/X11/work
                 else
                        rm /etc/X11/xorg.conf
                        ln -s /etc/X11/xorg.conf-single /etc/X11/xorg.conf
                        echo "CyberSpace ;-)"
#                       touch /etc/X11/cyberspace
        fi
        ;;
stop)
        echo "I am out of here ;-)"
        ;;
*)
        echo "Usage: /etc/init.d/whereami {start|stop|restart|force-reload}"
        exit 1
        ;;
esac
exit 0

Hope this helps

---

