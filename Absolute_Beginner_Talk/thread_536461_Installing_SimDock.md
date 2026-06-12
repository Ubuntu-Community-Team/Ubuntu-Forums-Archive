---
title: "Installing SimDock"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Magneticgravity on 2007-08-27
I download the .deb verison of SimDock.

It launches installer when i double click and i get this:

---

### Post by Magneticgravity on 2007-08-27
Anyone?

---

### Post by saipu on 2007-09-01
I also facing the same problem before.
So what i do was download the rpm package and the convert it to deb package using alien. Or  you may try to download another deb package from getdeb ([www.getdeb.net](www.getdeb.net))

---

### Post by Orbital75 on 2007-09-03
You don't have to compile Simdock....
I just use Apt-get and it even put an icon on my Applications menu.
The icon looks like a Horse Magnet.

---

### Post by ressac on 2007-09-08
i download from getdeb.net and its work

---

### Post by slimdog360 on 2007-09-08
the getdeb way or aptget way will probably work but for future reference I can give you a hint. The permission problem means that this particular deb file is protected and I would guess only root would be able to install it. There is a number of ways around this.

```
sudo dpkg -i name_of_file.deb
``` will install the deb file for you using root privileges.

```
sudo chmod -R 777 name_of_file.deb
``` will change the privileges to let anyone use it. Which will let you run it the way you tried originally.

You can apply these methods to anything in linux.

---

### Post by Nessa on 2007-10-01
The code doesn't work...

---

### Post by brunoscunha on 2007-11-03
Same problem here :(

---

### Post by oasick on 2007-11-04
Hi everybody !!! I compiled wxwidgets_2.8.5 and simdock-1.2 for Ubuntu Gutsy :)

You can download the files here:

[wxwidgets_2.8.5]("http://www.box.net/shared/91x5r27zyg")
[simdock-1.2]("http://www.box.net/shared/ht4abfyf46")

First you most install wxwidgets_2.8.5.deb

If you have any problem with background (sometimes appears a message at start session) you most do 2 things:

1. Scale the wallpaper image to your screen resolution. For example, if your screen resolution in 1024x768 your wallpaper image most have the same resolution.

2. To start simdock you most indicate where is your wallpaper image like this:

simdock /here/is/my/wallpaper/thisis.jpg

Don't forget that simdock is a very earlier application... but this version works very fine in my ubuntu gutsy :)

I hope that this halp you. Reggards and.. Good save Ubuntu :lolflag:

---

### Post by benjaminmorris on 2007-11-06
I tried to install the packages you posted for download (thanks, by the way) but I get an error that a dependency is not satisfiable: libpango1.0-0

Any ideas where to get it?

EDIT: Actually, upon further research I found I already had it installed, but still unable to install wxwidgets or simdock. Any ideas?
EDIT AGAIN: For anybody else having the same problem, here's how I fixed it:

1. Add one of the repositories here: [*http://packages.debian.org/sid/libpango1.0-0/i386/download*]("http://packages.debian.org/sid/libpango1.0-0/i386/download") to your */etc/apt/sources.list* by adding the appropriate line to end, i.e. 

```
deb http://http.us.debian.org/debian sid main
```

2. Run Synaptic Package Manager, ignoring errors about GPG and such. Search for libpango.

3. Mark libpango for update. Synaptic will automatically mark all necessary dependencies for update as well. Apply changes

4. Now you should be able to install wxwidgets, and then simdock. 

I got it installed, but decided it wasn't for me just yet. It still lacks a lot of customization options, and it just doesn't seem to behave quite right.

Oh, and one other thing: when you add that repository from debian.org, you'll probably get a notification that there are a bunch of updates available. Update at your own risk. I'm pretty new at linux and troubleshooting, so I may or may not be able to answer questions or help you solve problems, but I'll do my best.

---

### Post by TadH on 2007-11-11
i could not get this to work

---

### Post by Marari on 2007-11-15
Worked like a charm for me on 7.10

First installed the *libpango* package, then wxwidgets and finally simdock.

No issues. Works nicely on a non-composted desktop.

---

### Post by sophtpaw on 2007-11-21
> **Orbital75 said:**
> You don't have to compile Simdock....
I just use Apt-get and it even put an icon on my Applications menu.
The icon looks like a Horse Magnet.

how to use apt-get to install simdock? it is not in repositories, so??

Can someone tell me how to get SimDock?

thank you

---

### Post by sophtpaw on 2007-11-21
i can only find a deb for SimDock at getdeb.net for feisty
Anyone know of a deb for simdock for gutsy?

thank you

---

### Post by overdrank on 2007-11-21
> **sophtpaw said:**
> i can only find a deb for SimDock at getdeb.net for feisty
Anyone know of a deb for simdock for gutsy?

thank you

Hi you can download the deb here and should work with Gutsy
[http://sourceforge.net/project/showfiles.php?group_id=198436&package_id=235109](http://sourceforge.net/project/showfiles.php?group_id=198436&package_id=235109)

---

### Post by sophtpaw on 2007-11-21
> **overdrank said:**
> Hi you can download the deb here and should work with Gutsy
[http://sourceforge.net/project/showfiles.php?group_id=198436&package_id=235109](http://sourceforge.net/project/showfiles.php?group_id=198436&package_id=235109)

thanks, i got it now

---

### Post by Partyboi2 on 2007-11-21
When I tried to use the .deb file that I downloaded I was faced with the same problem that it could not open simdock deb
So the way I got it to work was using the .rpm file from here:
[http://sourceforge.net/project/downloading.php?group_id=198436&use_mirror=optusnet&filename=simdock-1.2-2.i386.rpm&84904024](http://sourceforge.net/project/downloading.php?group_id=198436&use_mirror=optusnet&filename=simdock-1.2-2.i386.rpm&84904024)

You will need to have libwxgtk2.8-0 installed for simdock to work.
```
 sudo apt-get install libwxgtk2.8-0
```Then installed alien.
```
sudo apt-get install alien
```then converted it to a .deb file
```
sudo alien -d simdock-1.2-2.i386.rpm
```then installed it
```
sudo dpkg -i /home/*username*/*location*/simdock_1.2-3_i386.deb
```Change *username* to your username.
Change *location* to where the file can be found
Might help someone else out:)

---

### Post by sophtpaw on 2007-11-21
SimDock eats up into the monitors real-estate quite a bit?? Its noticeably reducing firefox by a width of nearly two more panels on top of default panel.

Also, trying to add it as launcher firefox-bin doesn't launch it. Anyone know the correct command?

thank you

---

### Post by Manan on 2007-11-23
hello respected members this is my first post here and my first attempt to a native hdd installation of any linux distro ...

i tried to install this simdock using the links given but im getting a dependency error

Its says: dependency not satisfiable: libpango1.0-0 i tried to re-install the same through synaptics but its till did not work im getting the same error for wxwidgets and sim dock :( any help guys

thanx :p

Edit: i got it to install on my system but now when i click on he horse shoe icon nothing happens it does not start :?

---

### Post by Partyboi2 on 2007-11-23
Try starting it from a terminal and see if that works.
```
simdock
``` 
:)

---

### Post by az_s_za on 2007-11-25
Thanks partyboi for your instructions here.

I installed simdock from the rpm file as per your instructions, but when I run "simdock" it doesn't work.

In a terminal I get:-
> $ simdock
simdock: error while loading shared libraries: libwnck-1.so.18: cannot open shared object file: No such file or directory

I had a look in synaptic and there is no package called "libwnck-1.so.18" available.

Any ideas???  Thanks.

---

### Post by MozartlovesUbun2 on 2007-11-25
gonna try it too

---

### Post by az_s_za on 2007-11-25
Also, does simdock work OK once its going?

I see some other threads with problems of simdock keeping part of the screen to itself with some apps.  I don't want to spend heaps of time getting it going only to find I have problems with it.

Thanx.

---

### Post by Partyboi2 on 2007-11-25
az_s_za,

You will need to make sure that you have libwxgtk2.8-0 package installed.
```
sudo apt-get install libwxgtk2.8-0 
```

---

### Post by Partyboi2 on 2007-11-25
simdock seems to be a pretty basic program, it does not seem to have a auto hide feature so takes a chunk out of the size of the windows that you are viewing. Me personally I prefer Awn and kiba docks, cause they got more flexibility of what you can do with them.
But if you are wanting something simple simdock seems to be that!

---

### Post by az_s_za on 2007-11-26
Thanks.

I think I'll give it a miss.  I only have an 11.1" screen, so don't want to lose any of it to the dock.

I am currently using cairo-dock which is EXCELLENT, but I thought I'd see if I could get an alternative that doesnt require compiz.

I'll just stick to Cairo-dock.

---

