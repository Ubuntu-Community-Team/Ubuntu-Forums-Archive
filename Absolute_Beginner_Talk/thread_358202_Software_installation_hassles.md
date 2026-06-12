---
title: "Software installation hassles"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by samienela on 2007-02-10
I am looking for some temperature monitor software for my computer (Opteron 165 cpu, Gigabyte K8N51GMF-9-RH mobo, Ubuntu Dapper)  and found "Computertemp"

Tried to install it, found that it requires pygtk.

Searched at ubuntuforums and several other places...
Found a tarball of pygtk, downloaded it to ./tmp, untarred it, cd'd into the folder and typed ./configure

Got error message, "no acceptable C compiler"

Searched at ubuntuforums and the psychocats site...
Did sudo install build-essentials and tried ./configure again

Got error message, cannot find headers required to compile python extensions

Searched at ubuntuforums and the psychocats site...
Did sudo install python-dev  and tried ./configure again

Got error message, no package "pygobject-2.0" found

This is like a bad dream, everything I try gets me stuck even further.  Advice please!

1)  What should I do to complete this installation?  OR...
2)  Is there some other temperature monitor package available that is more compatible with my absolute-beginner level skill in LInux? 

Thanks!

---

### Post by oilchangeguy on 2007-02-10
yes trying to get software to install in any version of linux is nowhere as easy as it is in windows. that being said linux is still a very good os. sorry i don't have a direct answer to your question. but is there a reason you need a temp. monitor? depending on the age of your computer you may be able to set an alarm in the bios when the cpu temp. gets to a preset level. and as log as you keep the inside of your computer dust free, and have enough cooling fans overheating should not be a problem.

---

### Post by aysiu on 2007-02-10
Instead of compiling from source, have you tried this? ```
wget -c http://download2.berlios.de/computertemp/computertemp_0.9.6-0ubuntu1_all.deb
sudo dpkg -i computertemp_0.9.6-0ubuntu1_all.deb
```

---

### Post by DSn0wMan on 2007-02-10
I noticed that there are some python-gkt packages available in the repositories. I am not sure if this is the one you need, but there is python-gtk-1.2, and python-gtk2.

You might also look into installing gdesklets. There are several hardware monitoring utilities available through gdesklets wich is also in the repositories.

---

### Post by risbac on 2007-02-10
Usually you NEVER install softwares from source, unless you have no other choice. Did you search into Synaptic first? That's really where you should start from. Or even from the "new applications installer" in the first menu (sorry I don't know the title in english for this option).

Then if no other choice and you want to compile, usually the website where you download the source from is listing what other packages you need. You can then just install all of them before compiling.

I'm not quite comfortable with compiling stuffs, but I'm already 2 years old with Ubuntu. I tried also at the beginning, but that's a Windows habit more than anything else I guess... 

About your particular problem, I don't think it's the easiest one to solve... As you know, there are not opensource drivers for everything, and from my experience, that's the case of temperature sensors sadly. Usually, if the driver exists, it's in the kernel, so nothing to do except running the software. So maybe look for the software first, there should be some applets for the taskbar. Then if it's not working, means the driver for the sensors is not in the kernel, and that's the beginning of some searches in the forums :)

---

### Post by aysiu on 2007-02-10
Just download the Dapper .deb and double-click it to install it.

It even works in Edgy (see attached screenshot)

---

### Post by samienela on 2007-02-10
Thanks aysiu for the hints - I downloaded the .deb, which looks like an open box on my desktop, and installed it.  I saw all the windows you got in your screenshot, plus a folder computertemp-0.9.6 on my desktop which may be left over from the earlier attempt to compile it from source. The only difference is that my installer window says "installing package file" and yours said "installation finished" above the solid orange progress bar  - the text below the bar says 
"Package 'computertemp_0.9.6-0ubuntu1_all.deb' was installed"  so I reckon it did install.

Unfortunately now I have no idea how to run this thing, or even where to find it.  I don't see it in the Applications menu, or on the list shown by clicking "Add/Remove Applications" even with unsupported and commercial applications checked.

Is it supposed to show up as an icon in the group at the right side of the top bar of the gnome desktop, near the time and the on/off button?  I don't see it there.

The bug-report section of the computertemp/berlios.de website says
> (3) Open a terminal and execute /usr/lib/gnome-panel/computertemp (in most distros computertemp will be there)

I typed "locate gnome-panel" in a terminal and found that it is at
/usr/share/omf/gnome-panel

but the only groups of files there are workplace-switcher, fish-applet, and window-list. (I don't even know what fish-applet is).

When I type "locate computertemp" in the terminal the only place it comes up is on the desktop - which is obviously the wrong place for an installed application.  Is it really installed?

Please advise - Many thanks!

---

### Post by aysiu on 2007-02-10
That's odd. When I do *locate lib/gnome-panel*, I get this: ```
locate lib/gnome-panel
/usr/lib/gnome-panel
/usr/lib/gnome-panel/libclock-applet.a
/usr/lib/gnome-panel/libclock-applet.la
/usr/lib/gnome-panel/libclock-applet.so
/usr/lib/gnome-panel/libfish-applet-2.a
/usr/lib/gnome-panel/libfish-applet-2.la
/usr/lib/gnome-panel/libfish-applet-2.so
/usr/lib/gnome-panel/libnotification-area-applet.a
/usr/lib/gnome-panel/libnotification-area-applet.la
/usr/lib/gnome-panel/libnotification-area-applet.so
/usr/lib/gnome-panel/libwnck-applet.a
/usr/lib/gnome-panel/libwnck-applet.la
/usr/lib/gnome-panel/libwnck-applet.so
``` Try this: ```
cd /usr/lib/gnome-panel
./computertemp
```

---

### Post by samienela on 2007-02-11
Thanks aysiu, but that doesn't work:

> sami@sami-opty165:~$ locate lib/gnome-panel
/usr/lib/gnome-panel
/usr/lib/gnome-panel/clock-applet
sami@sami-opty165:~$ cd /usr/lib/gnome-panel
sami@sami-opty165:/usr/lib/gnome-panel$ ls -la
total 124
drwxr-xr-x   2 root root  4096 2006-08-05 19:25 .
drwxr-xr-x 119 root root 28672 2007-02-10 15:34 ..
-rwxr-xr-x   1 root root 87696 2006-07-31 17:04 clock-applet
sami@sami-opty165:/usr/lib/gnome-panel$ locate computertemp
/home/sami/Desktop/computertemp-0.9.6.tar.gz
sami@sami-opty165:/usr/lib/gnome-panel$


lib/gnome-panel is in the right place, but doesn't have the computertemp applet in it.
The only place computertemp shows up is as the deb file on the desktop.  (I trashed the tar.gz file downloaded earlier, and its unpacked version)

When I cliek on the .deb file on my desktop, the window that comes up says that it's already installed and asks if I would like to reinstall it.

What do you recommend now?

---

### Post by aysiu on 2007-02-11
Can we try adding it graphically?

What happens if you right-click the panel, select **Add to Panel**, and then select the Computer Temperature Monitor? Is it listed as one of the available applets...?

---

### Post by samienela on 2007-02-11
Good idea - It came up in the list, but when I tried to add it it showed up "x-ed out" with the message "no temperature monitor support".

This surprised me - because the mobo should support acpi sensors - but at least the installation of the monitor applet seems to have gone OK.

I was able to add the cpu frequency monitor, though it is not reading correctly for the chip, 1 GHz instead of the expected 1.8 GHz... also my Folding@Home frametimes are longer than expected - this makes me think there may be something set wrong in the BIOS.  While I'd definitely appreciate advice on that, it goes beyond the topic of this thread and forum.

Many thanks for your help!

---

### Post by samienela on 2007-02-13
Couple days later... more questions.

A friend of mine has been trying to help me through this. On his advice I typed
```
 sudo acpi -V 
```
which returned the message "no support for device type: thermal"

After installing acpid and lm-sensors upon his advice (everything seems to have gone well in the installation), I get the same message.  Also, the command 
```
 sudo sensors-detect
``` returns the message

No i2c device files found.  Use prog/mkdev/mkdev.sh to create them.

I could use some kindly expert advice on what to do next - and also a pointer to some good resources on the problem of sensor detection in general. 

FWIW, the machine has an Opteron 165 CPU, Gigabyte GA-K8N51GMF-9-RH mobo, 1 Gb DDR400 RAM, and is running Ubuntu 6.06 "Dapper".  

Thanks in advance!

---

### Post by jlachovsky on 2007-03-14
I am also having the same issue with the computertemp program.

---

