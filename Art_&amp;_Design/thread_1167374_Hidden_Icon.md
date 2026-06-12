---
title: "Hidden Icon"
date: 2009-05-22
forum: Art &amp; Design
---

### Post by jesterthejedi on 2009-05-22
Hello I am the dev of an icon theme, and this icon is bugging me. I cannot locate it anywhere in /usr/share/icons or /usr/share/pixmaps. I just need to know the icon name and location so that I can write an updated icon for my theme. See the screen shot, its the first 3 icons that need to be located.

---

### Post by cubeist on 2009-06-11
> **jesterthejedi said:**
> Hello I am the dev of an icon theme, and this icon is bugging me. I cannot locate it anywhere in /usr/share/icons or /usr/share/pixmaps. I just need to know the icon name and location so that I can write an updated icon for my theme. See the screen shot, its the first 3 icons that need to be located.

Hey,
I really like your mashup icon group.  I have actually been working on it recently to improve a few missing / ugly existing icons and you have piqued my interest on this one...I will post back if I find it!

---

### Post by cubeist on 2009-06-11
Ok, this is driving me crazy!  It should definitely be in somewhere in /usr.  The closest I can find is the base clock icon without the 'ringing' lines... that icon is called "gworldclock.png" and is at

/usr/share/app-install/icons

---

### Post by cubeist on 2009-06-11
Found it!

called stock_alarm.png

/usr/share/icons/gnome/48x48/stock/generic

---

### Post by jesterthejedi on 2009-06-14
Awesome. That will be replaced in the next Mashup release. Here is my suggestion>

Also need to find the Rhythmbox drag/drop icon for moving to media. I'll post the screen shot in a bit.

---

### Post by cubeist on 2009-06-15
That's a perfect icon.  Keep up the cool work... if you need my help with anything, just pm me, cheers

---

### Post by jesterthejedi on 2009-06-22
3 nasty icons still remain.

1. when using Rhythmbox, drag a song to a playlist or audio player and the mouse pointer draws an icon with the new/add/move/copy text like view. I would like to have a musical note or similar in its place. No Screenshot could be taken for some reason.
2. Multimedia Volume Control, its already in my theme, but in Services it wont change over. See png for detail.
3. Synaptic Tray Icon, its and old /usr/share/pixmaps relic that cannot be located either. See the other png file.

I am also aware that the last two may be bugs in Gnome that are causing old icons to be used. Any info would be stellar.

Billy

---

### Post by cubeist on 2009-06-22
> **jesterthejedi said:**
> 3 nasty icons still remain.

1. when using Rhythmbox, drag a song to a playlist or audio player and the mouse pointer draws an icon with the new/add/move/copy text like view. I would like to have a musical note or similar in its place. No Screenshot could be taken for some reason.
2. Multimedia Volume Control, its already in my theme, but in Services it wont change over. See png for detail.
3. Synaptic Tray Icon, its and old /usr/share/pixmaps relic that cannot be located either. See the other png file.

I am also aware that the last two may be bugs in Gnome that are causing old icons to be used. Any info would be stellar.

Billy

1. I know the icon you are talking about, it is an ugly piece of paper with a little blue picture (a head) on it.  I can't find this generic icon anywhere... Unfortunately, even if I could find it, as far as I can tell, you could change it to a nicer icon, but not to a rhythmbox only icon.  It appears the pixmap is shared across the system, so if you had a musical note on it, then any other app would also use the same pixmap...

2. This is strange because if I select another icon set (ie, hydroxygen) which uses a new multimedia icon, it does change in the services window (See pic).  In the hydroxygen icon set, the icon is in a folder 48x48/apps and is labeled multimedia-volume-contol.png and then a second icon called multimedia.png.  I am not sure why it won't change in mashup, but at least we know it is possible to change.

3. This little monster is either the one at /usr/share/synaptic/pixmaps/ and is called synaptic_32x32.xpm, or in /usr/share/synaptic/pixmaps/glade/ called synaptic_mini.xpm.  Unfortunately, adding either to the apps folder doesn't change it...but I haven't logged out and back in yet...

---

### Post by cubeist on 2009-06-22
forgot the image...doh!

---

### Post by jesterthejedi on 2009-06-24
So is it the multimedia-volume-control.png or multimedia.png that the system uses for this menu?

---

### Post by cubeist on 2009-06-24
> **jesterthejedi said:**
> So is it the multimedia-volume-control.png or multimedia.png that the system uses for this menu?

Good question!  I have replaced both, even added a 48x48 pixmap, and it still refuses to change.

---

### Post by jesterthejedi on 2009-06-25
The status for offline/online.png had to be scaled down to get them working in evolution. You mentioned a 48x folder. I will try adding the info to the index and trying the icon. I hate to have to disturb my folder simplicity and would prefer a link. Do you know how to make link ../ with an upper directory location?

---

### Post by cubeist on 2009-06-25
disregard my previous post about needing a specific 48x48 pixel icon.  The 128x128 works aok... I found a great resource for the correct icon naming schema.

First, go to  the Tango project (lots of great info on this site)
[http://tango.freedesktop.org/Standard_Icon_Naming_Specification](http://tango.freedesktop.org/Standard_Icon_Naming_Specification)

Then download the icon-naming-utils.  Here is a direct link:
[http://tango.freedesktop.org/releases/icon-naming-utils-0.8.90.tar.gz](http://tango.freedesktop.org/releases/icon-naming-utils-0.8.90.tar.gz)

You don't have to install the program (you can if you want), but in this folder is a fantastic resource called ***legacy-icon-mapping.xml***.  This file contains the main name of an icon and all the legacy links required for it to display properly.

So for the multimedia-volume-control icon, here are all the required links
```
	<icon name="multimedia-volume-control">
	    <link>gnome-mixer</link>
	    <link>volume-knob</link>
	    <link>arts</link>
	    <link>kcmsound</link>
	    <link>multimedia</link>
	    <link>xfce4-mixer</link>
	</icon>
```

cheers,

---

### Post by jesterthejedi on 2009-06-25
AWESOME!!!
I will create the links. So that takes care of all except Rhythmbox's copy icon. I don't believe its a system wide icon, as I have not seen it in use anywhere else. Any ideas?

---

### Post by jesterthejedi on 2009-06-25
Okay done with that job! The old synaptic icon still bugs me. That's an app a lot of people use frequently. No icon theme AFAIK has been able to break that code. Pushing the limits of what can be covered is what can make my theme exceptional, and that's my goal. Here is a screen cap of the fixes as compared to Hydroxygen.

---

### Post by cubeist on 2009-06-25
Yes Synaptic icon really bugs me!  There must be code that does not allow the icon to be changed.

Also on my list of top pet peeves is not being able to find the rhythmbox 'drag' icon.  I have looked everywhere for this icon, but cannot find it.  It definitely is a standard gnome mimetype...It just isn't anywhere in /usr/share/...  In the banshee program, it uses the mimetype x-audio-generic.png, but like synaptic, there must be code that overwrites custom icons.

---

### Post by jesterthejedi on 2009-06-27
Is there a way to reverse engineer the app to find out? My other thought is to ask the direct programer if they would also know. A few more steps...

---

### Post by jesterthejedi on 2009-07-10
Is the drag/drop icon in Rhythmbox/Archive Manager somehow a cursor file? It seems to take over the mouse use. I am thinking its in default cursor folder.

---

### Post by cubeist on 2009-07-11
It's possible, but I have no idea how to open cursor images.

I looked in the code for both rhythmbox and banshee and couldn't find any specific references to that icon.  I can't figure out why they use different icons.

Did you figure out anything for the synaptic icon yet?

---

