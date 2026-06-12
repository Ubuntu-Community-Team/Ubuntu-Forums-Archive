---
title: "[SOLVED] change taskbar at bottom of screen"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by ahervey85 on 2008-01-20
i am currently setting up the theme and such for my desktop i have the background i want and even a theme i found on gnome-look.org i think a mac4lin graphite emerald one. my question is how do i get the icons like in the screenshot at the bottom of my screen? i really would like to change from the task bar thing that goes all the way across since it clashes with the theme and background. does any of this make sense? thanks for any help.

---

### Post by banewman on 2008-01-20
That will probably be a dock - avant window navigator or similar
The theme at gnome-look will have comments at the bottom and one might ask the question about the dock
If you right click the bottom panel you'll get options to change its' properties or remove it.
:)

---

### Post by ahervey85 on 2008-01-20
ok thanks that was quick! i will go back and see what i can find about the dock. thanks!

---

### Post by ahervey85 on 2008-01-20
ok, i looked it up and even checked out the how to install awn but im getting a little confused as to if i am doing it right? could someone help a little?

---

### Post by banewman on 2008-01-20
Here's a handy little howto for that - 
[http://www.ubuntugeek.com/howto-install-avant-window-navigator-awn-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/howto-install-avant-window-navigator-awn-in-ubuntu-710-gutsy-gibbon.html)
:)

---

### Post by Smelly Avocado on 2008-01-20
here is a guide to installing it
[http://ubuntuforums.org/showthread.php?t=385981]("http://ubuntuforums.org/showthread.php?t=385981")
its just about the easiest way to.

---

### Post by Paul820 on 2008-01-20
The easiest way is to just grab the .deb file from getdeb.net and run that [http://www.getdeb.net/search.php?keywords=awn]("http://www.getdeb.net/search.php?keywords=awn")

---

### Post by ahervey85 on 2008-01-20
i have tried all of that and afterwards this is what i get 

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                              Depends: libawn-bzr (= 0.2.0-bzr155-1) but it is not going to be installed
  awn-core-applets-bzr: Depends: libawn-bzr but it is not going to be installed
                        Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                        Depends: libawn-bzr but it is not going to be installed
                        Depends: python-libawn-bzr but it is not going to be installed
E: Broken packages
angel@angel-laptop:~$


when i try the libawn0 i get this error - dependancy is not satisfiable libpango 1.0-0

---

### Post by banewman on 2008-01-20
Open the synaptic package manager and click on settings in the top menu - then repositories - and check that all boxes are selected in the first tab except for sources
:)

---

### Post by ahervey85 on 2008-01-20
ok i did that and it installed some things but i am still getting the same error message

---

### Post by banewman on 2008-01-20
Did you read the ubuntugeeks link - it says you need desktop effects enabled for avant window manager to work - sounds like you don't have that running...
:)

---

### Post by st33med on 2008-01-20
Yes, generally, you need a composite manager, like E12 (Enlightenment), to run awn-bzr.

---

### Post by ahervey85 on 2008-01-20
ok and how exactly do i do this? i mean is it in the synaptics or do i have to d/l something?

---

### Post by CupofDice on 2008-01-20
Check System/Preferences/Appearance/Visual Effects and choose Normal or Extra to see if that works. (If you are using gutsy. I don't know how it works on Feisty).

---

### Post by ahervey85 on 2008-01-20
yeah i had that and still nothing i was asking more or less about the composite manager, desktop effects and such and the E12 enlightenment thing.

---

### Post by CupofDice on 2008-01-20
Yeah, enabling Normal or Extra is enabling Compiz Fusion which is a composite manager (and what allows me to run awn). I think you can ignore the advice about E12 since that doesn't need a graphics card, and when I ran E12 (which  is a desktop environment like gnome, but more 'lighter' and with nice graphics) on old hardware I couldn't run awn (though I may be wrong). Anyway you have a graphics card right?

Edit- You can also run E12 with gnome, but I am assuming you are just worried about getting awn to work. If so, and you have the options in Appearance checked, then it is just a installation problem.

Edit- [This]("http://ubuntuforums.org/showthread.php?t=572019&highlight=Avant+Window+Navigator") is how I installed awn.

---

### Post by ahervey85 on 2008-01-21
ok i have tried what you suggested and for the first part this is the response i got - 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
autotools-dev is already the newest version.
autotools-dev set to manual installed.
libgnome2-common is already the newest version.
libgnomevfs2-0 is already the newest version.
libgnome-desktop-2 is already the newest version.
libgnome2-0 is already the newest version.
libwnck-common is already the newest version.
python-gtk2 is already the newest version.
python-gconf is already the newest version.
bzr is already the newest version.
gnome-common is already the newest version.
python-gconf is already the newest version.
bzr is already the newest version.
E: Couldn't find package co
angel@angel-laptop:~$ cd awn-curves
bash: cd: awn-curves: No such file or directory

maybe i am doing something wrong?

this is the other message that i keep getting - 

The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                              Depends: libawn-bzr (= 0.2.0-bzr155-1) but it is not going to be installed
  awn-core-applets-bzr: Depends: libawn-bzr but it is not going to be installed
                        Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                        Depends: libawn-bzr but it is not going to be installed
                        Depends: python-libawn-bzr but it is not going to be installed
E: Broken packages

also, when i go to appearance visual effects the option for custom is now available

---

### Post by CupofDice on 2008-01-21
Well, you have dependency problems and those are always hell.  I think " sudo apt-get install -f " will help. It definitely won't hurt.

Edit - The way nikoPSK has his tutorial set out is definitely confusing if you are copying/pasting. If sudo apt-get install -f doesn't work, try this. Maje sure you have build essentials installed.

First, copy and paste this as a whole and enter.

```
sudo rm -f /usr/local/bin/awn*
sudo rm -f /usr/local/bin/avant*
sudo rm -rf /usr/local/lib/awn
sudo rm -f /usr/local/share/locale/*/LC_MESSAGES/avant-window-navigator.mo
sudo rm -f /usr/local/share/applications/avant*
sudo rm -f /usr/local/share/applications/awn*
sudo rm -rf /usr/local/share/avant-window-navigator
sudo rm -f /usr/local/lib/libawn*
sudo rm -rf /usr/local/include/libawn
sudo rm -f /usr/local/lib/libawn*
sudo rm -f /usr/local/lib/pkgconfig/awn.pc
sudo rm -rf /usr/local/share/awn-core-applets
sudo rm -rf /usr/local/lib/python2.5/site-packages/awn/
```

Then copy/paste this, hit enter

```
sudo apt-get install bzr m4 gnome-common
```

Then copy/paste this, hit enter

```
sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev 
```

Then copy/paste this, hit enter

```
bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves
```

Then copy/paste this, hit enter

```
cd awn-curves
```

copy/paste, hit enter

```
./autogen.sh && make
```

Then copy/paste this, hit enter

```
sudo make install
```

Then copy/paste this, hit enter

```
gksudo gedit /etc/apt/sources.list
```

Add this

```
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
```

Save and close. Then back to the terminal and copy/paste, hit enter

```
wget http://download.tuxfamily.org/syzygy42/reacocard.asc
```

Then copy/paste this, hit enter

```
sudo apt-key add reacocard.asc
```

Then copy/paste this, hit enter

```
rm reacocard.asc
```

Then copy/paste this, hit enter

```
sudo apt-get update
```

Finally you can install

```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
```

---

### Post by ahervey85 on 2008-01-21
thanks sooo much for all that it start doing something different but again when i got to the last step this is what i got - 

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                              Depends: libawn-bzr (= 0.2.0-bzr155-1) but it is not going to be installed
  awn-core-applets-bzr: Depends: libawn-bzr but it is not going to be installed
                        Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                        Depends: libawn-bzr but it is not going to be installed
                        Depends: python-libawn-bzr but it is not going to be installed
E: Broken packages
angel@angel-laptop:~/awn-curves$ 

am i still maybe missing something somewhere?

---

### Post by ice60 on 2008-01-21
i found this with instuctions that might help, in post #5
[http://ubuntuforums.org/showthread.php?p=4174567](http://ubuntuforums.org/showthread.php?p=4174567)

---

### Post by ahervey85 on 2008-01-21
ok it worked for a minute when i did the avant windows navigator and it brought it up but as soon as i closed the terminal it closed too?

---

### Post by ice60 on 2008-01-21
do this -
alt-F2
and put 
avant-window-navigator
in there and hit enter

when you close your terminal it's killing it, you could try closing the terminal with ctrl-d to keep it running, but that doesn't always work!

---

### Post by ice60 on 2008-01-21
you need to put **avant-window-navigator** in your startups to get it running at boot. i don't use ubuntu so i'm not sure how to do that, you can try and see if this works -

alt-F2
gnome-session-properties

and putting it in the startup programs, if it's there that should work, if you have the eye-candy effects running for it to work too.

---

### Post by ahervey85 on 2008-01-21
ok that works thanks! now i gotta figure out how to get the applications places and system down there so i can get rid of the bars thanks again!

---

### Post by Paul820 on 2008-01-21
You can start it from Applications->Accessories-> Avant Window Navigator and to have it start when ubuntu starts just put it in your sessions: System->Preferences->Sessions and click add, then put **avant-window-navigator** for the command and **awn** for the name.

---

### Post by ahervey85 on 2008-01-21
never mind already answered

---

### Post by oodledoodle on 2008-01-21
command part is "avant-window-navigator" without the quotes.

---

### Post by ice60 on 2008-01-21
maybe you can drag them there?? 

if you have a program in the dock and it's already running, but you need a new version running, you can click with the middle button, i suppose that's obvious, but it took me an hour or so to work it out lol.

a good program to get is a clipboard manager that runs in the panel tray, so you don't have to keep looking up things you had in the clipboard, like that avant-window-navigator. there's one called glipper and one called desktop-data-manager if you need one??

---

### Post by ahervey85 on 2008-01-21
ok is there somewhere a guide to add buttons to it like apps places and sytem and messenger and the like?

---

### Post by ice60 on 2008-01-21
i think you need to look for awn-extras-applets, it adds things. i've never used it though. maybe someone will know what to install??
[http://wiki.awn-project.org/index.php?title=Awn_Extras](http://wiki.awn-project.org/index.php?title=Awn_Extras)

---

### Post by ice60 on 2008-01-21
this might be it -
[https://launchpad.net/awn-extras/0.2/0.2.1/+download/awn-extras-applets-0.2.1.tar](https://launchpad.net/awn-extras/0.2/0.2.1/+download/awn-extras-applets-0.2.1.tar)
so you should be able to follow the install instructions you did last time -

wget [https://launchpad.net/awn-extras/0.2/0.2.1/+download/awn-extras-applets-0.2.1.tar](https://launchpad.net/awn-extras/0.2/0.2.1/+download/awn-extras-applets-0.2.1.tar)
tar -xvf awn-extras-applets-0.2.1.tar
cd /awn-extras-applets-0.2.1
./configure
make
sudo make install

then right-click on the corner of the dock and select **preferences** and go to **applets**

that's what i'd install, but i really don't know, so you should probably wait and see if someone knows that's right??

and you can drag programs on and off it straight from their menus, or the desktop.

---

### Post by ahervey85 on 2008-01-21
thanks for all your help! now that i know how to do this i am going to go put it on my laptop right now im playing around with it on my husbands laptop. how do i go about uninstalling it off of his?

---

### Post by ice60 on 2008-01-21
> **ahervey85 said:**
> thanks for all your help! now that i know how to do this i am going to go put it on my laptop right now im playing around with it on my husbands laptop. how do i go about uninstalling it off of his?

are you serious? after all that lol. i think it's this -
sudo apt-get remove avant-window-navigator awn-extras-applets

EDIT, i mean you're trying it out on his computer first loool

---

### Post by ahervey85 on 2008-01-21
yeah unfortunately. my laptop is new and i dont want to mess it up and hes at school right now so i thought i would give it a shot on his to see if it works.

---

### Post by ahervey85 on 2008-01-21
it didnt work i tried it w/o the awn extras applets and it said package avant window navigator is not installed so not removed

---

### Post by ahervey85 on 2008-01-21
can anyone help?

---

### Post by ice60 on 2008-01-22
sorry, i wasn't thinking, from the decompressed directory that you used to install avant-window-navigator run this (this is the directory i mean 
/avant-window-navigator-0.2.1) -

sudo make uninstall
sudo rm -f /usr/local/bin/awn-manager
sudo rm -f /usr/local/bin/avant-*

you got it from this post - [http://ubuntuforums.org/showpost.php?p=4179777&postcount=5](http://ubuntuforums.org/showpost.php?p=4179777&postcount=5)

if you deleted that directory download it again, i *think* you'll need to follow the install instructions again, then when it's installed do those commands -

sudo make uninstall
sudo rm -f /usr/local/bin/awn-manager
sudo rm -f /usr/local/bin/avant-*

in future, when you install from source, instead of running -
sudo make install
you can run 
sudo checkinstall install
checkinstall will ask a few questions, which you can click enter to for almost all of them to select the defaults, apart from when it asks for a name, you can use the name of the program, then hit enter twice, it will be obvious when you see it.

with checkinstall you will be able to uninstall everything you installed by using synaptic, or by running the commands that didn't work before -
sudo apt-get remove avant-window-navigator awn-extras-applets

[color=red]i searched the forums and saw some poeple had problems with apt-get autoremove, so make sure it's really safe to use before you run it[/color]
when you have been installing and uninstalling programs you can clean up a bit by running -
apt-get autoremove
or, there's also a GUI program i've used in the past called gtkorphan, it always worked OK for me and removed unused dependencies

---

