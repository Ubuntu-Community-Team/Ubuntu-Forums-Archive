---
title: "Music applet - configure warnings"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by y-lee on 2008-01-28
I am trying to compile [Music Applet]("http://www.kuliniewicz.org/music-applet/downloads/") in Dapper.  **./configure** gives the following warnings:

```
configure: WARNING: Song notification popups are disabled because the following Python modules could not be found:
configure: WARNING:     * pynotify
configure: WARNING: Saving passwords is disabled because the following Python modules could not be found:
configure: WARNING:     * gnomekeyring
configure: WARNING: Amarok support is disabled because the following Python modules could not be found:
configure: WARNING:     * kdecore
configure: WARNING:     * pcop
configure: WARNING:     * pydcop
configure: WARNING: MPD support is disabled because the following Python modules could not be found:
configure: WARNING:     * mpdclient2
configure: WARNING: XMMS2 support is disabled because the following Python modules could not be found:
configure: WARNING:     * xmmsclient
```

This is after I installed a bunch of stuff I thought I needed and I reduced the errors and warnings to just these. Since  I plan on using this applet with Amarok I need at least that much supported but preferably I wish no warnings.:)

It confuses me because i have for example:


```
python-kde3
python-kde3-dev 
python2.4-xmms
```

Any help or suggestions would be greatly appreciated.

---

### Post by y-lee on 2008-01-28
I found two post here, [Can't Compile music-applet]("http://ubuntuforums.org/showthread.php?t=423156") and [trouble compiling music-applet 2.1]("http://ubuntuforums.org/showthread.php?t=421174&highlight=music-applet"). Neither one of which helped. I do however note that I have python2.4  not 2.5. Could that be the problem? 

BTW this applet is not in Dappers repos :(

---

### Post by emarkd on 2008-01-28
Do you have easy_install?  If not, I think you can get it from the repositories by installing python-setuptools.  After you have easy_install setup, you can search cheeseshop.python.org for your missing packages and install them using easy_install

---

### Post by emarkd on 2008-01-28
Definitely upgrade to 2.5 first and see what you've got then.  Python is pretty backwards-compatible but some of the modules are not.

---

### Post by y-lee on 2008-01-28
Thanks for the easy install tip emarkd :)

Python 2.5 is not in Dappers repos.  I Installed Dapper because i liked the idea of LTS but being new to both linux and ubuntu i was unaware that meant the repos were not kept up to date:confused: Not hardly my idea of long term support.

But anyway I am downloading Python 2.5.1 now and am going to try to compile it today or tomorrow (work interferes with my computer life.) Do i need to uninstall my current python or can I just compile the source code essentially on top of it?

---

### Post by y-lee on 2008-01-28
Well I compiled python 2.5.1 without uninstalling the previous version as reading thru the included readmes let me to believe this would not be problematic.

```
$ python
Python 2.5.1 (r251:54863, Jan 28 2008, 13:50:48)
[GCC 4.0.3 (Ubuntu 4.0.3-1ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.


```

However Now I have more warnings :confused:

```
configure: WARNING: The following Python modules required to run Music Applet could not be found:
configure: WARNING:     * gconf
configure: WARNING:     * gnomeapplet
configure: WARNING:     * gobject
configure: WARNING:     * gtk
configure: WARNING:     * pango
configure: WARNING: Song notification popups are disabled because the following Python modules could not be found:
configure: WARNING:     * pynotify
configure: WARNING: Saving passwords is disabled because the following Python modules could not be found:
configure: WARNING:     * gnomekeyring
configure: WARNING: Amarok support is disabled because the following Python mod les could not be found:
configure: WARNING:     * kdecore
configure: WARNING:     * pcop
configure: WARNING:     * pydcop
configure: WARNING: Audacious support is disabled because the following Python modules could not be found:
configure: WARNING:     * dbus
configure: WARNING: Banshee support is disabled because the following Python modules could not be found:
configure: WARNING:     * dbus
configure: WARNING: Exaile support is disabled because the following Python modules could not be found:
configure: WARNING:     * dbus
configure: WARNING: MPD support is disabled because the following Python modules  could not be found:
configure: WARNING:     * mpdclient2
configure: WARNING: Muine support is disabled because the following Python modules could not be found:
configure: WARNING:     * dbus
configure: WARNING: Quod Libet support is disabled because the following Python modules could not be found:
configure: WARNING:     * dbus
configure: WARNING: Rhythmbox support is disabled because the following Python modules could not be found:
configure: WARNING:     * dbus
configure: WARNING: VLC support is disabled because the following Python modules  could not be found:
configure: WARNING:     * dbus
configure: WARNING: XMMS1 support is disabled because the following Python modules could not be found:
configure: WARNING:     * xmms
configure: WARNING: XMMS2 support is disabled because the following Python modules could not be found:
configure: WARNING:     * xmmsclient
```

---

### Post by emarkd on 2008-01-28
Well, you have to look what the LTS releases are for.  They're intended to be systems that are rock-solid and do not change often, like server or other critical applications.  Updates are not made to LTS releases unless there are security issues.  Since Python 2.5 is not a security update to 2.4, it's not updated in 6.06LTS.  Does that make sense?

If you're going to be running a lot of current software or experimenting around a bit with your Ubuntu, you may want to consider upgrading to 7.10 before you continue.  Most of those dependency errors you're getting are related to newer technologies present in 7.10 but (apparently) not in 6.06LTS

---

### Post by y-lee on 2008-01-28
I understand your point about LTS, I was just whining because when I installed Dapper I did not understand all that it implied, ie software not being current and an inability to compile current software. I had read lots (for about 2 months) about Ubuntu before installing and no one had made that clear or i missed it. That point should be made clear on Ubuntus web site.

Dapper has been remarkably stable and I've had no other real issues other than  an inability to install certain things. At this point I will never go back to Windows as Ubuntu has transformed my machine, it is faster, never crashes (almost), and gives me far less headaches. 

I am planing on reinstalling (and updating) but before I do I need to figure out what to do with about 20G of files I wish to keep. I have no backup or extra HD to store it on, nor can I afford it at the moment. 

So at this point it looks like installing Music applet on Dapper is probably not going to happen ?

Should I leave python2.5 installed? Will it hurt anything like kill apps using python?

---

### Post by emarkd on 2008-01-28
I actually agree with you on your first point.  I've had to explain that to several people as I've personally convinced them to try Ubuntu.  The differences are not made as clear as it should be.  In fact, Ubuntu's page only points out the positives of using 6.06LTS over 7.10 and doesn't even mention that there is a down side.

You can try and use easy_install to meet all of those dependencies that popped up.  I'm not saying it can't be done; it'll just take a lot of searching on the cheeseshop to find the proper packages to install.

You shouldn't have any problems with having 2.5 over 2.4.

---

### Post by y-lee on 2008-01-28
> **emarkd said:**
> You can try and use easy_install to meet all of those dependencies that popped up.  I'm not saying it can't be done; it'll just take a lot of searching on the cheeseshop to find the proper packages to install..

Maybe in time. What gets me is uncertainty about the dbus issue and 

```
configure: WARNING: The following Python modules required to run Music Applet could not be found:
configure: WARNING:     * gconf
configure: WARNING:     * gnomeapplet
configure: WARNING:     * gobject
configure: WARNING:     * gtk
configure: WARNING:     * pango

```

I found dbus online but am uncertain whether i should upgrade it as I have alot of dbus stuff installed. The rest I also have installed but most likely older copies. I'm not sure if trying to update this stuff would kill Dapper :confused:

The python stuff seems like less of a problem.

Meanwhile I installed Rhythmbox Applet 0.1.7, it will have to do for now even tho Rhythmbox doesn't really meet my needs as well as Amarok. That is the  reason I installed Amarok to begin with.

Easy_install is cool tho i definitely thank you for that :)

---

### Post by y-lee on 2008-01-28
I wrote Paul Kuliniewicz the programmer who created this applet and he actually responded. Sort of surprised me but here's what he had to say  about my issues here: 

> The configure script can't find the Python modules the applet needs,
which means either they're not installed or they're installed somewhere
where Python isn't looking for them.  Ubuntu should have everything you
need; it's just a matter of making sure the right packages are
installed.

On Debian at least, the minimal set of Python packages is something
like:

 [LIST]
[*] python-glade2
[*]  python-gnome2
[*]  python-gnome2-desktop
[*]  python-gobject
[*]  python-gtk2
[/LIST]

All of those come out of PyGTK, I believe, but Debian (and Ubuntu,
presumably) splits it up into multiple packages.

To enable support for particular players, you'll need to figure out
which packages provide the necessary Python modules.  For Amarok in
particular, you'll need:

[LIST]
[*]python-dcop
[*] python-kde3
[/LIST]

Since each distro will have their own packages for the various
dependencies Music Applet has, there's no good way for the configure
script to point out precisely which packages you need to install.  All
it can really do is warn you if it can't find the Python modules it
needs.

If you still have problems getting things working, let me know.

I checked and found i needed:

[LIST]
[*]python-dcop 
[*]python-gobject
[/LIST]

However I am still getting exactly the same errors as above:

```
configure: WARNING: The following Python modules required to run Music Applet could not be found:
configure: WARNING:     * gconf
configure: WARNING:     * gnomeapplet
configure: WARNING:     * gobject
configure: WARNING:     * gtk
configure: WARNING:     * pango
configure: WARNING: Song notification popups are disabled because the following Python modules could not be found:
configure: WARNING:     * pynotify
configure: WARNING: Saving passwords is disabled because the following Python modules could not be found:
configure: WARNING:     * gnomekeyring
configure: WARNING: Amarok support is disabled because the following Python modules could not be found:
configure: WARNING:     * kdecore
configure: WARNING:     * pcop
configure: WARNING:     * pydcop
configure: WARNING: Audacious support is disabled because the following Python modules could not be found:
configure: WARNING:     * dbus
configure: WARNING: Banshee support is disabled because the following Python modules could not be found:
configure: WARNING:     * dbus
configure: WARNING: Exaile support is disabled because the following Python modules could not be found:
configure: WARNING:     * dbus
configure: WARNING: MPD support is disabled because the following Python modules could not be found:
configure: WARNING:     * mpdclient2
configure: WARNING: Muine support is disabled because the following Python modules could not be found:
configure: WARNING:     * dbus
configure: WARNING: Quod Libet support is disabled because the following Python modules could not be found:
configure: WARNING:     * dbus
configure: WARNING: Rhythmbox support is disabled because the following Python modules could not be found:
configure: WARNING:     * dbus
configure: WARNING: VLC support is disabled because the following Python modules could not be found:
configure: WARNING:     * dbus
configure: WARNING: XMMS1 support is disabled because the following Python modules could not be found:
configure: WARNING:     * xmms
configure: WARNING: XMMS2 support is disabled because the following Python modules could not be found:
configure: WARNING:     * xmmsclient

```

At this point I feel maybe I should uninstall Python 2.5.1 and reinstall Python 2.4 at least then i didn't have the dbus thing and gconf et al. and trying again. However It's going to have to be tomorrow as its late here now.

---

### Post by y-lee on 2008-01-29
By reverting back to Python 2.4.3 and installing a few more things, most notably:

```
python-mpdclient 
gob2
glade-gnome [COLOR="Blue"](this one came with others)[/COLOR]

```


I have reduced the warnings to:

```


configure: WARNING: Song notification popups are disabled because the following Python modules could not be found:
configure: WARNING:     * pynotify
configure: WARNING: Saving passwords is disabled because the following Python modules could not be found:
configure: WARNING:     * gnomekeyring
configure: WARNING: XMMS2 support is disabled because the following Python modules could not be found:
configure: WARNING:     * xmmsclient



```


But I'm unable to find these modules, still working on it. The applet might compile now but I kinda want the Song notification popup, and hence the pynotify module :(

---

### Post by pmasiar on 2008-01-30
> **y-lee said:**
> I understand your point about LTS, I was just whining because when I installed Dapper I did not understand all that it implied, ie software not being current and an inability to compile current software. I had read lots (for about 2 months) about Ubuntu before installing and no one had made that clear or i missed it. That point should be made clear on Ubuntus web site.

I am planing on reinstalling (and updating) but before I do I need to figure out what to do with about 20G of files I wish to keep. I have no backup or extra HD to store it on, nor can I afford it at the moment. 

So at this point it looks like installing Music applet on Dapper is probably not going to happen ?

Should I leave python2.5 installed? Will it hurt anything like kill apps using python?

Now you know that LTS is accomplished by debugging and maintaining old "stable" versions of code, which means not adding new bugs, and not adding new features.

Installing Python2.5 might kill your whole system, if those two python versions will get mixed up. It is possible but not trivial.

I am not sure if you can upgrade Dapper without reinstalling, you may want to check that. Some later version is possible to upgrade, up one version at a time.

Now you know that you should have separate partition for data, so even in case you reinstall partition with OS, you keep your data. Maybe next time you will do it. maybe you should write up comment to the part where you read about formatting your hardisk, about having more partitions, not just a one.

You may look to save your 20GB music files on CDs, if you cannot afford second disk. But maybe some of your friends has external harddrive connected via USB, so you can make backup that way.

Another variant would be to get a friend with big enough free space on his drive, connect both computers in LAN, and transfer your data to his disk before reinstall, then transfer them back.

If not, get a USB memory stick and transfer data to other computer by that.

Another (very slow) variant is to upload your data to gmail, there is gmail plugin for firefox which uses gmail as data repository.

You should ask Music applet author 9or check website) for which ubuntu version it is intended - different versions have different requirements and different libraries available, as you just fund.

Yet another option would be to forget about music for a while :-) , and learn more about different ways of connecting your linux box to others, and data transfer. Fortunately to you, there are many flexible ways to do it.

---

### Post by The Wizzard on 2008-02-03
Hi

I had some similar problems, but at the end I kinda managed to install it ... tho, every time I try to load it it crashes. 
When trying to run it via terminal, I get the following error
```
/usr/local/lib/python2.5/site-packages/musicapplet/applet.py:973: GtkWarning: Unable to locate theme engine in module_path: "pixmap",
  theme = gtk.icon_theme_get_default ()
```

Any idea what's the problem?

---

### Post by y-lee on 2008-02-03
**The Wizzard**

You are might be getting this problem because you installed a theme without having the right packages that is uses. Myabe what you are missing is  gtk2-engines-pixbuf.

Type the below in a terminal and let me know


```
 sudo apt-get install gtk2-engines-pixbuf 
```

---

### Post by The Wizzard on 2008-02-04
Ok, now debugging gives out the following:

```
wizzy@Minty:~$ /usr/local/libexec/music-applet 
DEBUG: GConf root is /apps/panel/applets/applet_9/prefs
Failed to open module at /usr/local/lib/python2.5/site-packages/musicapplet/plugins/__init__.py: 'module' object has no attribute 'INFO'
Failed to open module at /usr/local/lib/python2.5/site-packages/musicapplet/plugins/__init__.pyo: 'module' object has no attribute 'INFO'
Failed to open module at /usr/local/lib/python2.5/site-packages/musicapplet/plugins/__init__.pyc: 'module' object has no attribute 'INFO'
Failed to scan /home/wizzy/.gnome2/music-applet/plugins: [Errno 2] No such file or directory: '/home/wizzy/.gnome2/music-applet/plugins'
QApplication: There should be max one application object

** (music-applet:6081): WARNING **: Unable to load icon 'rhythmbox': Icon 'rhythmbox' not present in theme
```

I guess it's probably cuz the applet loads all the plugins by default. And I'm cluless how to disable them v_v

---

### Post by Arcnsparc on 2008-04-11
I had a similar post here:
[http://ubuntuforums.org/showthread.php?p=4699069#post4699069](http://ubuntuforums.org/showthread.php?p=4699069#post4699069)
and my main problem is the 

configure: WARNING: Amarok support is disabled because the following Python modules could not be found:
configure: WARNING:     * kdecore
configure: WARNING:     * pcop
configure: WARNING:     * pydcop

part of the install.  I think there is a way to set the path so the install will know where these things are.  I get more errors for the other players but i really dont mind because i wont be using them.  If you figured out how to fix this I'd love to know it has been driving me nuts!  thanks!

---

### Post by Jorenko on 2008-06-07
> **Arcnsparc said:**
> I had a similar post here:
[http://ubuntuforums.org/showthread.php?p=4699069#post4699069](http://ubuntuforums.org/showthread.php?p=4699069#post4699069)
and my main problem is the 

configure: WARNING: Amarok support is disabled because the following Python modules could not be found:
configure: WARNING:     * kdecore
configure: WARNING:     * pcop
configure: WARNING:     * pydcop

part of the install.  I think there is a way to set the path so the install will know where these things are.  I get more errors for the other players but i really dont mind because i wont be using them.  If you figured out how to fix this I'd love to know it has been driving me nuts!  thanks!

I just came to this thread searching for an answer to your exact question. Based on the first post on this page, combined with some additional research, my solution was this:
```
sudo aptitude install python-kde3 python-dcop
```
Once I installed those, I was good to go with Amarok.

Edit: I'm on 64-bit hardy, fyi.

---

