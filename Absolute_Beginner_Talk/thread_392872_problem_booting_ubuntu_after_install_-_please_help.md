---
title: "problem booting ubuntu after install - please help"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Lambchop on 2007-03-25
I've been trying to get Ubuntu installed for the past 2 days now (and the whole experience has made me hate Windows even more :O )  I've finally gotten all my disk issues sorted out, my partitions made, Ubuntu installed successfully, and Grub works fine.  Go me.

But! There is a problem.  When I choose to boot Ubuntu from the Grub menu, it shows the little progress bar load screen, but once that is done it goes to a black screen and never changes.  I had this same problem when I first tried the LiveCD as well, but manually changing the video settings (F4 on the LiveCD menu) from VGA to 1280x1024x32 fixed the problem.  I assume this must be the cause of the problem.

My question then, is thus: How can I do this when booting up Ubuntu from the hard drive, and not from the LiveCD (since of course there is no option to do so when not using the CD)?

Thanks in advance for any help I receive - I REALLY WANT TO GET STARTED IN UBUNTU... AAAHH!!

---

### Post by lamalex on 2007-03-25
you could try doing the same thing you do when you boot live by doing this
```

control + alt + f1 //get into a terminal
login as root
nano /boot/grub/menu.lst

```

scroll down to your kernel and add your flag.
```


alternately
[code]
control + alt +f1
login as root
dpkg-reconfigure -phish xserver-xorg

```
GL DUDE

---

### Post by Lambchop on 2007-03-25
Alright, I booted Ubuntu in recovery mode, and entered the dpkg- string when the terminal line came up.  It brought up a screen with a bunch of choices, and VGA was highlighted.  The problem is, I don't know which one to pick.  My graphics card is an nVidia GeForce 6800 GT, if it matters.

---

### Post by freebird54 on 2007-03-25
To get the thing started in a particular mode, you can add a vga=### to the grub kernel line in your **/boot/grub/menu.lst** file.  Here is a list of the numbers to use (795 looks to be your requirement)

```
Colours   640x400 640x480 800x600 1024x768 1152x864 1280x1024 1600x1200
--------+--------------------------------------------------------------
 4 bits |    ?       ?      770       ?        ?        ?         ?
 8 bits |   768     769     771      773      353      775       796 
15 bits |    ?      784     787      790      354      793       797 
16 bits |    ?      758     788      791      355      794       798 
24 bits |    ?      786     789      792       ?       795       799 
32 bits |    ?       ?       ?        ?       356       ?

```

which would produce a line looking like:
```

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,3)
**kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hde4 ro quiet splash vga=795**
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

```

Hope this helps..  :)

---

### Post by Lambchop on 2007-03-25
Ok, adding the vga=795 thing helped, the screen now boots in the correct resolution.

BUT of course there is another problem =)  Now when Ubuntu boots it tells me that xserver is not set up correctly.

Some possibly useful tidbits from the error screen (I'm not sure what's important and what isn't):
 
Log file: "/var/log/Xorg.0.log"
Using config file: "/etc/X11/xorg.conf"
(EE) VGA(0): Driver can't support depth 24
(EE) Screen(s) found, but none have a usable configuration

After running the dkpg- command that was posted before, I did tinker with some things (not too many... only something that seemed applicable to my problem) in xserver... is there a way to reset it to default or anything?

---

### Post by freebird54 on 2007-03-25
You could post the file **/etc/X11/xorg.conf** here, and I might be able to spot some things that are not 'original'.  If you aren't sure how, say so :)

Also - when the dpkg-reconfigure ran, it should have written out a backup file with the format of  xorg.conf.200703ddhhmmss - where dd=day,hh-hour, mm=mins etc etc.

You could put it back - but I would just compare them in 2 instances of 'Text Editor' (gedit) and see what you've done :)

---

### Post by Lambchop on 2007-03-25
Alright, how can I post that **.conf** file?

Some other info: 
I tried changing the color depth from 24, setting it to 16 and then to 8.  At 16 it gave me basically the same error, and at 8 it comes up with some garbled colors across the top of the screen.  However, I can get to Terminal from that point, so I know that at least the OS itself is loading properly (but unfortunately not the graphics).

Also, when I do the dpkg-reconfigure, it brings up that blue and gray screen with the options on it.  Some of the slides have a list of items that are marked like this: [*] for selected or [ ] for unselected.  I cannot for the life of me figure out how to select or un-select them; the only keys that seem to do anything are the arrows and Enter.

---

### Post by Lambchop on 2007-03-25
bump

---

### Post by Muzik83 on 2007-03-25
To paste your xorg.conf file here, do the following

gedit /etc/X11/xorg.conf

Copy and paste all the contents here (alternatively you could attach the file, but that's more complicated and not needed!)

-sean

---

### Post by Muzik83 on 2007-03-25
Oops missed the how to check thing in your previous post.  

When doing dpkg-reconfigure you can tab or arrow around the elements, use space to select the current highlighted one, and enter to move to the next screen

-sean

---

### Post by freebird54 on 2007-03-25
OK - easiest way to post the file:  Go to a terminal and

```
cat /etc/X11/xorg.conf
```

Use the slider to get to the top of the 'output', highlight it, and Edit->Copy it (or <ctrl><shift>C ) - then paste it into the message  ( <ctrl>v )  While it is still highlighted, click the '#' near the right above in your message editor to 'put it in a box'.

BTW - if you are to EDIT the xorg.conf file when you are up and running in X - then
```

gksudo gedit /etc/X11/xorg.conf
```

is the way to go.  You need the admin rights to edit the file, and gedit is a graphic program and should have **gksudo** rather than **sudo** to get them.

AS for running the -reconfigure - someone beat me to it!  That program uses what USED to be a graphic interface back in the day  :)  As was said  <tab> to navigate between elements, <arrow> to move around in an element, and <space> to select/unselect choices (toggle the stars beside resolutions for example).

We'll get you going - hang in there!

---

### Post by Lambchop on 2007-03-25
YAY! I finally got it working... turns out all I had to do was go into dpkg-reconfigure and change from vga to nv driver ... which is strange because I thought I had tried that before.

Oh well... it works!

---

