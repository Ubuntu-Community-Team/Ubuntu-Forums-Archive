---
title: "old-aged noobie needs help please."
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by md11driver on 2007-12-02
i'm a sixty one year old long time windows user who started using linux (7.10 gutsy gibbon) less than a week ago.  i have many hours invested (i'm retired) and have several good features up and running (windows xp on a vmware virtual server, etc)

i'm noticing what appear to be installation issues.

1.  my mouse in linux only displays two adjusting tabs instead of the typical three (no "pointer" option).  also, when selecting multiple files, i have to hold down ctrl+alt to get the process to work, instead of the usual ctrl.

2. my cd writer will read only some cds and will not write at all.  (displays "unable to mount volume" error message.  my dvd rom player displays the same error message.  

can these things be fixed, or do i need to abandon all my hard work and reinstall everything?

i've searched this forum and others and can't find similar problems.

my machine is a four-year-old sony vaio (3.06 mhz, one mg ram, big hard drive)

all internet and sharing connections working great.

thanks in advance for helping a geezer with his first steps.

thanks in advance for helping a geezer.

---

### Post by daimaru on 2007-12-02
first off welcome and its great that your giving ubuntu a try.
I have never heard of a ctrl+alt click version and that the ctrl key does not work, so I won't be of much help there. the only thing i can suggest is using the shift key to multiple select files. click one file hold shift and click another file.  this selects multiple files, ctrl selects individual files or lets you add remove files from already selected ones. 

> my mouse in linux only displays two adjusting tabs instead of the typical three (no "pointer" option). 
I don't really understand what you mean by that. Does your mouse only have 2 buttons and no scrollwheel? 
if so maybe it would help to enable          Option          "Emulate3Buttons"       "true" in your xorg.conf file.

```
sudo gedit /etc/X11/xorg.conf
```
under Section "InputDevice" (the one where it says mouse, cause there are many inputdevice sections like keyboard wacom etc)
here is my mouse section.

```

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"    "/dev/input/mice"
    Option        "Protocol"    "ExplorerPS/2"
    Option        "ZAxisMapping"    "4 5"
    Option        "Buttons"     "7"
        Option        "ButtonMapping" "1 2 3 6 7"
EndSection

```
yours will look different, and may already have Option          "Emulate3Buttons"       "true" in there. otherwise add this to it. 
```
Option          "Emulate3Buttons"       "true"
```

As to the cd-burning question. I remember reading somewhere about sony vaio laptops and that you need to apply a fix to get the cd rom to work on some of them. but in order to find that thread again, you would have to post the full name of your sony vaio model. for example sony vaio VGN-FZ11Z  

sorry i can not be of more help, but maybe someone with more experience picks up this thread and can help you out.

---

### Post by md11driver on 2007-12-02
thanks, daimaru.

my brother's mouse (earlier ver of ubuntu) shows three adjusting tabs when selecting systems/preferences/mouse.  according to my 7.10 help files, mine should also.  my mouse preferences show only two adjusting tabs (buttons, motion, but no pointer options).

usually, with windows and confirmed by other users of linux, i can select multiple individual files by pushing ctrl, clicking left mouse and highlighting the files.  in this way i can select desired files from a list of files.  when i hold ctrl and click left mouse, i get a grabbing hand sign.  in order to select multiple desired files, i found by experimentation that if i hold down ctrl+alt, it works as it should.  pretty basic stuff but not working correctly.

my mouse is set to "emulate 3 buttons"

my puter is a sony desktop pcv-rx991.  i'm a fairly good windows guy and have helped more than a few neighbors, but i'm stumbling over hazards in the dark with linux

my mouse issues i can live with, but i really must be able to write to cd in order to live with this operating system.  everyone i've personally spoken with has had no issues with hardware recognitions when installing gutsy.

i'm trying very hard to avoid a total reinstall and seeing all my work go up in smoke. 

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"

---

### Post by pinguino13 on 2007-12-02
Welcome to Ubuntu. Your mouse pointer options are in System>Preferences>Appearance and click on Customize. Hope this helps.

---

### Post by scrooge_74 on 2007-12-02
Nice to hear you are comming on board, sadly as was my case, my many years of experience with Windows only served me to not be afraid to try out things, all my knowledge was worth 0.  

Do check for your exact model there is probably a fix somewhere.

also check [http://help.ubuntu.com](http://help.ubuntu.com) is a good place to learn, also all my google searches are done in [http://google.com/linux](http://google.com/linux)  to get my answers faster

---

### Post by Bartender on 2007-12-02
Try installing braseros and see if it talks to your optical drives.
Also try installing K3B from the repositories - it'll need a bunch of KDE stuff to make it work but it's a good burn utility.
I had a funny experience with optical drives just a few weeks ago.  I could not control burn speeds at all with a fairly new Lite-On CD burner.  You could click on "speed" but all the options were grayed out.  I swapped the Lite-On out for a 5 year old TDK burner and was able to set burn speeds.
Moral of the story - you gotta be flexible, and willing to try different parts if you have some.

---

### Post by scrooge_74 on 2007-12-02
I second brasero is nice burner, some brand of cd drives always gave me troubles with some brands of CDs when I used to have Windows

---

### Post by md11driver on 2007-12-02
you're all great to reply.  thanks!!!

i downloaded and installed k3b.  i was unable to find braseros after a quick search.  i attempted to burn a data cd using k3b and got an error message which said:

"cdrecord has no permission to open the device"

does this give anyone any insight?

waiting hopefully,
md11driver

---

### Post by scrooge_74 on 2007-12-03
the name is brasero, about the error code try running the program from a terminal using sudo that way the error should go away.  Other possibility is that you need to add cdrecord  to the cdrom group or yourself.

---

### Post by md11driver on 2007-12-04
md11driver here.  i did a reinstall and all my issues went away.  long live linux!!!!

---

### Post by scrooge_74 on 2007-12-04
Great anything else post

---

### Post by jimmj43 on 2007-12-04
As one geezer to another..... This may not match what you've got because I'm running Feisty, but if I go to: System > Preferences > and look for "appearance" I come up empty-handed. There IS, however a "Mouse" selection, and it has three tabs.

I now have a red pointer approximately the size of a Buick that I'm unlikely to 'lose' on a text-rich page. :lolflag:

---

### Post by louieb on 2007-12-04
> **md11driver said:**
> 1.  my mouse in linux only displays two adjusting tabs instead of the typical three (no "pointer" option).  also, when selecting multiple files, i have to hold down ctrl+alt to get the process to work, instead of the usual ctrl.
50 something guy here using Gutsy.  I only have 2 tabs also.  No pointer theme tab either. Help shows how to use it -  :) if it  were  there.  

When selecting files Crtl+click and CTRL+Alt+Click work the same for me.

One nice add-on for Firefox is **no squint. **It remembers zoom level on a site by site basis.

---

### Post by texasjim on 2008-01-11
First off, Welcome from another 61-yr old geezer.  Been running Ubuntu since Feb '07 and it will keep you thinkin.

For the k3b - cdrecord problem:
In a terminal window enter
sudo chown 777 /dev/hdx where x=your disk number.  May be sdcx.

That fixed my problem with k3b & cdrecord.

Keep pushing the buttons and turning the knobs, it's the best way I know to
get familiar with the system, and you really gotta work to break it.

---

